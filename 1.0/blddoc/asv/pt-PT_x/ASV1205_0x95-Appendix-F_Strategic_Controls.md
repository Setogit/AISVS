# Apêndice B: Controles Estratégicos

## C4.15 Segurança de Infraestrutura Resistente a Quantum

Prepare a infraestrutura de IA para ameaças da computação quântica por meio de criptografia pós-quântica e protocolos seguros contra computação quântica.

|   #    | Descrição                                                                                                                                                                                               | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pelo NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais.  |   3   |  D/V  |
| 4.15.2 | Verifique se os sistemas de distribuição quântica de chaves (QKD) estão implementados para comunicações de IA de alta segurança com protocolos de gerenciamento de chaves à prova de ataques quânticos. |   3   |  D/V  |
| 4.15.3 | Verifique se as estruturas de agilidade criptográfica permitem migração rápida para novos algoritmos pós-quânticos com rotação automatizada de certificados e chaves.                                   |   3   |  D/V  |
| 4.15.4 | Verifique se a modelagem de ameaças quânticas avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos, com cronogramas de migração documentados e avaliações de risco.                     |   3   |   V   |
| 4.15.5 | Verifique se os sistemas criptográficos híbridos clássico-quânticos oferecem defesa em profundidade durante o período de transição quântica com monitoramento de desempenho.                            |   3   |  D/V  |

---

## C4.17 Infraestrutura de Conhecimento Zero

Implemente sistemas de prova de conhecimento zero para verificação e autenticação de IA preservando a privacidade, sem revelar informações sensíveis.

|   #    | Descrição                                                                                                                                                                                      | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.17.1 | Verifique se as provas de conhecimento zero (ZK-SNARKs) validam a integridade do modelo de IA e a origem do treinamento sem expor os pesos do modelo ou os dados de treinamento.               |   3   |  D/V  |
| 4.17.2 | Verifique se os sistemas de autenticação baseados em ZK possibilitam a verificação do usuário preservando a privacidade para serviços de IA sem revelar informações relacionadas à identidade. |   3   |  D/V  |
| 4.17.3 | Verifique se os protocolos de interseção privada de conjuntos (PSI) permitem a correspondência segura de dados para IA federada sem expor conjuntos de dados individuais.                      |   3   |  D/V  |
| 4.17.4 | Verifique se os sistemas de aprendizado de máquina de conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica de cálculo correto.                             |   3   |  D/V  |
| 4.17.5 | Verifique se os ZK-rollups fornecem processamento de transações de IA escalável e que preserva a privacidade, com verificação em lote e redução da sobrecarga computacional.                   |   3   |  D/V  |

---

## C4.18 Prevenção de Ataques de Canal Lateral

Proteja a infraestrutura de IA contra ataques de canal lateral baseados em tempo, energia, eletromagnéticos e cache que possam vazar informações sensíveis.

|   #    | Descrição                                                                                                                                                                  | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Verifique se o tempo de inferência de IA é normalizado usando algoritmos de tempo constante e preenchimento para prevenir ataques de extração de modelo baseados em tempo. |   3   |  D/V  |
| 4.18.2 | Verifique se a proteção contra análise de potência inclui injeção de ruído, filtragem da linha de alimentação e padrões de execução randomizados para hardware de IA.      |   3   |  D/V  |
| 4.18.3 | Verifique se a mitigação de canal lateral baseada em cache usa particionamento de cache, randomização e instruções de limpeza para evitar vazamento de informações.        |   3   |  D/V  |
| 4.18.4 | Verifique se a proteção contra emissões eletromagnéticas inclui blindagem, filtragem de sinais e processamento randomizado para prevenir ataques do tipo TEMPEST.          |   3   |  D/V  |
| 4.18.5 | Verifique se as defesas contra canais laterais microarquiteturais incluem controles de execução especulativa e ofuscação do padrão de acesso à memória.                    |   3   |  D/V  |

---

## C4.19 Segurança de Hardware Neuromórfico e de IA Especializada

Garantir a segurança das arquiteturas emergentes de hardware de IA, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

|   #    | Descrição                                                                                                                                                                                     | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.19.1 | Verifique se a segurança do chip neuromórfico inclui criptografia de padrão de spikes, proteção do peso sináptico e validação da regra de aprendizado baseada em hardware.                    |   3   |  D/V  |
| 4.19.2 | Verifique se os aceleradores de IA baseados em FPGA implementam criptografia de bitstream, mecanismos anti-sabotagem e carregamento seguro de configuração com atualizações autenticadas.     |   3   |  D/V  |
| 4.19.3 | Verifique se a segurança do ASIC personalizado inclui processadores de segurança integrados no chip, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de violação. |   3   |  D/V  |
| 4.19.4 | Verifique se os sistemas de computação óptica implementam criptografia óptica à prova de ataques quânticos, comutação fotônica segura e processamento de sinais ópticos protegido.            |   3   |  D/V  |
| 4.19.5 | Verifique se os chips de IA híbridos analógico-digitais incluem computação analógica segura, armazenamento protegido de pesos e conversão analógico-digital autenticada.                      |   3   |  D/V  |

---

## C4.20 Infraestrutura de Computação que Preserva a Privacidade

Implemente controles de infraestrutura para computação que preserva a privacidade, a fim de proteger dados sensíveis durante o processamento e análise de IA.

|   #    | Descrição                                                                                                                                                                                                    | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.20.1 | Verifique se a infraestrutura de criptografia homomórfica permite computação criptografada em cargas de trabalho sensíveis de IA com verificação de integridade criptográfica e monitoramento de desempenho. |   3   |  D/V  |
| 4.20.2 | Verifique se os sistemas de recuperação de informações privadas permitem consultas ao banco de dados sem revelar padrões de consulta, com proteção criptográfica dos padrões de acesso.                      |   3   |  D/V  |
| 4.20.3 | Verifique se os protocolos de computação multipartidária segura permitem inferência de IA preservando a privacidade, sem expor entradas individuais ou cálculos intermediários.                              |   3   |  D/V  |
| 4.20.4 | Verifique se o gerenciamento de chaves que preserva a privacidade inclui geração distribuída de chaves, criptografia de limiar e rotação segura de chaves com proteção suportada por hardware.               |   3   |  D/V  |
| 4.20.5 | Verifique se o desempenho da computação preservadora de privacidade está otimizado por meio de agrupamento, cache e aceleração de hardware, mantendo as garantias de segurança criptográfica.                |   3   |  D/V  |

| 4.9.1 | Verificar se todos os ambientes em nuvem estão integrados a sistemas centralizados de identidade para garantir uma autenticação consistente. | 1 | D/V |
| 4.9.2 | Verificar se as implantações multi-nuvem utilizam padrões de identidade federada (por exemplo, OIDC, SAML) com aplicação centralizada de políticas entre os provedores. | 2 | D/V |
| 4.9.3 | Verificar se as transferências de dados entre nuvens e híbridas utilizam criptografia de ponta a ponta com chaves gerenciadas pelo cliente e aplicam os requisitos de residência de dados jurisdicionais. | 2 | D/V |
| 4.9.1 | Verifique se a integração de armazenamento em nuvem utiliza criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente. | 1 | D/V |
| 4.9.2 | Verificar se os limites de segurança do deployment híbrido estão claramente definidos com canais de comunicação criptografados. | 2 | D/V |

