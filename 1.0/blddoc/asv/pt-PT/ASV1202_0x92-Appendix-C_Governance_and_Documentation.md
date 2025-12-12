# Apêndice C: Governança e Documentação de Segurança em IA (Reorganizado)

## Objetivo

Este apêndice fornece requisitos fundamentais para estabelecer estruturas organizacionais, políticas, documentação e processos para governar a segurança de IA ao longo do ciclo de vida do sistema.

---

## AC.1 Adoção do Framework de Gestão de Riscos em IA

|   #    | Descrição                                                                                                                  | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.1.1 | Verifique se uma metodologia de avaliação de risco específica para IA está documentada e implementada.                     |   1   |  D/V  |
| AC.1.2 | Verifique se avaliações de risco são realizadas em pontos-chave do ciclo de vida da IA e antes de mudanças significativas. |   2   |   D   |
| AC.1.3 | Verifique se o framework de gerenciamento de riscos está alinhado com os padrões estabelecidos (por exemplo, NIST AI RMF). |   3   |  D/V  |

---

## AC.2 Política e Procedimentos de Segurança de IA

|   #    | Descrição                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.2.1 | Verifique se existem políticas de segurança de IA documentadas.                                                                   |   1   |  D/V  |
| AC.2.2 | Verifique se as políticas são revisadas e atualizadas pelo menos anualmente e após mudanças significativas no cenário de ameaças. |   2   |   D   |
| AC.2.3 | Verifique se as políticas abrangem todas as categorias AISVS e os requisitos regulamentares aplicáveis.                           |   3   |  D/V  |

---

## AC.3 Papéis e Responsabilidades para Segurança de IA

|   #    | Descrição                                                                                                              | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.3.1 | Verifique se os papéis e responsabilidades de segurança de IA estão documentados.                                      |   1   |  D/V  |
| AC.3.2 | Verifique se os indivíduos responsáveis possuem a expertise adequada em segurança.                                     |   2   |   D   |
| AC.3.3 | Verifique se um comitê de ética em IA ou um conselho de governança foi estabelecido para sistemas de IA de alto risco. |   3   |  D/V  |

---

## AC.4 Diretrizes Éticas para a Aplicação de IA

|   #    | Descrição                                                                             | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------- | :---: | :---: |
| AC.4.1 | Verifique se existem diretrizes éticas para o desenvolvimento e implantação de IA.    |   1   |  D/V  |
| AC.4.2 | Verifique se existem mecanismos para detectar e relatar violações éticas.             |   2   |   D   |
| AC.4.3 | Verifique se revisões éticas regulares dos sistemas de IA implantados são realizadas. |   3   |  D/V  |

---

## AC.5 Monitoramento de Conformidade Regulatória de IA

|   #    | Descrição                                                                                                | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.5.1 | Verifique se existem processos para identificar as regulamentações de IA aplicáveis.                     |   1   |  D/V  |
| AC.5.2 | Verifique se a conformidade com todos os requisitos regulatórios está avaliada.                          |   2   |   D   |
| AC.5.3 | Verifique se as mudanças regulatórias desencadeiam revisões e atualizações oportunas nos sistemas de IA. |   3   |  D/V  |

---

## AC.6 Governança, Documentação e Processo de Dados de Treinamento

### AC.6.1 Fonte de Dados & Diligência Devida

|    #     | Descrição                                                                                                                                                                                                                                                                                                                                          | Nível | Papel |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.1.1 | Verifique se apenas conjuntos de dados avaliados quanto à qualidade, representatividade, origem ética e conformidade de licença são permitidos, reduzindo os riscos de contaminação, viés embutido e violação de propriedade intelectual.                                                                                                          |   1   |  D/V  |
| AC.6.1.2 | Verifique se os fornecedores de dados terceiros, incluindo provedores de modelos pré-treinados e conjuntos de dados externos, passam por diligência devida em segurança, privacidade, origem ética e qualidade dos dados antes que seus dados ou modelos sejam integrados.                                                                         |   2   |  D/V  |
| AC.6.1.3 | Verifique se as transferências externas utilizam TLS/autenticação e verificações de integridade.                                                                                                                                                                                                                                                   |   1   |   D   |
| AC.6.1.4 | Verifique se as fontes de dados de alto risco (por exemplo, conjuntos de dados de código aberto com procedência desconhecida, fornecedores não avaliados) recebem uma análise aprimorada, como análise em ambiente isolado, verificações extensas de qualidade/viés e detecção direcionada de envenenamento, antes do uso em aplicações sensíveis. |   2   |  D/V  |
| AC.6.1.5 | Verifique se os modelos pré-treinados obtidos de terceiros são avaliados quanto a vieses incorporados, possíveis backdoors, integridade de sua arquitetura e a proveniência dos dados originais de treinamento antes do ajuste fino ou implantação.                                                                                                |   3   |  D/V  |

### AC.6.2 Gestão de Viés e Justiça

|    #     | Descrição                                                                                                                                                                                                                                                                                                                                                     | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.2.1 | Verifique se os conjuntos de dados são analisados quanto a desequilíbrios representacionais e potenciais vieses em atributos legalmente protegidos (por exemplo, raça, gênero, idade) e outras características eticamente sensíveis relevantes para o domínio de aplicação do modelo (por exemplo, status socioeconômico, localização).                       |   1   |  D/V  |
| AC.6.2.2 | Verifique se os vieses identificados são mitigados por meio de estratégias documentadas, como reequilíbrio, aumento de dados direcionado, ajustes algorítmicos (por exemplo, técnicas de pré-processamento, processamento e pós-processamento) ou reponderação, e se o impacto da mitigação tanto na justiça quanto no desempenho geral do modelo é avaliado. |   2   |  D/V  |
| AC.6.2.3 | Verifique se as métricas de equidade pós-treinamento são avaliadas e documentadas.                                                                                                                                                                                                                                                                            |   2   |  D/V  |
| AC.6.2.4 | Verifique se uma política de gerenciamento de viés ao longo do ciclo de vida atribui responsáveis e uma cadência de revisão.                                                                                                                                                                                                                                  |   3   |  D/V  |

### AC.6.3 Governança de Rotulagem e Anotação

|     #     | Descrição                                                                                                                                                                                                                                                          | Nível | Papel |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.6.3.1  | Verifique se a qualidade da rotulagem/anotação é garantida por meio de verificações cruzadas dos revisores ou consenso.                                                                                                                                            |   2   |  D/V  |
| AC.6.3.2  | Verifique se os cartões de dados são mantidos para conjuntos de dados de treinamento significativos, detalhando características, motivações, composição, processos de coleta, pré-processamento, licenças e usos recomendados/desencorajados.                      |   2   |  D/V  |
| AC.6.3.3  | Verifique se os cartões de dados documentam os riscos de viés, distorções demográficas e considerações éticas relevantes para o conjunto de dados.                                                                                                                 |   2   |  D/V  |
| AC.6.3.4  | Verifique se os cartões de dados são versionados junto com os conjuntos de dados e atualizados sempre que o conjunto de dados for modificado.                                                                                                                      |   2   |  D/V  |
| AC.6.3.5  | Verifique se os cartões de dados são revisados e aprovados por partes interessadas técnicas e não técnicas (por exemplo, conformidade, ética, especialistas no domínio).                                                                                           |   2   |  D/V  |
| AC.6.3.6  | Verifique se a qualidade da rotulagem/anotação é garantida por meio de diretrizes claras, revisões cruzadas por avaliadores, mecanismos de consenso (por exemplo, monitoramento do acordo entre anotadores) e processos definidos para resolução de discrepâncias. |   2   |  D/V  |
| AC.6.3.7  | Verifique se os rótulos críticos para segurança, proteção ou justiça (por exemplo, identificação de conteúdo tóxico, descobertas médicas críticas) recebem uma revisão dupla independente obrigatória ou uma verificação robusta equivalente.                      |   3   |  D/V  |
| AC.6.3.8  | Verifique se os guias de rotulagem e instruções são abrangentes, controlados por versão e revisados por pares.                                                                                                                                                     |   2   |  D/V  |
| AC.6.3.9  | Verifique se os esquemas de dados para rótulos estão claramente definidos e controlados por versão.                                                                                                                                                                |   2   |  D/V  |
| AC.6.3.10 | Verifique se os fluxos de trabalho de rotulagem terceirizados ou crowdsourced incluem salvaguardas técnicas/procedimentais para garantir a confidencialidade dos dados, integridade, qualidade dos rótulos e prevenir o vazamento de dados.                        |   2   |  D/V  |
| AC.6.3.11 | Verifique se todo o pessoal envolvido na anotação de dados passou por verificação de antecedentes e foi treinado em segurança e privacidade de dados.                                                                                                              |   2   |  D/V  |
| AC.6.3.12 | Verifique se todo o pessoal de anotação assina acordos de confidencialidade e não divulgação.                                                                                                                                                                      |   2   |  D/V  |
| AC.6.3.13 | Verifique se as plataformas de anotação aplicam controles de acesso e monitoram ameaças internas.                                                                                                                                                                  |   2   |  D/V  |

### AC.6.4 Portões de Qualidade de Conjunto de Dados e Quarentena

|    #     | Descrição                                                                                                                                                                                                                                                                                                                            | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.6.4.1 | Verifique se os conjuntos de dados com falha estão isolados em quarentena com trilhas de auditoria.                                                                                                                                                                                                                                  |   2   |  D/V  |
| AC.6.4.2 | Verifique se os gateways de qualidade bloqueiam conjuntos de dados abaixo do padrão, a menos que exceções sejam aprovadas.                                                                                                                                                                                                           |   2   |  D/V  |
| AC.6.4.3 | Verifique se as verificações manuais pontuais realizadas por especialistas no domínio cobrem uma amostra estatisticamente significativa (por exemplo, ≥1% ou 1.000 amostras, o que for maior, ou conforme determinado pela avaliação de risco) para identificar questões sutis de qualidade que não foram detectadas pela automação. |   2   |   V   |

### AC.6.5 Detecção de Ameaças/Envenenamento e Desvio

|    #     | Descrição                                                                                                               | Nível | Papel |
| :------: | ----------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.5.1 | Verifique se as amostras sinalizadas acionam uma revisão manual antes do treinamento.                                   |   2   |  D/V  |
| AC.6.5.2 | Verifique se os resultados alimentam o dossiê de segurança do modelo e informam a inteligência de ameaças em andamento. |   2   |   V   |
| AC.6.5.3 | Verifique se a lógica de detecção está atualizada com novas informações de ameaças.                                     |   3   |  D/V  |
| AC.6.5.4 | Verifique se os pipelines de aprendizado online monitoram a mudança na distribuição.                                    |   3   |  D/V  |

### AC.6.6 Exclusão, Consentimento, Direitos, Retenção e Conformidade

|     #     | Descrição                                                                                                                                                                                                                                                                                                  | Nível | Papel |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.6.1  | Verifique se os fluxos de trabalho de exclusão de dados de treinamento eliminam dados primários e derivados e avalie o impacto no modelo, e se o impacto nos modelos afetados é avaliado e, se necessário, tratado (por exemplo, por meio de re-treinamento ou recalibração).                              |   1   |  D/V  |
| AC.6.6.2  | Verifique se existem mecanismos para rastrear e respeitar o escopo e o status do consentimento do usuário (e retiradas) para dados usados no treinamento, e se o consentimento é validado antes que os dados sejam incorporados a novos processos de treinamento ou atualizações significativas do modelo. |   2   |   D   |
| AC.6.6.3  | Verifique se os fluxos de trabalho são testados anualmente e registrados.                                                                                                                                                                                                                                  |   2   |   V   |
| AC.6.6.4  | Verifique se os períodos explícitos de retenção estão definidos para todos os conjuntos de dados de treinamento.                                                                                                                                                                                           |   1   |  D/V  |
| AC.6.6.5  | Verifique se os conjuntos de dados são automaticamente expirados, excluídos ou revisados para exclusão ao final de seu ciclo de vida.                                                                                                                                                                      |   2   |  D/V  |
| AC.6.6.6  | Verifique se as ações de retenção e exclusão são registradas e auditáveis.                                                                                                                                                                                                                                 |   2   |  D/V  |
| AC.6.6.7  | Verifique se os requisitos de residência de dados e transferência transfronteiriça são identificados e aplicados para todos os conjuntos de dados.                                                                                                                                                         |   2   |  D/V  |
| AC.6.6.8  | Verifique se as regulamentações específicas do setor (por exemplo, saúde, finanças) são identificadas e atendidas no manuseio de dados.                                                                                                                                                                    |   2   |  D/V  |
| AC.6.6.9  | Verifique se a conformidade com as leis de privacidade relevantes (por exemplo, GDPR, CCPA) está documentada e revisada regularmente.                                                                                                                                                                      |   2   |  D/V  |
| AC.6.6.10 | Verifique se existem mecanismos para responder a solicitações de titulares de dados para acesso, retificação, restrição ou objeção.                                                                                                                                                                        |   2   |  D/V  |
| AC.6.6.11 | Verifique se as solicitações são registradas, monitoradas e atendidas dentro dos prazos legais estabelecidos.                                                                                                                                                                                              |   2   |  D/V  |
| AC.6.6.12 | Verifique se os processos de direitos do titular dos dados são testados e revisados regularmente quanto à eficácia.                                                                                                                                                                                        |   2   |  D/V  |

### AC.6.7 Controle de Versão e Gestão de Mudanças

|    #     | Descrição                                                                                                                                                                   | Nível | Papel |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.7.1 | Verifique se uma análise de impacto é realizada antes de atualizar ou substituir uma versão do conjunto de dados, abrangendo desempenho do modelo, equidade e conformidade. |   2   |  D/V  |
| AC.6.7.2 | Verifique se os resultados da análise de impacto estão documentados e revisados pelos stakeholders relevantes.                                                              |   2   |  D/V  |
| AC.6.7.3 | Verifique se existem planos de reversão caso novas versões introduzam riscos inaceitáveis ou regressões.                                                                    |   2   |  D/V  |

### AC.6.8 Governança de Dados Sintéticos

|    #     | Descrição                                                                                                                                                       | Nível | Papel |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.8.1 | Verifique se o processo de geração, os parâmetros e o uso pretendido dos dados sintéticos estão documentados.                                                   |   2   |  D/V  |
| AC.6.8.2 | Verifique se os dados sintéticos são avaliados quanto ao risco de viés, vazamento de privacidade e problemas de representatividade antes do uso no treinamento. |   2   |  D/V  |

### AC.6.9 Monitoramento de Acesso

|    #     | Descrição                                                                                                                                                            | Nível | Papel |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.9.1 | Verifique se os registros de acesso são revisados regularmente para identificar padrões incomuns, como grandes exportações ou acesso a partir de novas localizações. |   2   |  D/V  |
| AC.6.9.2 | Verifique se os alertas são gerados para eventos de acesso suspeitos e investigados prontamente.                                                                     |   2   |  D/V  |

### AC.6.10 Governança do Treinamento Adversarial

|     #     | Descrição                                                                                                                                                                                                 | Nível | Papel |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.6.10.1 | Verifique se, quando o treinamento adversarial é utilizado, a geração, o gerenciamento e o versionamento dos conjuntos de dados adversariais estão documentados e controlados.                            |   2   |  D/V  |
| AC.6.10.2 | Verifique se o impacto do treinamento de robustez adversarial no desempenho do modelo (tanto contra entradas limpas quanto adversariais) e nas métricas de equidade é avaliado, documentado e monitorado. |   3   |  D/V  |
| AC.6.10.3 | Verifique se as estratégias para treinamento adversarial e robustez são periodicamente revisadas e atualizadas para combater as técnicas de ataque adversarial em evolução.                               |   3   |  D/V  |

---

## AC.7 Governança e Documentação do Ciclo de Vida do Modelo

|   #    | Descrição                                                                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.7.1 | Verifique se todos os artefatos do modelo utilizam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados especificando quando cada componente da versão deve ser incrementado. |   2   |  D/V  |
| AC.7.2 | Verifique se as implantações de emergência exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança pré-designada dentro dos prazos pré-acordados.         |   2   |  D/V  |
| AC.7.3 | Verifique se os artefatos de rollback (versões anteriores do modelo, configurações, dependências) são mantidos conforme as políticas organizacionais.                                           |   2   |   V   |
| AC.7.4 | Verifique se o acesso ao log de auditoria requer autorização adequada e se todas as tentativas de acesso são registradas com a identidade do usuário e um carimbo de data/hora.                 |   2   |  D/V  |
| AC.7.5 | Verifique se os artefatos de modelos aposentados são mantidos de acordo com as políticas de retenção de dados.                                                                                  |   1   |  D/V  |

---

## Governança de Segurança de Prompt, Entrada e Saída AC.8

### AC.8.1 Defesa contra Injeção de Prompt

|    #     | Descrição                                                                                                                                                                                                                                          | Nível | Papel |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.8.1.1 | Verifique se os testes de avaliação adversarial (por exemplo, prompts "many-shot" da Red Team) são realizados antes de cada lançamento de modelo ou template de prompt, com limites de taxa de sucesso e bloqueadores automáticos para regressões. |   2   |  D/V  |
| AC.8.1.2 | Verifique se todas as atualizações das regras de filtro de prompt, versões do modelo classificador e alterações na lista de bloqueio são controladas por versão e auditáveis.                                                                      |   3   |  D/V  |

### AC.8.2 Resistência a Exemplos Adversariais

|    #     | Descrição                                                                                                                                                                            | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.8.2.1 | Verifique se as métricas de robustez (taxa de sucesso de conjuntos de ataques conhecidos) são monitoradas ao longo do tempo por meio de automação e se regressões acionam um alerta. |   3   |  D/V  |

### AC.8.3 Triagem de Conteúdo e Política

|    #     | Descrição                                                                                                                                                                                     | Nível | Papel |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.8.3.1 | Verifique se o modelo de triagem ou o conjunto de regras é re-treinado/atualizado pelo menos trimestralmente, incorporando novos padrões de jailbreak ou de violação de políticas observados. |   2   |   D   |

### AC.8.4 Limitação da Taxa de Entrada e Prevenção de Abuso

|    #     | Descrição                                                                                                                 | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.8.4.1 | Verifique se os registros de prevenção de abusos são mantidos e revisados para identificar padrões de ataques emergentes. |   3   |   V   |

### AC.8.5 Procedência e Atribuição de Entrada

|    #     | Descrição                                                                                                                                                      | Nível | Papel |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.8.5.1 | Verifique se todas as entradas de usuário são marcadas com metadados (ID do usuário, sessão, fonte, carimbo de data/hora, endereço IP) no momento da ingestão. |   1   |  D/V  |
| AC.8.5.2 | Verifique se os metadados de proveniência são mantidos e auditáveis para todas as entradas processadas.                                                        |   2   |  D/V  |
| AC.8.5.3 | Verifique se fontes de entrada anômalas ou não confiáveis são sinalizadas e sujeitas a escrutínio aprimorado ou bloqueio.                                      |   2   |  D/V  |

---

## AC.9 Validação Multimodal, MLOps e Governança de Infraestrutura

### AC.9.1 Pipeline de Validação de Segurança Multimodal

|    #     | Descrição                                                                                                                                                                                                                                                                | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.9.1.1 | Verifique se os classificadores de conteúdo específicos por modalidade são atualizados conforme os cronogramas documentados (mínimo trimestralmente) com novos padrões de ameaças, exemplos adversariais e benchmarks de desempenho mantidos acima dos limiares básicos. |   3   |  D/V  |

### AC.9.2 Segurança de CI/CD e Build

|    #     | Descrição                                                                                                                                                   | Nível | Papel |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.2.1 | Verifique se a infraestrutura como código é analisada em cada commit e se as mesclagens são bloqueadas quando há descobertas de severidade crítica ou alta. |   1   |  D/V  |
| AC.9.2.2 | Verifique se os pipelines CI/CD utilizam identidades de curta duração e com escopo limitado para acesso a segredos e infraestrutura.                        |   2   |  D/V  |
| AC.9.2.3 | Verifique se os ambientes de build estão isolados das redes e dados de produção.                                                                            |   2   |  D/V  |

### AC.9.3 Segurança de Contêineres e Imagens

|    #     | Descrição                                                                                                                                                                                              | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.9.3.1 | Verifique se as imagens de contêiner são escaneadas para bloquear segredos hardcoded (por exemplo, chaves de API, credenciais, certificados).                                                          |   2   |  D/V  |
| AC.9.3.2 | Verifique se as imagens de contêiner são examinadas de acordo com os cronogramas organizacionais, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limites de risco organizacional. |   1   |  D/V  |

### AC.9.4 Monitoramento, Alertas e SIEM

|    #     | Descrição                                                                                                                                                                     | Nível | Papel |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.4.1 | Verifique se os alertas de segurança se integram com plataformas SIEM (Splunk, Elastic ou Sentinel) utilizando os formatos CEF ou STIX/TAXII com enriquecimento automatizado. |   2   |   V   |

### AC.9.5 Gestão de Vulnerabilidades

|    #     | Descrição                                                                                                                                                                                                    | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.9.5.1 | Verifique se as vulnerabilidades de alta gravidade estão corrigidas de acordo com os prazos de gerenciamento de risco organizacional, incluindo procedimentos de emergência para CVEs explorados ativamente. |   2   |  D/V  |

### AC.9.6 Controle de Configuração e Deriva

|    #     | Descrição                                                                                                                                                                                                                | Nível | Papel |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.9.6.1 | Verifique se a deriva de configuração é detectada utilizando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento organizacional, com reversão automática para alterações não autorizadas. |   2   |  D/V  |

### AC.9.7 Endurecimento do Ambiente de Produção

|    #     | Descrição                                                                                                                                                                                                      | Nível | Papel |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.7.1 | Verifique se os ambientes de produção bloqueiam o acesso SSH, desativam os pontos finais de depuração e exigem solicitações de alteração com requisitos de aviso prévio organizacional, exceto em emergências. |   2   |  D/V  |

### Portões de Promoção de Versão AC.9.8

|    #     | Descrição                                                                                                                                                             | Nível | Papel |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.8.1 | Verifique se os portões de promoção incluem testes automatizados de segurança (SAST, DAST, varredura de container) com zero achados CRÍTICOS exigidos para aprovação. |   2   |  D/V  |

### AC.9.9 Monitoramento de Carga de Trabalho, Capacidade e Custo

|    #     | Descrição                                                                                                                                                                                                                                          | Nível | Papel |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.9.1 | Verifique se a utilização da GPU/TPU é monitorada com alertas acionados em limiares definidos pela organização e se o dimensionamento automático ou o balanceamento de carga são ativados com base em políticas de gerenciamento de capacidade.    |   1   |  D/V  |
| AC.9.9.2 | Verifique se as métricas de carga de trabalho de IA (latência de inferência, taxa de transferência, taxas de erro) são coletadas de acordo com os requisitos de monitoramento organizacional e correlacionadas com a utilização da infraestrutura. |   1   |  D/V  |
| AC.9.9.3 | Verifique se o monitoramento de custos acompanha os gastos por carga de trabalho/inquilino com alertas baseados nos limites orçamentários organizacionais e controles automatizados para excessos de orçamento.                                    |   2   |   V   |
| AC.9.9.4 | Verifique se o planejamento de capacidade utiliza dados históricos com períodos de previsão definidos pela organização e provisionamento automatizado de recursos com base em padrões de demanda.                                                  |   3   |   V   |

### AC.9.10 Aprovações e Trilhas de Auditoria

|     #     | Descrição                                                                                                                                                               | Nível | Papel |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.10.1 | Verifique que a promoção de ambiente requer aprovação de pessoal autorizado definido pela organização, com assinaturas criptográficas e trilhas de auditoria imutáveis. |   1   |  D/V  |

### AC.9.11 Governança de IaC

|     #     | Descrição                                                                                                                                                                 | Nível | Papel |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.11.1 | Verifique se as alterações de infraestrutura como código exigem revisão por pares com testes automatizados e análise de segurança antes da mesclagem na branch principal. |   2   |  D/V  |

### AC.9.12 Manipulação de Dados em Ambiente Não-Produtivo

|     #     | Descrição                                                                                                                                                                                                                                                 | Nível | Papel |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.12.1 | Verifique se os dados fora de produção estão anonimizados de acordo com os requisitos organizacionais de privacidade, geração de dados sintéticos ou mascaramento completo dos dados com remoção de informações pessoais identificáveis (PII) verificada. |   2   |  D/V  |

### AC.9.13 Backup & Recuperação de Desastres

|     #     | Descrição                                                                                                                                                                                                                           | Nível | Papel |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.13.1 | Verifique se as configurações da infraestrutura estão sendo copiadas de segurança de acordo com os cronogramas de backup organizacionais para regiões geograficamente separadas, com a implementação da estratégia de backup 3-2-1. |   1   |  D/V  |
| AC.9.13.2 | Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados de acordo com os cronogramas organizacionais, com as metas de RTO e RPO atendendo aos requisitos da organização.             |   2   |   V   |
| AC.9.13.3 | Verifique se a recuperação de desastres inclui runbooks específicos para IA com restauração de pesos do modelo, reconstrução de cluster GPU e mapeamento de dependências de serviço.                                                |   3   |   V   |

### AC.9.14 Conformidade e Documentação

|     #     | Descrição                                                                                                                                                                                                 | Nível | Papel |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.14.1 | Verifique se a conformidade da infraestrutura é avaliada conforme os cronogramas organizacionais em relação aos controles SOC 2, ISO 27001 ou FedRAMP, com coleta automatizada de evidências.             |   2   |  D/V  |
| AC.9.14.2 | Verifique se a documentação da infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaça atualizados de acordo com os requisitos de gerenciamento de mudanças organizacionais. |   2   |   V   |
| AC.9.14.3 | Verifique se as alterações na infraestrutura passam por uma avaliação automatizada de impacto de conformidade com fluxos de trabalho de aprovação regulatória para modificações de alto risco.            |   3   |  D/V  |

### AC.9.15 Hardware e Cadeia de Suprimentos

|     #     | Descrição                                                                                                                                                                                               | Nível | Papel |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.15.1 | Verifique se o firmware do acelerador de IA (BIOS da GPU, firmware do TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os prazos de gerenciamento de patches da organização. |   2   |  D/V  |
| AC.9.15.2 | Verifique se a cadeia de suprimentos de hardware de IA inclui a verificação de procedência com certificados do fabricante e validação de embalagem à prova de violação.                                 |   3   |   V   |

### AC.9.16 Estratégia e Portabilidade na Nuvem

|     #     | Descrição                                                                                                                                                                                               | Nível | Papel |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.16.1 | Verifique se a prevenção do bloqueio do fornecedor de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formato. |   3   |   V   |
| AC.9.16.2 | Verifique se a otimização de custos multi-cloud inclui controles de segurança que evitam o espalhamento de recursos, bem como cobranças não autorizadas de transferência de dados entre nuvens.         |   3   |   V   |

### AC.9.17 GitOps e Auto-Cura

|     #     | Descrição                                                                                                                                                                              | Nível | Papel |
| :-------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AC.9.17.1 | Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de branch que impeçam pushes diretos para os branches principais.                     |   2   |  D/V  |
| AC.9.17.2 | Verifique se a infraestrutura autocurável inclui correlação de eventos de segurança com resposta automatizada a incidentes e fluxos de trabalho de notificação às partes interessadas. |   3   |   V   |

### AC.9.18 Confiança Zero, Agentes, Provisionamento e Atenticação de Residência

|     #     | Descrição                                                                                                                                                                | Nível | Papel |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| AC.9.18.1 | Verifique se o acesso aos recursos na nuvem inclui verificação de zero-confiança com autenticação contínua.                                                              |   2   |  D/V  |
| AC.9.18.2 | Verifique se o provisionamento automatizado de infraestrutura inclui a validação da política de segurança com bloqueio de implantação para configurações não conformes.  |   2   |  D/V  |
| AC.9.18.3 | Verifique se o provisionamento automatizado da infraestrutura valida as políticas de segurança durante o CI/CD, bloqueando configurações não conformes para implantação. |   2   |  D/V  |
| AC.9.18.4 | Verifique se os requisitos de residência de dados são aplicados por meio de atestação criptográfica dos locais de armazenamento.                                         |   3   |  D/V  |
| AC.9.18.5 | Verifique se as avaliações de segurança do provedor de nuvem incluem modelagem de ameaças específica para agentes e avaliação de riscos.                                 |   3   |  D/V  |

### AC.9.19 Controle de Acesso e Identidade

|   #   | Descrição                                                                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.3 | Verifique se os novos responsáveis passam por verificação de identidade alinhada com o padrão NIST 800-63-3 IAL-2 ou padrões equivalentes antes de receberem acesso ao sistema de produção.                      |   2   |   D   |
| 5.1.4 | Verifique se as revisões de acesso são realizadas trimestralmente com detecção automatizada de contas inativas, aplicação da rotação de credenciais e fluxos de trabalho de desprovisionamento.                  |   2   |   V   |
| 5.2.2 | Verifique se os princípios de menor privilégio são aplicados por padrão com contas de serviço começando com permissões somente de leitura e justificativa comercial documentada exigida para acesso de gravação. |   1   |  D/V  |
| 5.3.3 | Verifique se as definições de políticas são controladas por versão, revisadas por pares e validadas por meio de testes automatizados em pipelines de CI/CD antes da implantação em produção.                     |   2   |   D   |
| 5.3.4 | Verifique se os resultados da avaliação de políticas incluem fundamentações das decisões e são transmitidos para sistemas SIEM para análise de correlação e relatórios de conformidade.                          |   2   |   V   |
| 5.4.4 | Verifique se a latência da avaliação da política é monitorada continuamente com alertas automatizados para condições de tempo limite que possam possibilitar a evasão de autorização.                            |   2   |   V   |
| 5.5.4 | Verifique se os algoritmos de redação são determinísticos, controlados por versão e mantêm registros de auditoria para apoiar investigações de conformidade e análise forense.                                   |   2   |   V   |
| 5.5.5 | Verifique se os eventos de redação de alto risco geram logs adaptativos que incluem hashes criptográficos do conteúdo original para recuperação forense sem exposição de dados.                                  |   3   |   V   |
| 5.7.5 | Verifique se as condições de erro do agente e o tratamento de exceções incluem informações sobre o escopo da capacidade para apoiar a análise de incidentes e a investigação forense.                            |   3   |   V   |
| 5.4.2 | Verifique se as citações, referências e atribuições de fontes nos resultados do modelo estão validadas contra as permissões do solicitante e removidas caso seja detectado acesso não autorizado.                |   1   |  D/V  |

### Novos Itens a serem Integrados Acima

|   #   | Descrição                                                                                                                                                 | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.3 | Verifique se o conjunto de caracteres permitidos é regularmente revisado e atualizado para garantir que permaneça alinhado com os requisitos de negócios. |   2   |  D/V  |

