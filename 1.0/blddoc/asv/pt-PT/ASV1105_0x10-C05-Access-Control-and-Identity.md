# Controle de Acesso C5 e Identidade para Componentes e Usuários de IA

## Objetivo de Controle

O controle de acesso eficaz para sistemas de IA requer uma gestão de identidade robusta, autorização sensível ao contexto e aplicação em tempo de execução seguindo os princípios de confiança zero. Esses controles garantem que humanos, serviços e agentes autônomos interajam apenas com modelos, dados e recursos computacionais dentro de escopos explicitamente concedidos, com capacidades contínuas de verificação e auditoria.

---

## C5.1 Gerenciamento de Identidade e Autenticação

Estabeleça identidades suportadas criptograficamente para todas as entidades com autenticação multifatorial.

|   #   | Descrição                                                                                                                                                                                                                                         | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Verifique se todos os usuários humanos e os principais de serviço autenticam-se através de um provedor de identidade empresarial centralizado (IdP) utilizando os protocolos OIDC e/ou SAML.                                                      |   1   |  D/V  |
| 5.1.2 | Verifique se as operações de alto risco (implantação de modelo, exportação de pesos, acesso aos dados de treinamento, alterações na configuração de produção) exigem autenticação multifator ou autenticação reforçada com revalidação da sessão. |   1   |  D/V  |
| 5.1.3 | Verifique se os agentes de IA federados se autenticam por meio de declarações JWT assinadas que possuem um tempo máximo de vida útil de 24 horas e incluem prova criptográfica de origem.                                                         |   3   |  D/V  |

---

## C5.2 Autorização e Política

Implemente controles de acesso para todos os recursos de IA com modelos de permissão explícitos e trilhas de auditoria.

|   #   | Descrição                                                                                                                                                                                                                                                          | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 5.2.1 | Verifique se todos os recursos de IA (conjuntos de dados, modelos, endpoints, coleções vetoriais, índices de embedding, instâncias de computação) aplicam controles de acesso baseados em função com listas de permissão explícitas e políticas de negação padrão. |   1   |  D/V  |
| 5.2.2 | Verifique se todas as modificações no controle de acesso são registradas de forma imutável com carimbos de data e hora, identidades dos atores, identificadores dos recursos e alterações nas permissões.                                                          |   1   |   V   |
| 5.2.3 | Verifique se os rótulos de classificação de dados (PII, PHI, proprietário, etc.) são automaticamente propagados para os recursos derivados (incorporações, caches de prompt, saídas do modelo).                                                                    |   2   |   D   |
| 5.2.4 | Verifique se as tentativas de acesso não autorizadas e os eventos de escalonamento de privilégios acionam alertas em tempo real com metadados contextuais.                                                                                                         |   2   |  D/V  |
| 5.2.5 | Verifique se as decisões de autorização são externalizadas para um mecanismo de políticas dedicado (OPA, Cedar ou equivalente).                                                                                                                                    |   1   |  D/V  |
| 5.2.6 | Verifique se as políticas avaliam atributos dinâmicos em tempo de execução, incluindo função ou grupo do usuário, classificação do recurso, contexto da solicitação, isolamento de locatário e restrições temporais.                                               |   1   |  D/V  |
| 5.2.7 | Verifique se os valores de tempo de vida (TTL) do cache de políticas não excedem 5 minutos para recursos de alta sensibilidade e 1 hora para recursos padrão com capacidades de invalidação de cache.                                                              |   3   |  D/V  |

---

## C5.3 Aplicação de Segurança em Tempo de Consulta

Implemente controles de segurança na camada de banco de dados com filtragem obrigatória e políticas de segurança em nível de linha.

|   #   | Descrição                                                                                                                                                                                                                             | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Verifique se todas as consultas em banco de dados vetorial e SQL incluem filtros de segurança obrigatórios (ID do locatário, rótulos de sensibilidade, escopo do usuário) aplicados no nível do mecanismo do banco de dados.          |   1   |  D/V  |
| 5.3.2 | Verifique se as políticas de segurança em nível de linha e o mascaramento em nível de campo estão habilitados com herança de políticas para todos os bancos de dados vetoriais, índices de busca e conjuntos de dados de treinamento. |   1   |  D/V  |
| 5.3.3 | Verifique se as avaliações de autorização falhadas abortarão imediatamente as consultas e retornarão códigos de erro de autorização explícitos.                                                                                       |   2   |   D   |
| 5.3.4 | Verifique se os mecanismos de nova tentativa de consulta reavaliam as políticas de autorização para considerar mudanças dinâmicas de permissão dentro de sessões de usuário ativas.                                                   |   3   |  D/V  |

---

## C5.4 Filtragem de Saída e Prevenção de Perda de Dados

Implemente controles de pós-processamento para evitar a exposição não autorizada de dados em conteúdo gerado por IA.

|   #   | Descrição                                                                                                                                                                                                                            | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 5.4.1 | Verifique se os mecanismos de filtragem pós-inferência escaneiam e redigem informações pessoais identificáveis (PII) não autorizadas, informações classificadas e dados proprietários antes de entregar o conteúdo aos solicitantes. |   1   |  D/V  |
| 5.4.2 | Verifique se citações, referências e atribuições de fontes nas saídas do modelo são validadas de acordo com os direitos do chamador e removidas se for detectado acesso não autorizado.                                              |   1   |  D/V  |
| 5.4.3 | Verifique se as restrições de formato de saída (PDFs sanitizados, imagens com metadados removidos, tipos de arquivo aprovados) são aplicadas com base nos níveis de permissão do usuário e classificações de dados.                  |   2   |   D   |

---

## C5.5 Isolamento Multi-Inquilino

Garantir isolamento criptográfico e lógico entre os inquilinos na infraestrutura de IA compartilhada.

|   #   | Descrição                                                                                                                                                                                                                     | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.5.1 | Verifique se os espaços de memória, armazenamento de embeddings, entradas de cache e arquivos temporários estão segregados por namespace para cada locatário, com purga segura na exclusão do locatário ou término da sessão. |   1   |  D/V  |
| 5.5.2 | Verifique se cada solicitação de API inclui um identificador de inquilino autenticado que é validado criptograficamente em relação ao contexto da sessão e às autorizações do usuário.                                        |   1   |  D/V  |
| 5.5.3 | Verifique se as políticas de rede implementam regras de negação padrão para comunicação entre locatários em malhas de serviço e plataformas de orquestração de contêineres.                                                   |   2   |   D   |
| 5.5.4 | Verifique se as chaves de criptografia são exclusivas por locatário com suporte para chave gerenciada pelo cliente (CMK) e isolamento criptográfico entre os armazenamentos de dados dos locatários.                          |   3   |   D   |

---

## C5.6 Autorização de Agente Autônomo

Controle permissões para agentes de IA e sistemas autônomos por meio de tokens de capacidade com escopo e autorização contínua.

|   #   | Descrição                                                                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Verifique se os agentes autônomos recebem tokens de capacidade delimitada que enumeram explicitamente as ações permitidas, os recursos acessíveis, os limites de tempo e as restrições operacionais.           |   1   |  D/V  |
| 5.6.2 | Verifique se as capacidades de alto risco (acesso ao sistema de arquivos, execução de código, chamadas de API externas, transações financeiras) estão desativadas por padrão e requerem autorização explícita. |   1   |  D/V  |
| 5.6.3 | Verifique se os tokens de capacidade estão vinculados às sessões do usuário, incluem proteção criptográfica de integridade e garantam que não possam ser armazenados ou reutilizados em cenários offline.      |   2   |   D   |
| 5.6.4 | Verifique se as ações iniciadas pelo agente passam por autorização por meio de um mecanismo de política ABAC.                                                                                                  |   2   |   V   |

---

## Referências

* [NIST SP 800-162: Guide to Attribute Based Access Control (ABAC)](https://csrc.nist.gov/pubs/sp/800/162/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final)
* [NIST SP 800-63-3: Digital Identity Guidelines](https://csrc.nist.gov/pubs/sp/800/63/3/final)
* [NIST IR 8360: Machine Learning for Access Control Policy Verification](https://csrc.nist.gov/pubs/ir/8360/final)

