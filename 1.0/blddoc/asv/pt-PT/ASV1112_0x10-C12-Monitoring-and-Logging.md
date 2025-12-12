# C12 Monitoramento, Registro e Detecção de Anomalias

## Objetivo de Controle

Esta seção fornece requisitos para fornecer visibilidade em tempo real e forense sobre o que o modelo e outros componentes de IA veem, fazem e retornam, para que ameaças possam ser detectadas, triadas e aprendidas.

## C12.1 Registro de Requisições e Respostas

|   #    | Descrição                                                                                                                                                                                                                                                 | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Verifique se todas as solicitações dos usuários e respostas do modelo são registradas com os metadados apropriados (por exemplo, carimbo de data/hora, ID do usuário, ID da sessão, versão do modelo).                                                    |   1   |  D/V  |
| 12.1.2 | Verifique se os registros são armazenados em repositórios seguros, com controle de acesso, políticas de retenção adequadas e procedimentos de backup.                                                                                                     |   1   |  D/V  |
| 12.1.3 | Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger as informações sensíveis contidas nos logs.                                                                                             |   1   |  D/V  |
| 12.1.4 | Verifique se os dados sensíveis em prompts e resultados são automaticamente ocultados ou mascarados antes do registro, com regras de ocultação configuráveis para informações pessoalmente identificáveis (PII), credenciais e informações proprietárias. |   1   |  D/V  |
| 12.1.5 | Verifique se as decisões de políticas e as ações de filtragem de segurança são registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.                                                            |   2   |  D/V  |
| 12.1.6 | Verifique se a integridade dos logs está protegida por meio de, por exemplo, assinaturas criptográficas ou armazenamento somente para gravação.                                                                                                           |   2   |  D/V  |

---

## C12.2 Detecção de Abuso e Alertas

|   #    | Descrição                                                                                                                                                                                                               | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Verifique se o sistema detecta e alerta sobre padrões conhecidos de jailbreak, tentativas de injeção de prompt e entradas adversariais usando detecção baseada em assinatura.                                           |   1   |  D/V  |
| 12.2.2 | Verifique se o sistema se integra com as plataformas existentes de Gestão de Informações e Eventos de Segurança (SIEM) utilizando formatos de log e protocolos padrão.                                                  |   1   |  D/V  |
| 12.2.3 | Verifique se os eventos de segurança enriquecidos incluem contexto específico de IA, como identificadores de modelo, pontuações de confiança e decisões do filtro de segurança.                                         |   2   |  D/V  |
| 12.2.4 | Verifique se a detecção de anomalias comportamentais identifica padrões incomuns de conversa, tentativas excessivas de repetição ou comportamentos sistêmicos de sondagem.                                              |   2   |  D/V  |
| 12.2.5 | Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando potenciais violações de políticas ou tentativas de ataques são detectadas.                                                  |   2   |  D/V  |
| 12.2.6 | Verifique se regras personalizadas estão incluídas para detectar padrões de ameaças específicos de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompts e ataques de extração de modelos. |   2   |  D/V  |
| 12.2.7 | Verifique se os fluxos de trabalho automatizados de resposta a incidentes podem isolar modelos comprometidos, bloquear usuários mal-intencionados e escalar eventos críticos de segurança.                              |   3   |  D/V  |

---

## C12.3 Detecção de Deriva do Modelo

|   #    | Descrição                                                                                                                                                                              | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Verifique se o sistema monitora métricas básicas de desempenho, como precisão, pontuações de confiança, latência e taxas de erro ao longo das versões do modelo e períodos de tempo.   |   1   |  D/V  |
| 12.3.2 | Verifique se o alerta automatizado é acionado quando as métricas de desempenho excedem os limites de degradação predefinidos ou se desviam significativamente das linhas de base.      |   2   |  D/V  |
| 12.3.3 | Verifique se os monitores de detecção de alucinação identificam e sinalizam casos em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas. |   2   |  D/V  |

---

## C12.4 Telemetria de Desempenho e Comportamento

|   #    | Descrição                                                                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.4.1 | Verifique se as métricas operacionais, incluindo latência de requisição, consumo de tokens, uso de memória e taxa de transferência, são continuamente coletadas e monitoradas.                  |   1   |  D/V  |
| 12.4.2 | Verifique se as taxas de sucesso e falha são monitoradas com a categorização dos tipos de erro e suas causas raízes.                                                                            |   1   |  D/V  |
| 12.4.3 | Verifique se o monitoramento da utilização dos recursos inclui uso de GPU/CPU, consumo de memória e requisitos de armazenamento, com alerta em caso de ultrapassagem dos limites estabelecidos. |   2   |  D/V  |

---

## C12.5 Planejamento e Execução de Resposta a Incidentes de IA

|   #    | Descrição                                                                                                                                                                                            | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo comprometimento de modelos, envenenamento de dados e ataques adversariais. |   1   |  D/V  |
| 12.5.2 | Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e expertise para investigar o comportamento do modelo e os vetores de ataque.                   |   2   |  D/V  |
| 12.5.3 | Verifique se a análise pós-incidente inclui considerações sobre re-treinamento do modelo, atualizações dos filtros de segurança e integração das lições aprendidas nos controles de segurança.       |   3   |  D/V  |

---

## C12.6 Detecção de Degradação de Desempenho em IA

Monitorar e detectar a degradação no desempenho e na qualidade do modelo de IA ao longo do tempo.

|   #    | Descrição                                                                                                                                                       | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Verifique se a precisão, precisão, recall e pontuações F1 do modelo são continuamente monitoradas e comparadas com os limiares de referência.                   |   1   |  D/V  |
| 12.6.2 | Verifique se a detecção de deriva de dados monitora mudanças na distribuição de entrada que podem impactar o desempenho do modelo.                              |   1   |  D/V  |
| 12.6.3 | Verifique se a detecção de drift de conceito identifica mudanças na relação entre os inputs e os outputs esperados.                                             |   2   |  D/V  |
| 12.6.4 | Verifique se a degradação do desempenho aciona alertas automáticos e inicia fluxos de trabalho de retreinamento ou substituição do modelo.                      |   2   |  D/V  |
| 12.6.5 | Verifique se a análise da causa raiz da degradação correlaciona quedas de desempenho com alterações nos dados, problemas na infraestrutura ou fatores externos. |   3   |   V   |

---

## C12.7 Visualização de DAG e Segurança do Fluxo de Trabalho

Proteja os sistemas de visualização de fluxo de trabalho contra vazamento de informações e ataques de manipulação.

|   #    | Descrição                                                                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Verifique se os dados de visualização do DAG são higienizados para remover informações sensíveis antes do armazenamento ou transmissão.                                                         |   1   |  D/V  |
| 12.7.2 | Verifique se os controles de acesso à visualização do fluxo de trabalho garantem que apenas usuários autorizados possam visualizar os caminhos de decisão do agente e os rastros de raciocínio. |   1   |  D/V  |
| 12.7.3 | Verifique se a integridade dos dados do DAG está protegida por meio de assinaturas criptográficas e mecanismos de armazenamento à prova de adulteração.                                         |   2   |  D/V  |
| 12.7.4 | Verifique se os sistemas de visualização de fluxo de trabalho implementam validação de entrada para prevenir ataques de injeção por meio de dados elaborados em nós ou arestas.                 |   2   |  D/V  |
| 12.7.5 | Verifique se as atualizações em tempo real do DAG são limitadas por taxa e validadas para prevenir ataques de negação de serviço nos sistemas de visualização.                                  |   3   |  D/V  |

---

## C12.8 Monitoramento Proativo de Comportamento de Segurança

Detecção e prevenção de ameaças de segurança por meio da análise proativa do comportamento do agente.

|   #    | Descrição                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.8.1 | Verifique se os comportamentos proativos dos agentes são validados quanto à segurança antes da execução, com integração de avaliação de riscos. |   1   |  D/V  |
| 12.8.2 | Verifique se os gatilhos da iniciativa autônoma incluem avaliação do contexto de segurança e análise do cenário de ameaças.                     |   2   |  D/V  |
| 12.8.3 | Verifique se os padrões de comportamento proativo são analisados quanto a potenciais implicações de segurança e consequências não intencionais. |   2   |  D/V  |
| 12.8.4 | Verifique se as ações pró-ativas críticas para a segurança requerem cadeias de aprovação explícitas com trilhas de auditoria.                   |   3   |  D/V  |
| 12.8.5 | Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões de agentes proativos que podem indicar comprometimento.     |   3   |  D/V  |

---

## Referências

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)

