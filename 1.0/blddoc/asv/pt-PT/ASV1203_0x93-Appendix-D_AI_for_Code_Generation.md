# Apêndice D: Governança e Verificação de Codificação Segura Assistida por IA

## Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistida por IA durante o desenvolvimento de software, garantindo segurança e rastreabilidade ao longo do SDLC.

---

## AD.1 Fluxo de Trabalho de Codificação Segura Assistida por IA

Integrar ferramentas de IA no ciclo de vida de desenvolvimento seguro de software (SSDLC) da organização sem enfraquecer as barreiras de segurança existentes.

|   #    | Descrição                                                                                                                                                                                                | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.1.1 | Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.                                                                      |   1   |  D/V  |
| AD.1.2 | Verifique se o fluxo de trabalho corresponde a cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).                                                                       |   2   |   D   |
| AD.1.3 | Verifique se as métricas (por exemplo, densidade de vulnerabilidade, tempo médio para detectar) são coletadas no código produzido por IA e comparadas com as bases de referência exclusivamente humanas. |   3   |  D/V  |

---

## AD.2 Qualificação de Ferramentas de IA e Modelagem de Ameaças

Assegure que as ferramentas de codificação de IA sejam avaliadas quanto às capacidades de segurança, riscos e impacto na cadeia de suprimentos antes da adoção.

|   #    | Descrição                                                                                                                                                                              | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Verifique se um modelo de ameaça para cada ferramenta de IA identifica riscos de uso indevido, inversão de modelo, vazamento de dados e cadeia de dependência.                         |   1   |  D/V  |
| AD.2.2 | Verifique se as avaliações das ferramentas incluem análise estática/dinâmica de quaisquer componentes locais e avaliação dos endpoints SaaS (TLS, autenticação/autorização, registro). |   2   |   D   |
| AD.2.3 | Verifique se as avaliações seguem um framework reconhecido e são refeitas após mudanças significativas de versão.                                                                      |   3   |  D/V  |

---

## AD.3 Gerenciamento Seguro de Prompt e Contexto

Evite o vazamento de segredos, código proprietário e dados pessoais ao construir prompts ou contextos para modelos de IA.

|   #    | Descrição                                                                                                                                                                                            | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Verifique se as orientações escritas proíbem o envio de segredos, credenciais ou dados classificados em prompts.                                                                                     |   1   |  D/V  |
| AD.3.2 | Verifique se os controles técnicos (redação no lado do cliente, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.                                                          |   2   |   D   |
| AD.3.3 | Verifique se os prompts e respostas são tokenizados, criptografados durante a transmissão e em repouso, e se os períodos de retenção estão em conformidade com a política de classificação de dados. |   3   |  D/V  |

---

## AD.4 Validação de Código Gerado por IA

Detectar e corrigir vulnerabilidades introduzidas pela saída de IA antes que o código seja mesclado ou implantado.

|   #    | Descrição                                                                                                                                                                                           | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Verifique se o código gerado por IA é sempre submetido à revisão humana de código.                                                                                                                  |   1   |  D/V  |
| AD.4.2 | Verifique se scanners automatizados (SAST/IAST/DAST) são executados em cada pull request contendo código gerado por IA e bloqueie merges em casos de descobertas críticas.                          |   2   |   D   |
| AD.4.3 | Verifique se os testes diferenciais de fuzzing ou os testes baseados em propriedades comprovam comportamentos críticos para a segurança (por exemplo, validação de entrada, lógica de autorização). |   3   |  D/V  |

---

## AD.5 Explicabilidade e Rastreabilidade das Sugestões de Código

Fornecer a auditores e desenvolvedores uma compreensão sobre por que uma sugestão foi feita e como ela evoluiu.

|   #    | Descrição                                                                                                                                                                                             | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Verifique se os pares de prompt/resposta são registrados com IDs de commit.                                                                                                                           |   1   |  D/V  |
| AD.5.2 | Verifique se os desenvolvedores podem exibir citações do modelo (trechos de treinamento, documentação) que suportem uma sugestão.                                                                     |   2   |   D   |
| AD.5.3 | Verifique se os relatórios de explicabilidade estão armazenados com os artefatos de design e referenciados nas revisões de segurança, satisfazendo os princípios de rastreabilidade da ISO/IEC 42001. |   3   |  D/V  |

---

## AD.6 Feedback Contínuo e Ajuste Fino do Modelo

Melhorar o desempenho de segurança do modelo ao longo do tempo, evitando deriva negativa.

|   #    | Descrição                                                                                                                                                                                                     | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Verifique se os desenvolvedores podem sinalizar sugestões inseguras ou não conformes, e se as sinalizações são rastreadas.                                                                                    |   1   |  D/V  |
| AD.6.2 | Verifique se o feedback agregado informa o ajuste fino periódico ou a geração aumentada por recuperação com corpora de codificação segura verificados (por exemplo, OWASP Cheat Sheets).                      |   2   |   D   |
| AD.6.3 | Verifique se um ambiente de avaliação em loop fechado executa testes de regressão após cada ajuste fino; as métricas de segurança devem atingir ou superar as linhas de base anteriores antes da implantação. |   3   |  D/V  |

---

### Referências

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

