# Segurança da Cadeia de Suprimentos C6 para Modelos, Frameworks e Dados

## Objetivo de Controle

Os ataques à cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para inserir backdoors, viés ou código explorável. Esses controles fornecem rastreabilidade de ponta a ponta, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

## C6.1 Avaliação de Modelos Pré-treinados e Integridade da Origem

Avalie e autentique as origens, licenças e comportamentos ocultos dos modelos de terceiros antes de qualquer ajuste fino ou implantação.

|   #   | Descrição                                                                                                                                                   | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.1.1 | Verifique se todo artefato de modelo de terceiros inclui um registro de origem assinado identificando o repositório de origem e o hash do commit.           |   1   |  D/V  |
| 6.1.2 | Verifique se os modelos são verificados quanto a camadas maliciosas ou gatilhos de Trojan usando ferramentas automatizadas antes da importação.             |   1   |  D/V  |
| 6.1.3 | Verifique se o fine-tuning por transferência de aprendizado passa na avaliação adversarial para detectar comportamentos ocultos.                            |   2   |   D   |
| 6.1.4 | Verifique se as licenças do modelo, as etiquetas de controle de exportação e as declarações de origem dos dados estão registradas em uma entrada ML-BOM.    |   2   |   V   |
| 6.1.5 | Verifique se os modelos de alto risco (pesos carregados publicamente, criadores não verificados) permanecem em quarentena até a revisão e aprovação humana. |   3   |  D/V  |

---

## C6.2 Escaneamento de Frameworks e Bibliotecas

Escaneie continuamente frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de execução segura.

|   #   | Descrição                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.2.1 | Verifique se os pipelines de CI executam scanners de dependências em frameworks de IA e bibliotecas críticas.                                      |   1   |  D/V  |
| 6.2.2 | Verifique se vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção para imagens de produção.                                                 |   1   |  D/V  |
| 6.2.3 | Verifique se a análise estática de código é executada em bibliotecas de ML bifurcadas ou fornecidas.                                               |   2   |   D   |
| 6.2.4 | Verifique se as propostas de atualização do framework incluem uma avaliação de impacto de segurança que faça referência aos feeds públicos de CVE. |   2   |   V   |
| 6.2.5 | Verifique se os sensores em tempo de execução alertam sobre cargas inesperadas de bibliotecas dinâmicas que desviam do SBOM assinado.              |   3   |   V   |

---

## C6.3 Fixação e Verificação de Dependências

Ancore todas as dependências em digests imutáveis e reproduza builds para garantir artefatos idênticos e à prova de adulteração.

|   #   | Descrição                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 6.3.1 | Verifique se todos os gerenciadores de pacotes aplicam a fixação de versões por meio de arquivos de bloqueio.            |   1   |  D/V  |
| 6.3.2 | Verifique se são usados resumos imutáveis em vez de tags mutáveis nas referências de contêineres.                        |   1   |  D/V  |
| 6.3.3 | Verifique se as verificações de build reproduzível comparam hashes entre execuções de CI para garantir saídas idênticas. |   2   |   D   |
| 6.3.4 | Verifique se as atestações de build são armazenadas por 18 meses para rastreabilidade de auditoria.                      |   2   |   V   |
| 6.3.5 | Verifique se as dependências expiradas acionam PRs automáticos para atualizar ou bifurcar versões fixadas.               |   3   |   D   |

---

## C6.4 Aplicação de Fonte Confiável

Permitir downloads de artefatos somente de fontes verificadas criptograficamente e aprovadas pela organização, e bloquear todo o resto.

|   #   | Descrição                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.4.1 | Verifique se os pesos do modelo, os conjuntos de dados e os contêineres são baixados apenas de domínios aprovados ou registros internos.      |   1   |  D/V  |
| 6.4.2 | Verifique se as assinaturas Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados em cache localmente.  |   1   |  D/V  |
| 6.4.3 | Verifique se os proxies de saída bloqueiam downloads de artefatos não autenticados para impor a política de fonte confiável.                  |   2   |   D   |
| 6.4.4 | Verifique se as listas de permissão do repositório são revisadas trimestralmente com evidências de justificativa comercial para cada entrada. |   2   |   V   |
| 6.4.5 | Verifique se as violações de política acionam o isolamento dos artefatos e o rollback das execuções de pipeline dependentes.                  |   3   |   V   |

---

## C6.5 Avaliação de Risco de Conjunto de Dados de Terceiros

Avalie conjuntos de dados externos quanto a envenenamento, viés e conformidade legal, e monitore-os ao longo de seu ciclo de vida.

|   #   | Descrição                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.5.1 | Verifique se os conjuntos de dados externos passam por uma avaliação de risco de envenenamento (por exemplo, impressão digital de dados, detecção de valores atípicos). |   1   |  D/V  |
| 6.5.2 | Verifique se as métricas de viés (paridade demográfica, igualdade de oportunidade) são calculadas antes da aprovação do conjunto de dados.                              |   1   |   D   |
| 6.5.3 | Verifique se a origem, a linhagem e os termos de licença dos conjuntos de dados estão capturados nas entradas do ML-BOM.                                                |   2   |   V   |
| 6.5.4 | Verifique se o monitoramento periódico detecta deriva ou corrupção em conjuntos de dados hospedados.                                                                    |   2   |   V   |
| 6.5.5 | Verifique se o conteúdo não permitido (direitos autorais, informações pessoais identificáveis) é removido por meio de limpeza automatizada antes do treinamento.        |   3   |   D   |

---

## C6.6 Monitoramento de Ataques à Cadeia de Suprimentos

Detecte ameaças à cadeia de suprimentos cedo por meio de feeds CVE, análises de registros de auditoria e simulações de red team.

|   #   | Descrição                                                                                                                                                                          | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.6.1 | Verifique se os logs de auditoria de CI/CD são transmitidos para o SIEM para detecção de puxões de pacotes anômalos ou etapas de construção adulteradas.                           |   1   |   V   |
| 6.6.2 | Verifique se os playbooks de resposta a incidentes incluem procedimentos de reversão para modelos ou bibliotecas comprometidos.                                                    |   2   |   D   |
| 6.6.3 | Verifique se as tags de enriquecimento de inteligência sobre ameaças etiquetam indicadores específicos de ML (por exemplo, IoCs de envenenamento de modelo) na triagem de alertas. |   3   |   V   |

---

## C6.7 ML‑BOM para Artefatos de Modelo

Gerar e assinar SBOMs detalhados específicos para ML (ML-BOMs) para que os consumidores a jusante possam verificar a integridade dos componentes no momento da implantação.

|   #   | Descrição                                                                                                                                 | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.7.1 | Verifique se cada artefato de modelo publica um ML‑BOM que lista conjuntos de dados, pesos, hiperparâmetros e licenças.                   |   1   |  D/V  |
| 6.7.2 | Verifique se a geração do ML-BOM e a assinatura Cosign estão automatizadas no CI e são obrigatórias para a mesclagem.                     |   1   |  D/V  |
| 6.7.3 | Verifique se as verificações de completude do ML‑BOM falham a compilação se algum metadado do componente (hash, licença) estiver ausente. |   2   |   D   |
| 6.7.4 | Verifique se os consumidores a jusante podem consultar ML-BOMs via API para validar os modelos importados no momento da implantação.      |   2   |   V   |
| 6.7.5 | Verifique se os ML‑BOMs estão sob controle de versão e se são comparados para detectar modificações não autorizadas.                      |   3   |   V   |

---

## Referências

* [OWASP LLM03:2025 Supply Chain](https://genai.owasp.org/llmrisk/llm032025-supply-chain/)
* [MITRE ATLAS : Supply Chain Compromise](https://atlas.mitre.org/techniques/AML.T0010)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)

