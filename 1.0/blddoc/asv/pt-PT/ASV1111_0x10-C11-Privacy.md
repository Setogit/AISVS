# 11 Proteção de Privacidade & Gestão de Dados Pessoais

## Objetivo de Controle

Mantenha garantias rigorosas de privacidade ao longo de todo o ciclo de vida da IA—coleta, treinamento, inferência e resposta a incidentes—para que os dados pessoais sejam processados apenas com consentimento claro, escopo mínimo necessário, exclusão comprovável e garantias formais de privacidade.

---

## 11.1 Anonimização e Minimização de Dados

|   #    | Descrição                                                                                                                                               | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.1.1 | Verifique se os identificadores diretos e quase-identificadores foram removidos ou hasheados.                                                           |   1   |  D/V  |
| 11.1.2 | Verifique se as auditorias automatizadas medem k-anonimato/l-diversidade e alertam quando os limites caem abaixo da política.                           |   2   |  D/V  |
| 11.1.3 | Verifique se os relatórios de importância de recursos do modelo comprovam que não há vazamento de identificadores além de ε = 0,01 de informação mútua. |   2   |   V   |
| 11.1.4 | Verifique se provas formais ou certificação de dados sintéticos mostram risco de reidentificação ≤ 0,05 mesmo sob ataques de vinculação.                |   3   |   V   |

---

## 11.2 Direito a ser Esquecido e Aplicação da Exclusão

|   #    | Descrição                                                                                                                                                                                                     | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.2.1 | Verifique se as solicitações de exclusão de dados pessoais se propagam para os conjuntos de dados brutos, checkpoints, embeddings, logs e backups dentro dos acordos de nível de serviço de menos de 30 dias. |   1   |  D/V  |
| 11.2.2 | Verifique se as rotinas de "desaprendizado de máquina" realmente re-treinam fisicamente ou aproximam a remoção usando algoritmos de desaprendizado certificados.                                              |   2   |   D   |
| 11.2.3 | Verifique se a avaliação do modelo sombra prova que os registros esquecidos influenciam menos de 1% dos resultados após o desaprendizado.                                                                     |   2   |   V   |
| 11.2.4 | Verificar se os eventos de exclusão são registrados de forma imutável e auditável para os reguladores.                                                                                                        |   3   |   V   |

---

## 11.3 Salvaguardas de Privacidade Diferencial

|   #    | Descrição                                                                                                                                      | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.3.1 | Verifique se os painéis de controle de contabilização da perda de privacidade alertam quando o ε cumulativo ultrapassa os limites da política. |   2   |  D/V  |
| 11.3.2 | Verifique se as auditorias de privacidade em caixa-preta estimam ε̂ dentro de 10% do valor declarado.                                          |   2   |   V   |
| 11.3.3 | Verifique se as provas formais abrangem todos os ajustes finos pós-treinamento e embeddings.                                                   |   3   |   V   |

---

## 11.4 Limitação de Propósito e Proteção contra Expansão de Escopo

|   #    | Descrição                                                                                                                                                      | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.4.1 | Verifique se cada conjunto de dados e ponto de verificação do modelo possui uma etiqueta de finalidade legível por máquina alinhada ao consentimento original. |   1   |   D   |
| 11.4.2 | Verifique se os monitores de tempo de execução detectam consultas inconsistentes com o propósito declarado e acionam uma recusa suave.                         |   1   |  D/V  |
| 11.4.3 | Verifique se os controles de política como código bloqueiam a redistribuição de modelos para novos domínios sem revisão de DPIA.                               |   3   |   D   |
| 11.4.4 | Verifique se as provas formais de rastreabilidade mostram que todo o ciclo de vida dos dados pessoais permanece dentro do escopo consentido.                   |   3   |   V   |

---

## 11.5 Gestão de Consentimento e Rastreamento com Base Legal

|   #    | Descrição                                                                                                                                                   | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.5.1 | Verifique se uma Plataforma de Gerenciamento de Consentimento (CMP) registra o status de opt-in, o propósito e o período de retenção por sujeito dos dados. |   1   |  D/V  |
| 11.5.2 | Verifique se as APIs expõem tokens de consentimento; os modelos devem validar o escopo do token antes da inferência.                                        |   2   |   D   |
| 11.5.3 | Verifique se o consentimento negado ou retirado interrompe os pipelines de processamento em até 24 horas.                                                   |   2   |  D/V  |

---

## 11.6 Aprendizado Federado com Controles de Privacidade

|   #    | Descrição                                                                                                               | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.6.1 | Verifique se as atualizações do cliente utilizam a adição de ruído de privacidade diferencial local antes da agregação. |   1   |   D   |
| 11.6.2 | Verifique se as métricas de treinamento são diferencialmente privadas e nunca revelam a perda de um único cliente.      |   2   |  D/V  |
| 11.6.3 | Verifique se a agregação resistente a envenenamento (por exemplo, Krum/Trimmed-Mean) está ativada.                      |   2   |   V   |
| 11.6.4 | Verifique se as provas formais demonstram o orçamento total de ε com menos de 5 de perda de utilidade.                  |   3   |   V   |

---

### Referências

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

