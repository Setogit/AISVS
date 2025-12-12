# Segurança de Memória C8, Incorporações e Banco de Dados Vetorial

## Objetivo de Controle

Incorporação e armazenamentos vetoriais atuam como a "memória ao vivo" dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelo usuário e reutilizando-os nos contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se deixada sem controle, essa memória pode expor Informações Pessoais Identificáveis (PII), violar consentimentos ou ser revertida para reconstruir o texto original. O objetivo desta família de controles é reforçar os pipelines de memória e bancos de dados vetoriais para que o acesso seja no mínimo privilégio, as incorporações preservem a privacidade, os vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine os prompts ou respostas de outro usuário.

---

## C8.1 Controles de Acesso à Memória e Índices RAG

Imponha controles de acesso granulares em cada coleção de vetores.

|   #   | Descrição                                                                                                                                                                              | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Verifique se as regras de controle de acesso a nível de linha/namespace restringem as operações de inserção, exclusão e consulta por locatário, coleção ou tag de documento.           |   1   |  D/V  |
| 8.1.2 | Verifique se as chaves de API ou JWTs possuem claims com escopo definido (por exemplo, IDs de coleção, verbos de ação) e são rotacionados pelo menos trimestralmente.                  |   1   |  D/V  |
| 8.1.3 | Verifique se as tentativas de escalonamento de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM dentro de 5 minutos.      |   2   |  D/V  |
| 8.1.4 | Verifique se o banco de dados vetorial registra nos logs o identificador do sujeito, a operação, o ID/nome do namespace do vetor, o limiar de similaridade e a contagem de resultados. |   2   |  D/V  |
| 8.1.5 | Verifique se as decisões de acesso são testadas para falhas de contorno sempre que os motores são atualizados ou as regras de fragmentação de índice mudam.                            |   3   |   V   |

---

## C8.2 Sanitização e Validação de Embeddings

Pré-analise o texto para informações pessoais identificáveis (PII), oculte ou pseudonimize antes da vetorização e, opcionalmente, pós-processe os embeddings para remover sinais residuais.

|   #   | Descrição                                                                                                                                                                                            | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Verifique se os dados PII e regulados são detectados por meio de classificadores automatizados e mascarados, tokenizados ou descartados antes da incorporação.                                       |   1   |  D/V  |
| 8.2.2 | Verifique se os pipelines de incorporação rejeitam ou colocam em quarentena entradas contendo código executável ou artefatos não UTF-8 que possam contaminar o índice.                               |   1   |   D   |
| 8.2.3 | Verifique se a sanitização de privacidade diferencial local ou métrica é aplicada a embeddings de sentença cuja distância para qualquer token PII conhecido esteja abaixo de um limiar configurável. |   2   |  D/V  |
| 8.2.4 | Verifique se a eficácia da sanitização (por exemplo, recall da redação de PII, deriva semântica) é validada pelo menos semestralmente contra corpora de referência.                                  |   2   |   V   |
| 8.2.5 | Verifique se as configurações de sanitização estão sob controle de versão e se as alterações passam por revisão por pares.                                                                           |   3   |  D/V  |

---

## C8.3 Expiração, Revogação e Exclusão de Memória

O "direito de ser esquecido" do GDPR e leis similares exigem apagamento em tempo hábil; portanto, os armazenamentos vetoriais devem suportar TTLs, exclusões definitivas e tomb-stoning para que vetores revogados não possam ser recuperados ou reindexados.

|   #   | Descrição                                                                                                                                                                            | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.3.1 | Verifique se todo vetor e registro de metadados possui um TTL ou rótulo de retenção explícito respeitado por trabalhos automatizados de limpeza.                                     |   1   |  D/V  |
| 8.3.2 | Verifique se as solicitações de exclusão iniciadas pelo usuário eliminam vetores, metadados, cópias em cache e índices derivados dentro de 30 dias.                                  |   1   |  D/V  |
| 8.3.3 | Verifique se as exclusões lógicas são seguidas pela fragmentação criptográfica dos blocos de armazenamento, caso o hardware suporte, ou pela destruição da chave do cofre de chaves. |   2   |   D   |
| 8.3.4 | Verifique se os vetores expirados são excluídos dos resultados da busca pelo vizinho mais próximo em menos de 500 ms após a expiração.                                               |   3   |  D/V  |

---

## C8.4 Prevenir Inversão e Vazamento de Embeddings

Defesas recentes—sobreposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia em camada de aplicação—podem reduzir as taxas de inversão em nível de token para menos de 5%.

|   #   | Descrição                                                                                                                                                                                    | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.4.1 | Verifique se existe um modelo formal de ameaça que abranja ataques de inversão, de associação e de inferência de atributos, e se ele é revisado anualmente.                                  |   1   |   V   |
| 8.4.2 | Verifique se a criptografia na camada de aplicação ou a criptografia pesquisável protegem os vetores contra leituras diretas por administradores de infraestrutura ou funcionários da nuvem. |   2   |  D/V  |
| 8.4.3 | Verifique se os parâmetros de defesa (ε para DP, ruído σ, posto de projeção k) equilibram privacidade ≥ 99 % de proteção de token e utilidade ≤ 3 % de perda de precisão.                    |   3   |   V   |
| 8.4.4 | Verifique se as métricas de resistência à inversão fazem parte dos critérios de liberação para atualizações do modelo, com orçamentos de regressão definidos.                                |   3   |  D/V  |

---

## C8.5 Aplicação de Escopo para Memória Específica do Usuário

O vazamento entre inquilinos continua sendo um dos principais riscos de RAG: consultas de similaridade mal filtradas podem revelar documentos privados de outro cliente.

|   #   | Descrição                                                                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.5.1 | Verifique se toda consulta de recuperação é pós-filtrada pelo ID do locatário/usuário antes de ser passada para o prompt do LLM.                                         |   1   |  D/V  |
| 8.5.2 | Verifique se os nomes das coleções ou IDs com namespace são salinizados por usuário ou locatário para que os vetores não possam colidir entre diferentes escopos.        |   1   |   D   |
| 8.5.3 | Verifique se os resultados de similaridade acima de um limite de distância configurável, mas fora do escopo do chamador, são descartados e acionam alertas de segurança. |   2   |  D/V  |
| 8.5.4 | Verifique se os testes de estresse multi-inquilino simulam consultas adversariais que tentam recuperar documentos fora do escopo e demonstram zero vazamento.            |   2   |   V   |
| 8.5.5 | Verifique se as chaves de criptografia são segregadas por locatário, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.            |   3   |  D/V  |

---

## C8.6 Segurança Avançada do Sistema de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, semântica e de trabalho, com requisitos específicos de isolamento e validação.

|   #   | Descrição                                                                                                                                                                                                                                                                 | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.6.1 | Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em função, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.          |   1   |  D/V  |
| 8.6.2 | Verifique se os processos de consolidação de memória incluem validação de segurança para evitar a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação de origem e checagens de integridade antes do armazenamento.                            |   2   |  D/V  |
| 8.6.3 | Verifique se as consultas de recuperação de memória são validadas e sanitizadas para evitar a extração de informações não autorizadas por meio de análise do padrão da consulta, aplicação de controle de acesso e filtragem de resultados.                               |   2   |  D/V  |
| 8.6.4 | Verifique se os mecanismos de esquecimento de memória excluem com segurança informações sensíveis com garantias de eliminação criptográfica, utilizando exclusão de chaves, sobrescrição múltipla ou exclusão segura baseada em hardware com certificados de verificação. |   3   |  D/V  |
| 8.6.5 | Verifique se a integridade do sistema de memória é continuamente monitorada para modificações não autorizadas ou corrupção por meio de somas de verificação, registros de auditoria e alertas automatizados quando o conteúdo da memória muda fora das operações normais. |   3   |  D/V  |

---

## Referências

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

