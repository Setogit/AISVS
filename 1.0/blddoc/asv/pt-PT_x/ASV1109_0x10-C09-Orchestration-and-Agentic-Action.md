# 9 Orquestração Autônoma e Segurança da Ação Agente

## Objetivo de Controle

Garantir que sistemas de IA autônomos ou multiagentes possam executar apenas ações que sejam explicitamente intencionadas, autenticadas, auditáveis e dentro de limites definidos de custo e risco. Isso protege contra ameaças como Comprometimento de Sistema Autônomo, Uso Indevido de Ferramentas, Detecção de Loop de Agentes, Sequestro de Comunicação, Falsificação de Identidade, Manipulação de Enxame e Manipulação de Intenção.

---

## 9.1 Orçamentos para Planejamento de Tarefas do Agente e Recursão

Controle planos recursivos e force pontos de verificação humanos para ações privilegiadas.

|   #   | Descrição                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.1.1 | Verifique se a profundidade máxima de recursão, amplitude, tempo de relógio de parede, tokens e custo monetário por execução de agente estão configurados centralmente e controlados por versão.   |   1   |  D/V  |
| 9.1.2 | Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) exigem aprovação humana explícita por meio de um canal auditável antes da execução. |   1   |  D/V  |
| 9.1.3 | Verifique se os monitores de recursos em tempo real acionam a interrupção do disjuntor quando qualquer limite de orçamento é excedido, interrompendo a expansão adicional das tarefas.             |   2   |   D   |
| 9.1.4 | Verifique se os eventos do disjuntor estão registrados com o ID do agente, condição que acionou e o estado do plano capturado para revisão forense.                                                |   2   |  D/V  |
| 9.1.5 | Verifique se os testes de segurança cobrem os cenários de exaustão do orçamento e plano descontrolado, confirmando a parada segura sem perda de dados.                                             |   3   |   V   |
| 9.1.6 | Verifique se as políticas orçamentárias estão expressas como política-como-código e aplicadas no CI/CD para bloquear a deriva de configuração.                                                     |   3   |   D   |

---

## 9.2 Isolamento de Plugin de Ferramenta

Isolar as interações da ferramenta para evitar acesso não autorizado ao sistema ou execução de código.

|   #   | Descrição                                                                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Verifique se cada ferramenta/plugin é executado dentro de um SO, contêiner ou sandbox em nível WASM com políticas de sistema de arquivos, rede e chamadas do sistema com privilégios mínimos. |   1   |  D/V  |
| 9.2.2 | Verifique se as cotas de recursos do sandbox (CPU, memória, disco, saída de rede) e os tempos limite de execução são aplicados e registrados.                                                 |   1   |  D/V  |
| 9.2.3 | Verifique se os binários ou descritores da ferramenta estão assinados digitalmente; as assinaturas são validadas antes do carregamento.                                                       |   2   |  D/V  |
| 9.2.4 | Verifique se a telemetria do sandbox é transmitida para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) geram alertas.                                                      |   2   |   V   |
| 9.2.5 | Verifique se os plugins de alto risco passam por revisão de segurança e testes de penetração antes do deployment em produção.                                                                 |   3   |   V   |
| 9.2.6 | Verifique se as tentativas de escape da sandbox são automaticamente bloqueadas e o plugin infrator é colocado em quarentena aguardando investigação.                                          |   3   |  D/V  |

---

## 9.3 Loop Autônomo e Limitação de Custos

Detectar e interromper a recursão descontrolada entre agentes e explosões de custo.

|   #   | Descrição                                                                                                                                                     | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.3.1 | Verifique se as chamadas entre agentes incluem um limite de saltos ou TTL que o tempo de execução decrementa e aplica.                                        |   1   |  D/V  |
| 9.3.2 | Verifique se os agentes mantêm um ID único de gráfico de invocação para detectar auto-invocação ou padrões cíclicos.                                          |   2   |   D   |
| 9.3.3 | Verifique que os contadores cumulativos de unidades de computação e gastos sejam monitorados por cadeia de requisições; ultrapassar o limite aborta a cadeia. |   2   |  D/V  |
| 9.3.4 | Verifique se a análise formal ou a verificação de modelo demonstra a ausência de recursão ilimitada nos protocolos do agente.                                 |   3   |   V   |
| 9.3.5 | Verifique se os eventos de aborto de loop geram alertas e alimentam métricas de melhoria contínua.                                                            |   3   |   D   |

---

## 9.4 Proteção contra Uso Indevido em Nível de Protocolo

Canais de comunicação seguros entre agentes e sistemas externos para prevenir sequestro ou manipulação.

|   #   | Descrição                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Verifique se todas as mensagens de agente para ferramenta e de agente para agente estão autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta. |   1   |  D/V  |
| 9.4.2 | Verifique se os esquemas são rigorosamente validados; campos desconhecidos ou mensagens malformadas são rejeitados.                                                     |   1   |   D   |
| 9.4.3 | Verifique se as verificações de integridade (MACs ou assinaturas digitais) cobrem toda a carga útil da mensagem, incluindo os parâmetros da ferramenta.                 |   2   |  D/V  |
| 9.4.4 | Verifique se a proteção contra reprodução (nonces ou janelas de carimbo de data/hora) está aplicada na camada de protocolo.                                             |   2   |   D   |
| 9.4.5 | Verifique se as implementações de protocolo passam por fuzzing e análise estática para identificar falhas de injeção ou desserialização.                                |   3   |   V   |

---

## 9.5 Identidade do Agente e Evidência de Violação

Assegure que as ações sejam atribuíveis e as modificações detectáveis.

|   #   | Descrição                                                                                                                                | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.5.1 | Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial ancorada em hardware).      |   1   |  D/V  |
| 9.5.2 | Verifique se todas as ações dos agentes são assinadas e carimbadas com data e hora; os logs devem incluir a assinatura para não repúdio. |   2   |  D/V  |
| 9.5.3 | Verifique se os logs à prova de adulteração são armazenados em um meio somente de anexação ou gravação única.                            |   2   |   V   |
| 9.5.4 | Verifique se as chaves de identidade giram em uma programação definida e conforme os indicadores de comprometimento.                     |   3   |   D   |
| 9.5.5 | Verifique se tentativas de falsificação ou conflito de chaves acionam a quarentena imediata do agente afetado.                           |   3   |  D/V  |

---

## 9.6 Redução de Risco em Enxame Multiagente

Mitigue riscos de comportamento coletivo por meio de isolamento e modelagem formal de segurança.

|   #   | Descrição                                                                                                                                             | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.6.1 | Verifique se os agentes que operam em diferentes domínios de segurança executam em sandboxes de tempo de execução isolados ou em segmentos de rede.   |   1   |  D/V  |
| 9.6.2 | Verifique se os comportamentos do enxame são modelados e formalmente verificados quanto à vivacidade e segurança antes da implantação.                |   3   |   V   |
| 9.6.3 | Verifique se os monitores em tempo de execução detectam padrões emergentes inseguros (por exemplo, oscilações, deadlocks) e iniciam ações corretivas. |   3   |   D   |

---

## 9.7 Autenticação / Autorização de Usuário e Ferramenta

Implemente controles de acesso robustos para cada ação acionada por agentes.

|   #   | Descrição                                                                                                                                               | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Verifique se os agentes se autenticam como principais de primeira classe nos sistemas descendentes, nunca reutilizando as credenciais do usuário final. |   1   |  D/V  |
| 9.7.2 | Verifique se as políticas de autorização granulares restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer.           |   2   |   D   |
| 9.7.3 | Verifique se as verificações de privilégios são reavaliadas a cada chamada (autorização contínua), e não somente no início da sessão.                   |   2   |   V   |
| 9.7.4 | Verifique se os privilégios delegados expiram automaticamente e exigem novo consentimento após o tempo limite ou alteração do escopo.                   |   3   |   D   |

---

## 9.8 Segurança da Comunicação Agente-para-Agente

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir espionagem e adulteração.

|   #   | Descrição                                                                                                                                             | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.8.1 | Verifique se a autenticação mútua e a criptografia com segredo perfeito à frente (por exemplo, TLS 1.3) são obrigatórias para os canais do agente.    |   1   |  D/V  |
| 9.8.2 | Verifique se a integridade e a origem da mensagem são validadas antes do processamento; falhas geram alertas e rejeitam a mensagem.                   |   1   |   D   |
| 9.8.3 | Verifique se os metadados de comunicação (carimbos de data e hora, números de sequência) são registrados para apoiar a reconstrução forense.          |   2   |  D/V  |
| 9.8.4 | Verifique se a verificação formal ou a checagem de modelos confirma que as máquinas de estado do protocolo não podem ser levadas a estados inseguros. |   3   |   V   |

---

## 9.9 Verificação de Intenção e Aplicação de Restrições

Validar que as ações do agente estejam alinhadas com a intenção declarada pelo usuário e as restrições do sistema.

|   #   | Descrição                                                                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.9.1 | Verifique se os solucionadores de restrições pré-execução verificam as ações propostas em relação às regras rígidas de segurança e políticas codificadas.                                                        |   1   |   D   |
| 9.9.2 | Verifique se ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) exigem confirmação explícita de intenção por parte do usuário que as iniciou.                                             |   2   |  D/V  |
| 9.9.3 | Verifique se as verificações de pós-condição confirmam que as ações concluídas alcançaram os efeitos pretendidos sem efeitos colaterais; discrepâncias acionam o rollback.                                       |   2   |   V   |
| 9.9.4 | Verifique se os métodos formais (por exemplo, verificação de modelos, demonstração de teoremas) ou testes baseados em propriedades demonstram que os planos do agente satisfazem todas as restrições declaradas. |   3   |   V   |
| 9.9.5 | Verifique se incidentes de incompatibilidade de intenção ou violação de restrições alimentam ciclos de melhoria contínua e compartilhamento de inteligência sobre ameaças.                                       |   3   |   D   |

---

## 9.10 Segurança da Estratégia de Raciocínio do Agente

Seleção e execução segura de diferentes estratégias de raciocínio, incluindo abordagens ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrição                                                                                                                                                                                                                                                      | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.10.1 | Verifique se a seleção da estratégia de raciocínio utiliza critérios determinísticos (complexidade da entrada, tipo de tarefa, contexto de segurança) e se entradas idênticas produzem seleções de estratégia idênticas dentro do mesmo contexto de segurança. |   1   |  D/V  |
| 9.10.2 | Verifique se cada estratégia de raciocínio (ReAct, Cadeia de Pensamento, Árvore de Pensamentos) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para sua abordagem cognitiva.                            |   1   |  D/V  |
| 9.10.3 | Verifique se as transições da estratégia de raciocínio são registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para a reconstrução da trilha de auditoria.                       |   2   |  D/V  |
| 9.10.4 | Verifique se o raciocínio Tree-of-Thoughts inclui mecanismos de poda de ramos que encerram a exploração quando são detectadas violações de políticas, limites de recursos ou limites de segurança.                                                             |   2   |  D/V  |
| 9.10.5 | Verifique se os ciclos ReAct (Raciocínio-Ação-Observação) incluem pontos de verificação de validação em cada fase: verificação do passo de raciocínio, autorização da ação e sanitização da observação antes de prosseguir.                                    |   2   |  D/V  |
| 9.10.6 | Verifique se as métricas de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) são monitoradas com alertas automatizados quando as métricas se desviam além dos limites configurados.                             |   3   |  D/V  |
| 9.10.7 | Verifique se as abordagens de raciocínio híbrido que combinam múltiplas estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes sem contornar quaisquer controles de segurança.                               |   3   |  D/V  |
| 9.10.8 | Verifique se o teste de segurança da estratégia de raciocínio inclui fuzzing com entradas malformadas, prompts adversariais projetados para forçar a troca de estratégia e testes de condição limite para cada abordagem cognitiva.                            |   3   |  D/V  |

---

## 9.11 Gerenciamento do Estado do Ciclo de Vida do Agente e Segurança

Inicialização segura do agente, transições de estado e término com trilhas de auditoria criptográficas e procedimentos definidos de recuperação.

|   #    | Descrição                                                                                                                                                                                                                                                                                 | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais suportadas por hardware e logs de auditoria imutáveis de inicialização contendo ID do agente, carimbo de data/hora, hash de configuração e parâmetros de inicialização.       |   1   |  D/V  |
| 9.11.2 | Verifique se as transições de estado do agente são assinadas criptograficamente, registradas com carimbo de data/hora e logadas com contexto completo, incluindo eventos que as desencadearam, hash do estado anterior, hash do novo estado e validações de segurança realizadas.         |   2   |  D/V  |
| 9.11.3 | Verifique se os procedimentos de desligamento do agente incluem limpeza segura da memória usando apagamento criptográfico ou sobrescrição múltipla, revogação de credenciais com notificação à autoridade certificadora e geração de certificados de término à prova de violação.         |   2   |  D/V  |
| 9.11.4 | Verifique se os mecanismos de recuperação do agente validam a integridade do estado usando checksums criptográficos (mínimo SHA-256) e fazem rollback para estados conhecidos como confiáveis quando a corrupção é detectada, com alertas automatizados e requisitos de aprovação manual. |   3   |  D/V  |
| 9.11.5 | Verifique se os mecanismos de persistência do agente criptografam dados de estado sensíveis com chaves AES-256 por agente e implementam rotação segura de chaves em cronogramas configuráveis (máximo de 90 dias) com implantação sem tempo de inatividade.                               |   3   |  D/V  |

---

## 9.12 Estrutura de Segurança para Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com processos definidos de avaliação de risco e aprovação.

|   #    | Descrição                                                                                                                                                                                                                                                                                     | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Verifique se os descritores da ferramenta incluem metadados de segurança especificando privilégios necessários (leitura/gravação/execução), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados nos manifestos da ferramenta. |   1   |  D/V  |
| 9.12.2 | Verifique se os resultados da execução da ferramenta são validados contra os esquemas esperados (Esquema JSON, Esquema XML) e políticas de segurança (sanitização de saída, classificação de dados) antes da integração, com limites de tempo e procedimentos de tratamento de erros.         |   1   |  D/V  |
| 9.12.3 | Verifique se os logs de interação da ferramenta incluem contexto detalhado de segurança, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com logging estruturado para integração com SIEM.                              |   2   |  D/V  |
| 9.12.4 | Verifique se os mecanismos de carregamento dinâmico de ferramentas validam assinaturas digitais usando a infraestrutura de PKI e implementam protocolos de carregamento seguro com isolamento em sandbox e verificação de permissões antes da execução.                                       |   2   |  D/V  |
| 9.12.5 | Verifique se as avaliações de segurança da ferramenta são acionadas automaticamente para novas versões com portas de aprovação obrigatórias, incluindo análise estática, testes dinâmicos e revisão da equipe de segurança, com critérios de aprovação documentados e requisitos de SLA.      |   3   |  D/V  |

---

## C9.13 Protocolo de Contexto de Modelo (MCP) Segurança

Garantir a descoberta, autenticação, autorização, transporte e uso seguros das integrações de ferramentas e recursos baseados em MCP para evitar confusão de contexto, invocação não autorizada de ferramentas ou exposição de dados entre diferentes locatários.

### Integridade do Componente e Higiene da Cadeia de Suprimentos

|   #    | Descrição                                                                                                                                                                                                                                                                   | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.13.1 | Verifique se as implementações do servidor, cliente e ferramenta MCP são revisadas manualmente ou analisadas automaticamente para identificar exposição de funções inseguras, configurações padrão inseguras, falta de autenticação ou ausência de validação de entrada.    |   1   |  D/V  |
| 9.13.2 | Verifique se servidores ou pacotes MCP externos ou de código aberto passam por varredura automatizada de vulnerabilidades e da cadeia de suprimentos (por exemplo, SCA) antes da integração, e que componentes com vulnerabilidades críticas conhecidas não são utilizados. |   1   |  D/V  |
| 9.13.3 | Verifique se os componentes do servidor e cliente MCP são obtidos apenas de fontes confiáveis e verificados usando assinaturas, somas de verificação ou metadados seguros de pacote, rejeitando versões adulteradas ou não assinadas.                                       |   1   |  D/V  |

### Autenticação e Autorização

|   #    | Descrição                                                                                                                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.13.4 | Verifique se os clientes e servidores MCP autenticam-se mutuamente usando credenciais fortes, que não sejam de usuário (por exemplo, mTLS, tokens assinados ou identidades emitidas pela plataforma), e que endpoints MCP não autenticados sejam rejeitados.                      |   2   |  D/V  |
| 9.13.5 | Verifique se os servidores MCP estão registrados por meio de um mecanismo controlado de integração técnica que exija definições explícitas de proprietário, ambiente e recurso; servidores não registrados ou indisponíveis para descoberta não devem ser acessíveis em produção. |   2   |  D/V  |
| 9.13.6 | Verifique se cada ferramenta ou recurso MCP define escopos de autorização explícitos (por exemplo, somente leitura, consultas restritas, níveis de efeito colateral) e se os agentes não podem invocar funções MCP fora de seu escopo atribuído.                                  |   2   |  D/V  |

### Transporte Seguro e Proteção da Fronteira de Rede

|    #    | Descrição                                                                                                                                                                                                                                                                             | Nível | Papel |
| :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.13.7  | Verifique se o HTTP transmissível autenticado e criptografado é usado como o principal transporte MCP em ambientes de produção; transportes alternativos (stdio, SSE) são restritos a ambientes locais ou rigorosamente controlados com justificativa explícita.                      |   2   |  D/V  |
| 9.13.8  | Verifique se os transportes streamable-HTTP MCP utilizam canais autenticados e criptografados (TLS 1.3 ou superior) com validação de certificado e segredo à frente para garantir a confidencialidade e integridade das mensagens MCP transmitidas.                                   |   2   |  D/V  |
| 9.13.9  | Verifique se os transportes MCP baseados em SSE são usados apenas dentro de canais internos privados e autenticados e aplique TLS, autenticação, validação de esquema, limites de tamanho de payload e limitação de taxa; os endpoints SSE não devem ser expostos à internet pública. |   2   |  D/V  |
| 9.13.10 | Verifique se os servidores MCP validam o`Origin` e`Host` Cabeçalhos em todos os transportes baseados em HTTP (incluindo SSE e HTTP transmissível) para prevenir ataques de reatribuição de DNS e rejeitar solicitações de origens não confiáveis, incompatíveis ou ausentes.          |   2   |  D/V  |

### Validação de Esquema, Mensagem e Entrada

|    #    | Descrição                                                                                                                                                                                                                                                                                                               | Nível | Papel |
| :-----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.13.11 | Verifique se os esquemas de ferramentas e recursos do MCP (por exemplo, esquemas JSON ou descritores de capacidade) são validados quanto à autenticidade e integridade usando assinaturas, somas de verificação ou atestação do servidor para prevenir adulteração dos esquemas ou modificação maliciosa de parâmetros. |   2   |  D/V  |
| 9.13.12 | Verifique se todos os transportes MCP aplicam a integridade da estrutura das mensagens, validação rigorosa de esquema, tamanhos máximos de carga útil e rejeição de quadros malformados, truncados ou intercalados para evitar ataques de dessincronização ou injeção.                                                  |   2   |  D/V  |
| 9.13.13 | Verifique se os servidores MCP realizam validação rigorosa de entrada para todas as chamadas de função, incluindo verificação de tipo, verificação de limites, aplicação de enumeração e rejeição de parâmetros não reconhecidos ou de tamanho excessivo.                                                               |   2   |  D/V  |

### Acesso de Saída e Segurança na Execução de Agentes

|    #    | Descrição                                                                                                                                                                                                                                                                | Nível | Papel |
| :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.13.14 | Verifique se os servidores MCP podem iniciar solicitações de saída apenas para destinos internos ou externos aprovados, seguindo políticas de egressos com privilégio mínimo, e não podem acessar alvos de rede arbitrários ou serviços de metadados internos da nuvem.  |   2   |  D/V  |
| 9.13.15 | Verifique se as ações MCP de saída implementam limites de execução (tempos limite, limites de recursão, limites de concorrência, disjuntores) para evitar invocações ilimitadas de ferramentas dirigidas por agentes ou efeitos colaterais encadeados.                   |   2   |  D/V  |
| 9.13.16 | Verifique se os metadados da solicitação e resposta do MCP (ID do servidor, nome do recurso, nome da ferramenta, identificador da sessão, locatário, ambiente) são registrados com proteção de integridade e correlacionados à atividade do agente para análise forense. |   2   |  D/V  |

### Restrições de Transporte e Controles de Limite de Alto Risco

|    #    | Descrição                                                                                                                                                                                                                                                                                     | Nível | Papel |
| :-----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.13.17 | Verifique se os transportes MCP baseados em stdio estão limitados a cenários de desenvolvimento de processo único e co-localizados, isolados da execução do shell, injeção de terminal e capacidades de criação de processos; stdio nunca deve cruzar fronteiras de rede ou multi-inquilinos. |   3   |  D/V  |
| 9.13.18 | Verifique se os servidores MCP expõem apenas funções e recursos na lista de permissões, e proíbem despacho dinâmico, invocação reflexiva ou execução de nomes de funções influenciados por entradas fornecidas pelo usuário ou pelo modelo.                                                   |   3   |  D/V  |
| 9.13.19 | Verifique se os limites de locatário, limites de ambiente (dev/teste/prod) e limites de domínio de dados são aplicados na camada MCP, prevenindo a descoberta cruzada de servidores ou recursos entre locatários ou ambientes.                                                                |   3   |  D/V  |

---

### Referências

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)
* [Model Context Protocol Specification](https://modelcontextprotocol.io)
* [Model Context Protocol Tools & Resources Specification](https://modelcontextprotocol.io/specification/2025-06-18/basic)
* [Model Context Protocol Transport Documentation](https://modelcontextprotocol.io/specification/2025-06-18/basic/transports)
* [OWASP GenAI Security Project — “A Practical Guide for Securely Using Third-Party MCP Servers 1.0”](https://genai.owasp.org/resource/cheatsheet-a-practical-guide-for-securely-using-third-party-mcp-servers-1-0/)
* [Cloud Security Alliance – Model Context Protocol Security Working Group](https://modelcontextprotocol-security.io)
* [CSA MCP Security: Top 10 Risks](https://modelcontextprotocol-security.io/top10/)
* [CSA MCP Security: TTPs & Hardening Guidance](https://modelcontextprotocol-security.io/ttps/)

