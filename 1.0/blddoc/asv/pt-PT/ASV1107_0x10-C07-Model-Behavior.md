# Comportamento do Modelo C7, Controle de Saída e Garantia de Segurança

## Objetivo de Controle

As saídas do modelo devem ser estruturadas, confiáveis, seguras, explicáveis e continuamente monitoradas em produção. Fazer isso reduz alucinações, vazamentos de privacidade, conteúdo prejudicial e ações descontroladas, ao mesmo tempo que aumenta a confiança do usuário e a conformidade regulatória.

---

## C7.1 Aplicação do Formato de Saída

Esquemas rigorosos, decodificação restrita e validação posterior impedem que conteúdo malformado ou malicioso se propague.

|   #   | Descrição                                                                                                                                                                                                          | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 7.1.1 | Verifique se os esquemas de resposta (por exemplo, JSON Schema) são fornecidos no prompt do sistema e se toda saída é automaticamente validada; saídas que não estejam em conformidade acionam reparo ou rejeição. |   1   |  D/V  |
| 7.1.2 | Verifique se a decodificação restrita (tokens de parada, regex, máximo de tokens) está ativada para evitar estouro ou canais laterais de injeção de prompt.                                                        |   1   |  D/V  |
| 7.1.3 | Verifique se os componentes downstream tratam as saídas como não confiáveis e as validam contra esquemas ou desserializadores seguros contra injeção.                                                              |   2   |  D/V  |
| 7.1.4 | Verifique se os eventos de saída inadequada são registrados, limitados por taxa e exibidos para monitoramento.                                                                                                     |   3   |   V   |

---

## C7.2 Detecção e Mitigação de Alucinações

A estimativa de incerteza e as estratégias de contingência limitam respostas fabricadas.

|   #   | Descrição                                                                                                                                                                                             | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Verifique se as log-probabilidades em nível de token, a auto-consistência do conjunto ou os detectores de alucinação ajustados atribuem uma pontuação de confiança a cada resposta.                   |   1   |  D/V  |
| 7.2.2 | Verifique se as respostas abaixo de um limiar de confiança configurável acionam fluxos de trabalho de fallback (por exemplo, geração aumentada por recuperação, modelo secundário ou revisão humana). |   1   |  D/V  |
| 7.2.3 | Verifique se os incidentes de alucinação estão marcados com metadados de causa raiz e alimentados aos pipelines de pós-morte e ajuste fino.                                                           |   2   |  D/V  |
| 7.2.4 | Verifique se os limiares e detectores são recalibrados após atualizações significativas do modelo ou da base de conhecimento.                                                                         |   3   |  D/V  |
| 7.2.5 | Verifique se as visualizações do painel acompanham as taxas de alucinação.                                                                                                                            |   3   |   V   |

---

## C7.3 Filtragem de Segurança e Privacidade de Saída

Os filtros de políticas e a cobertura da equipe vermelha protegem os usuários e dados confidenciais.

|   #   | Descrição                                                                                                                                                           | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.3.1 | Verifique se os classificadores pré e pós-geração bloqueiam conteúdo de ódio, assédio, autoagressão, extremista e sexualmente explícito alinhado à política.        |   1   |  D/V  |
| 7.3.2 | Verifique se a detecção de PII/PCI e a redação automática são executadas em todas as respostas; violações geram um incidente de privacidade.                        |   1   |  D/V  |
| 7.3.3 | Verifique se as etiquetas de confidencialidade (por exemplo, segredos comerciais) se propagam entre modalidades para evitar vazamentos em texto, imagens ou código. |   2   |   D   |
| 7.3.4 | Verifique se as tentativas de contornar o filtro ou classificações de alto risco exigem aprovação secundária ou reautenticação do usuário.                          |   3   |  D/V  |
| 7.3.5 | Verifique se os limites de filtragem refletem as jurisdições legais e o contexto da idade/papel do usuário.                                                         |   3   |  D/V  |

---

## C7.4 Limitação de Saída e Ação

Limites de taxa e barreiras de aprovação previnem abusos e autonomia excessiva.

|   #   | Descrição                                                                                                                                                                                   | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.4.1 | Verifique se as cotas por usuário e por chave de API limitam requisições, tokens e custo com recuo exponencial em erros 429.                                                                |   1   |   D   |
| 7.4.2 | Verifique se as ações privilegiadas (gravações de arquivos, execução de código, chamadas de rede) exigem aprovação baseada em políticas ou intervenção humana.                              |   1   |  D/V  |
| 7.4.3 | Verifique se as verificações de consistência cross-modal garantem que imagens, código e texto gerados para a mesma solicitação não possam ser usados para contrabandear conteúdo malicioso. |   2   |  D/V  |
| 7.4.4 | Verifique se a profundidade de delegação do agente, os limites de recursão e as listas de ferramentas permitidas estão configurados explicitamente.                                         |   2   |   D   |
| 7.4.5 | Verifique se a violação de limites gera eventos estruturados de segurança para ingestão pelo SIEM.                                                                                          |   3   |   V   |

---

## C7.5 Explicabilidade da Saída

Sinais transparentes melhoram a confiança do usuário e a depuração interna.

|   #   | Descrição                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Verifique se as pontuações de confiança voltadas para o usuário ou resumos breves de raciocínio são exibidos quando a avaliação de risco considera apropriado. |   2   |  D/V  |
| 7.5.2 | Verifique se as explicações geradas evitam revelar prompts sensíveis do sistema ou dados proprietários.                                                        |   2   |  D/V  |
| 7.5.3 | Verifique se o sistema captura log-probabilidades em nível de token ou mapas de atenção e os armazena para inspeção autorizada.                                |   3   |   D   |
| 7.5.4 | Verifique se os artefatos de explicabilidade estão sob controle de versão juntamente com os lançamentos do modelo para garantir auditabilidade.                |   3   |   V   |

---

## C7.6 Integração de Monitoramento

A observabilidade em tempo real fecha o ciclo entre desenvolvimento e produção.

|   #   | Descrição                                                                                                                                                                         | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.6.1 | Verifique se as métricas (violações de esquema, taxa de alucinação, toxicidade, vazamento de PII, latência, custo) são transmitidas para uma plataforma central de monitoramento. |   1   |   D   |
| 7.6.2 | Verifique se os limites de alerta estão definidos para cada métrica de segurança, com caminhos de escalonamento para plantão.                                                     |   1   |   V   |
| 7.6.3 | Verifique se os dashboards correlacionam anomalias de saída com modelo/versão, sinalizador de recurso e mudanças nos dados upstream.                                              |   2   |   V   |
| 7.6.4 | Verifique se os dados de monitoramento retornam para o re-treinamento, ajuste fino ou atualizações de regras dentro de um fluxo de trabalho de MLOps documentado.                 |   2   |  D/V  |
| 7.6.5 | Verifique se os pipelines de monitoramento são submetidos a testes de penetração e possuem controle de acesso para evitar o vazamento de logs sensíveis.                          |   3   |   V   |

---

## 7.7 Salvaguardas de Mídia Generativa

Garantir que os sistemas de IA não gerem conteúdo midiático ilegal, nocivo ou não autorizado, aplicando restrições de política, validação de saída e rastreabilidade.

|   #   | Descrição                                                                                                                                                                                                            | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Verifique se as instruções do sistema e do usuário proíbem explicitamente a geração de mídias deepfake ilegais, prejudiciais ou não consensuais (por exemplo, imagem, vídeo, áudio).                                 |   1   |  D/V  |
| 7.7.2 | Verifique se os prompts são filtrados para tentativas de gerar personificações, deepfakes sexualmente explícitos ou mídia que retrate indivíduos reais sem consentimento.                                            |   2   |  D/V  |
| 7.7.3 | Verifique se o sistema utiliza hashing perceptual, detecção de marca d'água ou identificação digital para impedir a reprodução não autorizada de mídia protegida por direitos autorais.                              |   2   |   V   |
| 7.7.4 | Verifique se toda a mídia gerada está assinada criptograficamente, com marca d'água ou incorporada com metadados de proveniência resistentes a adulteração para rastreabilidade subsequente.                         |   3   |  D/V  |
| 7.7.5 | Verifique se as tentativas de bypass (por exemplo, ofuscação de prompt, gírias, frases adversariais) são detectadas, registradas e limitadas em taxa; abusos repetidos são reportados aos sistemas de monitoramento. |   3   |   V   |

## Referências

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

