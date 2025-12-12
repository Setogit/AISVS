# Segurança de Infraestrutura, Configuração e Implantação C4

## Objetivo de Controle

A infraestrutura de IA deve ser reforçada contra escalonamento de privilégios, adulteração da cadeia de suprimentos e movimentação lateral por meio de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Apenas componentes de infraestrutura validados e autorizados chegam à produção por meio de processos controlados que garantem segurança, integridade e auditabilidade.

---

## C4.1 Isolamento do Ambiente de Execução

Prevenir fugas de contêiner e elevação de privilégios por meio de primitivas de isolamento em nível de sistema operacional.

|   #   | Descrição                                                                                                                                                                                                                                            | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.1.1 | Verifique se todas as cargas de trabalho de IA são executadas com as permissões mínimas necessárias no sistema operacional, por exemplo, removendo capacidades desnecessárias do Linux no caso de um contêiner.                                      |   1   |  D/V  |
| 4.1.2 | Verifique se as cargas de trabalho estão protegidas por tecnologias que limitam a exploração, como sandboxing, perfis seccomp, AppArmor, SELinux ou similares, e se a configuração é apropriada.                                                     |   1   |  D/V  |
| 4.1.3 | Verifique se as cargas de trabalho são executadas com um sistema de arquivos raiz somente leitura e se quaisquer pontos de montagem graváveis são explicitamente definidos e protegidos com opções restritivas (por exemplo, noexec, nosuid, nodev). |   2   |  D/V  |
| 4.1.4 | Verifique se o monitoramento em tempo de execução detecta comportamentos de escalonamento de privilégios e fuga de contêiner e termina automaticamente os processos infratores.                                                                      |   2   |  D/V  |
| 4.1.5 | Verifique se as cargas de trabalho de IA de alto risco são executadas em ambientes isolados por hardware (por exemplo, TEEs, hipervisores confiáveis ou nós bare-metal) somente após a atestação remota bem-sucedida.                                |   3   |  D/V  |

---

## C4.2 Pipelines Seguras de Construção e Implantação

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de builds reproduzíveis e artefatos assinados.

|   #   | Descrição                                                                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Verifique se as compilações são reproduzíveis e produzem metadados de procedência assinados conforme apropriado para os artefatos da compilação que podem ser verificados de forma independente.                 |   1   |  D/V  |
| 4.2.2 | Verifique se as compilações produzem uma lista de materiais de software (SBOM) e são assinadas antes de serem aceitas para implantação.                                                                          |   2   |  D/V  |
| 4.2.3 | Verifique se as assinaturas dos artefatos de build (por exemplo, imagens de container) e os metadados de proveniência são validados no momento da implantação, e que artefatos não verificados sejam rejeitados. |   2   |  D/V  |

---

## C4.3 Segurança de Rede e Controle de Acesso

Implemente redes de confiança zero com políticas de negação padrão e comunicações criptografadas.

|   #   | Descrição                                                                                                                                                                                                                                                            | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.3.1 | Verifique se as políticas de rede aplicam o bloqueio padrão para entrada e saída, permitindo explicitamente apenas os serviços necessários.                                                                                                                          |   1   |  D/V  |
| 4.3.2 | Verifique se os protocolos de acesso administrativo (por exemplo, SSH, RDP) e o acesso aos serviços de metadados em nuvem estão restritos e exigem autenticação forte.                                                                                               |   1   |  D/V  |
| 4.3.3 | Verifique se o tráfego de saída está restrito a destinos aprovados e se todas as solicitações estão registradas.                                                                                                                                                     |   2   |  D/V  |
| 4.3.4 | Verifique se a comunicação entre serviços utiliza TLS mútuo com validação de certificados e rotação automática regular.                                                                                                                                              |   2   |  D/V  |
| 4.3.5 | Verifique se as cargas de trabalho de IA e os ambientes (desenvolvimento, teste, produção) funcionam em segmentos de rede isolados (VPCs/VNets) sem acesso direto à internet e sem funções IAM compartilhadas, grupos de segurança ou conectividade entre ambientes. |   2   |  D/V  |

## C4.4 Gestão de Segredos e Chaves Criptográficas

Proteja segredos e chaves criptográficas com armazenamento seguro, rotação automatizada e controles de acesso rigorosos.

|   #   | Descrição                                                                                                                                                                                                                                                                                         | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.4.1 | Verifique se os segredos são armazenados em um sistema dedicado de gerenciamento de segredos com criptografia em repouso e isolados das cargas de trabalho da aplicação.                                                                                                                          |   1   |  D/V  |
| 4.4.2 | Verifique se as chaves criptográficas são geradas e armazenadas em módulos com suporte de hardware (por exemplo, HSMs, KMS em nuvem).                                                                                                                                                             |   1   |  D/V  |
| 4.4.3 | Verifique se o acesso a segredos de produção exige autenticação forte.                                                                                                                                                                                                                            |   1   |  D/V  |
| 4.4.4 | Verifique se os segredos são implantados nas aplicações em tempo de execução por meio de um sistema dedicado de gerenciamento de segredos. Os segredos nunca devem ser incorporados no código-fonte, arquivos de configuração, artefatos de build, imagens de contêiner ou variáveis de ambiente. |   1   |  D/V  |
| 4.4.5 | Verifique se a rotação de segredos está automatizada.                                                                                                                                                                                                                                             |   2   |  D/V  |

---

## C4.5 Sandboxing e Validação de Carga de Trabalho de IA

Isole modelos de IA não confiáveis em sandboxes seguros e proteja cargas de trabalho sensíveis de IA usando ambientes de execução confiáveis (TEEs) e tecnologias de computação confidencial.

|   #   | Descrição                                                                                                                                                                                                           | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.5.1 | Verifique se os modelos de IA externos ou não confiáveis são executados em sandboxes isolados.                                                                                                                      |   1   |  D/V  |
| 4.5.2 | Verifique se as cargas de trabalho isoladas não possuem conectividade de rede de saída por padrão, com qualquer acesso necessário explicitamente definido.                                                          |   1   |  D/V  |
| 4.5.3 | Verifique se a atestação da carga de trabalho é realizada antes do carregamento do modelo ou da carga de trabalho, garantindo a prova criptográfica de um ambiente de execução confiável.                           |   2   |  D/V  |
| 4.5.4 | Verifique se as cargas de trabalho confidenciais são executadas dentro de um ambiente de execução confiável (TEE) que oferece isolamento reforçado por hardware, criptografia de memória e proteção de integridade. |   3   |  D/V  |
| 4.5.5 | Verifique se os serviços de inferência confidenciais impedem a extração do modelo por meio de computação criptografada com pesos do modelo selados e execução protegida.                                            |   3   |  D/V  |
| 4.5.6 | Verifique se a orquestração dos ambientes de execução confiáveis inclui gerenciamento do ciclo de vida, atestação remota e canais de comunicação criptografados.                                                    |   3   |  D/V  |
| 4.5.7 | Verifique se a computação segura multipartidária (SMPC) permite o treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.                                                  |   3   |  D/V  |

---

## C4.6 Gerenciamento de Recursos de Infraestrutura de IA, Backup e Recuperação

Prevenir ataques de exaustão de recursos e garantir a alocação justa de recursos por meio de cotas e monitoramento. Manter a resiliência da infraestrutura por meio de backups seguros, procedimentos de recuperação testados e capacidades de recuperação de desastres.

|   #   | Descrição                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.6.1 | Verifique se o consumo de recursos da carga de trabalho está limitado adequadamente com, por exemplo, Kubernetes ResourceQuotas ou similar para mitigar ataques de Negação de Serviço.                                                         |   2   |  D/V  |
| 4.6.2 | Verifique se o esgotamento de recursos aciona proteções automatizadas (por exemplo, limitação de taxa ou isolamento de carga de trabalho) assim que os limites definidos de CPU, memória ou solicitações são excedidos.                        |   2   |  D/V  |
| 4.6.3 | Verifique se os sistemas de backup funcionam em redes isoladas com credenciais separadas, e se o sistema de armazenamento opera em uma rede air-gapped ou implementa proteção WORM (write-once-read-many) contra modificações não autorizadas. |   2   |  D/V  |

---

## C4.7 Segurança de Hardware em IA

Proteja componentes de hardware específicos para IA, incluindo GPUs, TPUs e aceleradores de IA especializados.

|   #   | Descrição                                                                                                                                                                                                   | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.7.1 | Verifique que, antes da execução da carga de trabalho, a integridade do acelerador de IA seja validada usando mecanismos de atestação baseados em hardware (por exemplo, TPM, DRTM ou equivalente).         |   2   |  D/V  |
| 4.7.2 | Verifique se a memória do acelerador (GPU) está isolada entre as cargas de trabalho por meio de mecanismos de particionamento com sanitização da memória entre os trabalhos.                                |   2   |  D/V  |
| 4.7.3 | Verifique se os módulos de segurança de hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-3 Nível 3 ou Common Criteria EAL4+.                          |   3   |  D/V  |
| 4.7.4 | Verifique se o firmware do acelerador (GPU/TPU/NPUs) está com a versão fixada, assinado e atestado na inicialização; firmware não assinado ou de depuração é bloqueado.                                     |   2   |  D/V  |
| 4.7.5 | Verifique se a VRAM e a memória no chip são zeradas entre trabalhos/inquilinos e se as políticas de reinicialização do dispositivo impedem a remanência de dados entre inquilinos.                          |   2   |  D/V  |
| 4.7.6 | Verifique se os recursos de particionamento/isolation (por exemplo, particionamento MIG/VM) são aplicados por inquilino e impedem o acesso à memória peer-to-peer entre as partições.                       |   2   |  D/V  |
| 4.7.7 | Verifique se as interconexões do acelerador (NVLink/PCIe/InfiniBand/RDMA/NCCL) estão restritas a topologias aprovadas e pontos finais autenticados; links de texto simples entre locatários são proibidos.  |   3   |  D/V  |
| 4.7.8 | Verifique se a telemetria do acelerador (energia, temperaturas, ECC, contadores de desempenho) é exportada para SIEM/OTel e se há alertas sobre anomalias indicativas de canais laterais ou canais ocultos. |   3   |   D   |

---

## C4.8 Segurança de IA na Borda e Distribuída

Implantações seguras de IA distribuída, incluindo computação de borda, aprendizado federado e arquiteturas multi-site.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                        | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.8.1 | Verifique se os dispositivos de IA de borda autenticam-se na infraestrutura central usando TLS mútuo.                                                                                                                                                                                                                                            |   2   |  D/V  |
| 4.8.2 | Verifique se os dispositivos de borda implementam boot seguro com assinaturas verificadas e proteção contra rollback para evitar ataques de rebaixamento de firmware.                                                                                                                                                                            |   2   |  D/V  |
| 4.8.3 | Verifique se a coordenação de IA distribuída utiliza mecanismos de consenso tolerantes a falhas bizantinas com validação dos participantes e detecção de nós maliciosos.                                                                                                                                                                         |   3   |  D/V  |
| 4.8.4 | Verifique se a comunicação de edge para nuvem suporta limitação de largura de banda, compressão de dados e operação offline segura com armazenamento local criptografado.                                                                                                                                                                        |   3   |  D/V  |
| 4.8.5 | Verifique se as aplicações de inferência móvel ou edge implementam proteções anti-tampering a nível de plataforma (por exemplo, assinatura de código, boot verificado, verificações de auto-integridade em tempo de execução) que detectam e bloqueiam binários modificados, aplicativos reempacotados ou frameworks de instrumentação anexados. |   3   |  D/V  |
| 4.8.6 | Verifique se os modelos implantados em dispositivos de borda ou móveis são assinados criptograficamente durante o empacotamento, e se o tempo de execução no dispositivo valida essas assinaturas ou somas de verificação antes do carregamento ou inferência; modelos não verificados ou alterados devem ser rejeitados.                        |   3   |  D/V  |
| 4.8.7 | Verifique se os tempos de execução de inferência no dispositivo aplicam isolamento de processo, memória e acesso a arquivos para evitar o despejo do modelo, depuração ou extração de embeddings e ativações intermediárias.                                                                                                                     |   3   |  D/V  |
| 4.8.8 | Verifique se os pesos do modelo e os parâmetros sensíveis armazenados localmente estão criptografados usando armazenamentos de chaves com suporte de hardware ou enclaves seguros (por exemplo, Android Keystore, iOS Secure Enclave, TPM/TEE), com chaves inacessíveis ao espaço do usuário.                                                    |   3   |  D/V  |
| 4.8.9 | Verifique se os modelos embalados em aplicativos móveis, IoT ou incorporados estão criptografados ou ofuscados em repouso, e descriptografados apenas dentro de um ambiente de execução confiável ou enclave seguro, impedindo a extração direta do pacote do aplicativo ou do sistema de arquivos.                                              |   3   |  D/V  |

---

## Referências

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

