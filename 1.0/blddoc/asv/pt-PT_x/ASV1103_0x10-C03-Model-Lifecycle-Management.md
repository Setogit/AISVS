# Gerenciamento do Ciclo de Vida do Modelo C3 e Controle de Mudanças

## Objetivo de Controle

Sistemas de IA devem implementar processos de controle de mudanças que impeçam modificações não autorizadas ou inseguras no modelo de chegarem à produção. Esse controle garante a integridade do modelo durante todo o ciclo de vida—desde o desenvolvimento até a implantação e descomissionamento—o que permite uma resposta rápida a incidentes e mantém a responsabilidade por todas as mudanças.

Objetivo Principal de Segurança: Apenas modelos autorizados e validados chegam à produção por meio da utilização de processos controlados que mantêm a integridade, rastreabilidade e recuperabilidade.

---

## C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                           | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.1.1 | Verifique se todos os artefatos do modelo (pesos, configurações, tokenizadores, modelos base, ajustes finos, adaptadores como LoRA e modelos de segurança/política) estão assinados criptograficamente por entidades autorizadas e são verificados na admissão de implantação (e ao serem carregados), bloqueando qualquer artefato não assinado ou adulterado.                                                     |   1   |  D/V  |
| 3.1.2 | Verifique se o rastreamento de dependências mantém um inventário em tempo real por meio de um registro de modelos e gráfico de linhagem/dependência, e produz uma Lista de Materiais de Modelo/IA (MBOM/AIBOM) legível por máquina (por exemplo, SPDX ou CycloneDX) que possibilita a identificação de todos os serviços/agentes consumidores por ambiente (por exemplo, desenvolvimento, teste, produção, região). |   2   |   V   |
| 3.1.3 | Verifique se a integridade da origem do modelo e os registros de rastreamento incluem a identidade da entidade autorizadora, somas de verificação dos dados de treinamento, resultados dos testes de validação com status de aprovado/reprovado, impressão digital da assinatura/cadeia de certificados ID, uma marca temporal de criação e ambientes de implantação aprovados.                                     |   3   |  D/V  |

---

## C3.2 Validação e Testes do Modelo

Os modelos devem passar pelas validações definidas de segurança e proteção antes da implantação.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.2.1 | Verifique se os modelos passam por testes de segurança automatizados que incluem validação de entrada, sanitização de saída e avaliações de segurança com limites de aprovação/reprovação organizacionais pré-acordados antes da implantação, abrangendo fluxos de trabalho do agente (planejamento, chamadas de ferramenta ou MCP, RAG/memória, multimodal) e diretrizes de segurança (modelos de política/segurança ou serviços de detecção) com uma estrutura de avaliação versionada. |   1   |  D/V  |
| 3.2.2 | Verifique se todas as alterações no modelo (implantação, configuração, desativação) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, uma identidade de ator autenticada, um tipo de alteração, e os estados anterior/posterior, com metadados de rastreamento (ambiente e serviços/agentess consumidores) e um identificador do modelo (versão/digest/assinatura).                                                                                              |   1   |   V   |
| 3.2.3 | Verifique se as falhas de validação bloqueiam automaticamente a implantação do modelo, a menos que haja uma aprovação explícita de substituição por pessoal autorizado pré-designado com justificativas comerciais documentadas.                                                                                                                                                                                                                                                          |   2   |  D/V  |

---

## C3.3 Implantação Controlada & Reversão

As implantações de modelos devem ser controladas, monitoradas e reversíveis.

|   #   | Descrição                                                                                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.3.1 | Verifique se os processos de implantação validam assinaturas criptográficas e calculam somas de verificação de integridade antes da ativação ou carregamento do modelo, falhando na implantação em caso de qualquer divergência.                                                                               |   1   |  D/V  |
| 3.3.2 | Verifique se as implantações em produção implementam mecanismos de lançamento gradual (implantações canário, implantações blue-green) com gatilhos automatizados de reversão baseados em taxas de erro pré-acordadas, limites de latência, alertas de guardrail/jailbreak ou taxas de falha da ferramenta/MCP. |   1   |   D   |
| 3.3.3 | Verifique se as capacidades de rollback restauram o estado completo do modelo (pesos, configurações, dependências, incluindo adaptadores e modelos de segurança/política) de forma atômica.                                                                                                                    |   2   |  D/V  |
| 3.3.4 | Verificar se as capacidades de desligamento de emergência do modelo podem desativar pontos de extremidade do modelo e desativar ferramentas de agente ou acesso MCP, RAG/conectores e credenciais de banco de dados/API, e vínculos de armazenamento de memória dentro de um tempo de resposta predefinido.    |   3   |  D/V  |

---

## C3.4 Práticas de Desenvolvimento Seguro

Os processos de desenvolvimento e treinamento de modelos devem seguir práticas seguras para evitar comprometimentos.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.4.1 | Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão separados fisicamente ou logicamente. Eles não compartilham infraestrutura, possuem controles de acesso distintos e armazenamento de dados isolado, e a orquestração de agentes e os servidores de ferramentas ou MCP também estão isolados.                                                                                    |   1   |  D/V  |
| 3.4.2 | Verifique se os artefatos de desenvolvimento do modelo (hiperparâmetros, scripts de treinamento, arquivos de configuração, modelos de prompt, políticas de agentes/diagramas de roteamento, contratos/esquemas de ferramentas ou MCP, e catálogos de ações ou listas de permissão de capacidades) estão armazenados em controle de versão e exigem aprovação de revisão por pares antes do uso no treinamento. |   1   |   D   |
| 3.4.3 | Verifique se o treinamento e o ajuste fino do modelo ocorrem em ambientes isolados com acesso à rede controlado, utilizando listas de permissão de saída e sem acesso às ferramentas de produção ou recursos do MCP.                                                                                                                                                                                           |   2   |  D/V  |
| 3.4.4 | Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes do uso no desenvolvimento do modelo, incluindo índices RAG, registros de ferramentas e dados gerados por agentes utilizados para ajuste fino.                                                                               |   2   |   D   |

---

## Desativação e Descomissionamento do Modelo C3.5

Modelos devem ser desativados com segurança quando não forem mais necessários ou quando forem identificados problemas de segurança.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.5.1 | Verifique se os artefatos do modelo aposentado (incluindo adaptadores e modelos de segurança/política) são apagados de forma segura usando apagamento criptográfico seguro.                                                                                                                                                                                                                                                    |   1   |  D/V  |
| 3.5.2 | Verifique se os eventos de desativação do modelo são registrados com carimbo de data/hora e identidade do ator, identificador do modelo (versão/digest/assinatura) e metadados de rastreamento (ambiente e serviços/agentes consumidores); as assinaturas dos modelos são revogadas, e listas de negação do registro/serviço, além da invalidação do cache do carregador, impedem que agentes carreguem artefatos desativados. |   2   |   V   |

---

## Referências

* [MITRE ATLAS](https://atlas.mitre.org/)
* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Reinforcement fine-tuning](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)

