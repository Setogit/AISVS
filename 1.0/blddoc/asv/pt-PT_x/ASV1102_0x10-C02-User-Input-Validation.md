# Validação de Entrada do Usuário C2

## Objetivo de Controle

A validação robusta da entrada do usuário é uma defesa de primeira linha contra alguns dos ataques mais prejudiciais aos sistemas de IA. Ataques de injeção de prompt podem substituir as instruções do sistema, vazar dados sensíveis ou direcionar o modelo para um comportamento que não é permitido. A menos que filtros dedicados e outras validações estejam em vigor, pesquisas mostram que jailbreaks que exploram janelas de contexto continuarão a ser eficazes.

---

## Defesa contra Injeção de Prompt C2.1

A injeção de prompt é um dos principais riscos para sistemas de IA. As defesas contra essa tática utilizam uma combinação de filtros de padrão, classificadores de dados e aplicação da hierarquia de instruções.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.1.1 | Verifique se qualquer entrada externa ou derivada que possa direcionar o comportamento, incluindo prompts de usuário, resultados de RAG, saídas de plugins ou MCP, mensagens entre agentes, respostas de API ou webhook, arquivos de configuração ou políticas, leituras e gravações de memória, é tratada como não confiável, tornando-a inativa por meio de citação, marcação e remoção de conteúdo ativo, e é filtrada por um conjunto de regras ou serviço de detecção de injeção de prompt mantido antes da concatenação em prompts ou execução de ações. |   1   |  D/V  |
| 2.1.2 | Verifique se o sistema aplica uma hierarquia de instruções na qual as mensagens do sistema e do desenvolvedor substituem as instruções do usuário e outras entradas não confiáveis, mesmo após o processamento das instruções do usuário.                                                                                                                                                                                                                                                                                                                      |   1   |  D/V  |
| 2.1.3 | Verifique se os prompts originados de conteúdo de terceiros (páginas da web, PDFs, e-mails) são higienizados isoladamente (por exemplo, removendo diretrizes semelhantes a instruções e neutralizando conteúdo HTML, Markdown e scripts) antes de serem concatenados ao prompt principal.                                                                                                                                                                                                                                                                      |   2   |   D   |

---

## C2.2 Resistência a Exemplos Adversariais

Modelos de Processamento de Linguagem Natural (NLP) ainda são vulneráveis a perturbações sutis em nível de caractere ou palavra que os humanos frequentemente não percebem, mas que os modelos tendem a classificar incorretamente.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                             | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.2.1 | Verifique se as etapas básicas de normalização de entrada (Unicode NFC, mapeamento de homoglifos, remoção de espaços em branco, remoção de caracteres de controle e caracteres invisíveis Unicode) são executadas antes da tokenização ou incorporação e antes da análise para argumentos de ferramenta ou MCP.                                                       |   1   |   D   |
| 2.2.2 | Verifique se a detecção de anomalias estatísticas sinaliza entradas com distância de edição incomumente alta em relação às normas linguísticas ou distâncias de incorporação anormais, e se as entradas sinalizadas são bloqueadas antes da concatenação em prompts ou da execução de ações.                                                                          |   2   |  D/V  |
| 2.2.3 | Verifique se o pipeline de inferência suporta variantes de modelos reforçados por treinamento adversarial ou camadas de defesa (por exemplo, randomização, destilação defensiva, verificações de alinhamento) para pontos finais de alto risco.                                                                                                                       |   2   |   D   |
| 2.2.4 | Verifique se as entradas adversariais suspeitas estão em quarentena e registradas com cargas completas e metadados de rastreamento (fonte, ferramenta ou servidor MCP, ID do agente, sessão).                                                                                                                                                                         |   2   |   V   |
| 2.2.5 | Verifique se o contrabando de codificação e representação tanto nas entradas quanto nas saídas (por exemplo, caracteres Unicode/invisíveis de controle, trocas de homoglifos ou texto de direção mista) é detectado e mitigado. As mitigações aprovadas incluem canonicalização, validação rigorosa de esquemas, rejeição baseada em políticas ou marcação explícita. |   2   |  D/V  |

---

## C2.3 Conjunto de Caracteres do Prompt

Restringir o conjunto de caracteres das entradas do usuário para permitir apenas os caracteres necessários para os requisitos comerciais pode ajudar a prevenir vários tipos de ataques.

|   #   | Descrição                                                                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.1 | Verifique se o sistema implementa uma limitação no conjunto de caracteres para entradas do usuário, permitindo apenas os caracteres que são explicitamente necessários para fins comerciais.  |   1   |   D   |
| 2.3.2 | Verifique se é usada uma abordagem de lista de permissão para definir o conjunto de caracteres permitidos.                                                                                    |   1   |   D   |
| 2.3.3 | Verifique se as entradas contendo caracteres fora do conjunto permitido são rejeitadas e registradas com metadados de rastreamento (fonte, ferramenta ou servidor MCP, ID do agente, sessão). |   1   |  D/V  |

---

## C2.4 Validação de Esquema, Tipo e Comprimento

Ataques de IA envolvendo entradas malformadas ou superdimensionadas podem causar erros de análise, vazamento de prompt entre campos e exaustão de recursos. A aplicação rigorosa de esquemas também é um pré-requisito ao realizar chamadas de ferramentas determinísticas.

|   #   | Descrição                                                                                                                                                                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.4.1 | Verifique se toda API, ferramenta ou endpoint MCP define um esquema de entrada explícito (JSON Schema, Protobuf ou equivalente multimodal), rejeita campos extras ou desconhecidos e coerção implícita de tipos, e valida as entradas no lado do servidor antes da montagem do prompt ou execução da ferramenta. |   1   |   D   |
| 2.4.2 | Verifique se as entradas que excedem os limites máximos de tokens ou bytes são rejeitadas com um erro seguro e nunca truncadas silenciosamente.                                                                                                                                                                  |   1   |  D/V  |
| 2.4.3 | Verifique se as verificações de tipo (por exemplo, intervalos numéricos, valores de enumeração, tipos MIME para imagens/áudio) são aplicadas do lado do servidor, inclusive para argumentos de ferramentas ou MCP.                                                                                               |   2   |  D/V  |
| 2.4.4 | Verifique se os validadores semânticos, que compreendem a entrada de PLN, operam em tempo constante e evitam chamadas de rede externas para prevenir DoS algorítmico.                                                                                                                                            |   2   |   D   |
| 2.4.5 | Verifique se as falhas de validação são registradas com trechos de payload redigidos e códigos de erro inequívocos, além de incluir metadados de rastreamento (origem, ferramenta ou servidor MCP, ID do agente, sessão) para auxiliar na triagem de segurança.                                                  |   3   |   V   |

---

## C2.5 Triagem de Conteúdo e Políticas

Os desenvolvedores devem ser capazes de detectar prompts sintaticamente válidos que solicitem conteúdo proibido (como instruções ilícitas, discurso de ódio e/ou texto protegido por direitos autorais) e, em seguida, impedir sua propagação.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                  | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.5.1 | Verifique se um classificador de conteúdo (zero shot ou ajustado) avalia todas as entradas e saídas para violência, automutilação, ódio, conteúdo sexual e solicitações ilegais, com limites configuráveis.                                                                                                                |   1   |   D   |
| 2.5.2 | Verifique se as entradas que violam as políticas serão rejeitadas para que não se propaguem para chamadas posteriores de LLM ou ferramentas/MCP.                                                                                                                                                                           |   1   |  D/V  |
| 2.5.3 | Verifique se a triagem respeita as políticas específicas do usuário (idade, restrições legais regionais) por meio de regras baseadas em atributos resolvidas no momento da solicitação, incluindo atributos de função do agente.                                                                                           |   2   |   D   |
| 2.5.4 | Verifique se os registros de triagem incluem pontuações de confiança do classificador e tags de categoria de política com estágio aplicado (pré-prompt ou pós-resposta) e metadados de rastreamento (fonte, ferramenta ou servidor MCP, ID do agente, sessão) para correlação SOC e reprodução futura por equipe vermelha. |   3   |   V   |

---

## C2.6 Limitação da Taxa de Entrada e Prevenção de Abuso

Os desenvolvedores devem prevenir abusos, exaustão de recursos e ataques automatizados contra sistemas de IA, limitando as taxas de entrada e detectando padrões de uso anômalos.

|   #   | Descrição                                                                                                                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.6.1 | Verifique se os limites de taxa por usuário, por IP, por chave de API, por agente e por sessão/tarefa são aplicados para todos os pontos finais de entrada e ferramentas/MCP.                                                                                    |   1   |  D/V  |
| 2.6.2 | Verifique se os limites de taxa de estouro e sustentação estão ajustados para prevenir ataques DoS e força bruta, e se os orçamentos por tarefa (por exemplo, tokens, chamadas de ferramenta/MCP e custo) são aplicados para os loops de planejamento do agente. |   2   |  D/V  |
| 2.6.3 | Verifique se padrões de uso anômalos (por exemplo, solicitações em rápida sucessão, inundação de entradas, chamadas repetitivas de ferramenta/MCP com falha ou loops recursivos de agentes) acionam bloqueios automáticos ou escalonamentos.                     |   2   |  D/V  |
| 2.6.4 | Verifique se os logs de prevenção de abusos são retidos e revisados em busca de padrões de ataque emergentes, com metadados de rastreamento (origem, ferramenta ou servidor MCP, ID do agente, sessão).                                                          |   3   |   V   |

---

## C2.7 Validação de Entrada Multi-Modal

Sistemas de IA devem incluir validação robusta para entradas não textuais (imagens, áudio, arquivos) para prevenir injeção, evasão ou abuso de recursos.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                          | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.7.1 | Verifique se todas as entradas que não são de texto (imagens, áudio, arquivos) são validadas quanto ao tipo, tamanho e formato antes do processamento, e que qualquer texto extraído (imagem para texto ou fala para texto) e quaisquer instruções ocultas ou incorporadas (metadados, camadas, texto alternativo, comentários) sejam tratados como não confiáveis conforme 2.1.1. |   1   |   D   |
| 2.7.2 | Verifique se os arquivos são examinados para malware e cargas úteis esteganográficas antes da ingestão, e se qualquer conteúdo ativo (como scripts ou macros) é removido ou o arquivo é colocado em quarentena.                                                                                                                                                                    |   2   |  D/V  |
| 2.7.3 | Verifique se as entradas de imagem/áudio são checadas quanto a perturbações adversariais ou padrões de ataque conhecidos, e se as detecções acionam um mecanismo de bloqueio (bloquear ou degradar capacidades) antes do uso do modelo.                                                                                                                                            |   2   |  D/V  |
| 2.7.4 | Verifique se as falhas de validação de entrada multimodal são registradas e acionam alertas para investigação, com metadados de rastreamento (origem, ferramenta ou servidor MCP, ID do agente, sessão).                                                                                                                                                                           |   3   |   V   |
| 2.7.5 | Verifique se a detecção de ataques cross-modal identifica ataques coordenados que abrangem múltiplos tipos de entrada (por exemplo, cargas ocultas esteganográficas em imagens combinadas com injeção de comandos em texto) por meio de regras de correlação e geração de alertas, e se as detecções confirmadas são bloqueadas ou requerem aprovação HITL (humano no loop).       |   2   |  D/V  |
| 2.7.6 | Verifique se as falhas de validação multimodal acionam o registro detalhado, incluindo todas as modalidades de entrada, resultados da validação e pontuações de ameaça, além dos metadados de rastreamento (fonte, ferramenta ou servidor MCP, ID do agente, sessão).                                                                                                              |   3   |  D/V  |
---

## C2.8 Detecção Adaptativa de Ameaças em Tempo Real

Os desenvolvedores devem empregar sistemas avançados de detecção de ameaças para IA que se adaptem a novos padrões de ataque e ofereçam proteção em tempo real com correspondência de padrões compilados.

|   #   | Descrição                                                                                                                                                                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.8.1 | Verifique se a correspondência de padrões (por exemplo, regex compilado) é executada em todas as entradas e saídas (incluindo superfícies de ferramentas/MCP) com impacto mínimo na latência.                                                                                                 |   1   |  D/V  |
| 2.8.3 | Verifique se os modelos de detecção adaptativa ajustam a sensibilidade com base na atividade recente de ataques e são atualizados com novos padrões em tempo real, ativando respostas adaptativas ao risco (por exemplo, desabilitar ferramentas, reduzir contexto ou exigir aprovação HITL). |   2   |  D/V  |
| 2.8.4 | Verifique se a precisão da detecção é aprimorada por meio da análise contextual do histórico do usuário, fonte e comportamento da sessão, incluindo metadados de rastreamento (fonte, ferramenta ou servidor MCP, ID do agente, sessão).                                                      |   3   |  D/V  |
| 2.8.5 | Verifique se as métricas de desempenho de detecção (taxa de detecção, taxa de falsos positivos, latência de processamento) são continuamente monitoradas e otimizadas, incluindo o tempo até o bloqueio e o estágio (pré-prompt/pós-resposta).                                                |   3   |  D/V  |

## Referências

* [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [LLM Prompt Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)
* [MITRE ATLAS : Adversarial Input Detection](https://atlas.mitre.org/mitigations/AML.M00150)
* [Mitigate jailbreaks and prompt injections](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)

