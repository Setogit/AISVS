# Apêndice A: Glossário

Este glossário abrangente fornece definições dos principais termos de IA, ML e segurança usados ao longo do AISVS para garantir clareza e entendimento comum.

* Exemplo Adversarial: Uma entrada deliberadamente criada para fazer um modelo de IA cometer um erro, frequentemente adicionando perturbações sutis imperceptíveis para os humanos.
  ​
* Robustez Adversarial – Robustez adversarial em IA refere-se à capacidade de um modelo de manter seu desempenho e resistir a ser enganado ou manipulado por entradas maliciosas intencionalmente elaboradas para causar erros.
  ​
* Agente – Agentes de IA são sistemas de software que utilizam IA para perseguir objetivos e completar tarefas em nome dos usuários. Eles demonstram raciocínio, planejamento e memória, e possuem um nível de autonomia para tomar decisões, aprender e se adaptar.
  ​
* Agentic AI: Sistemas de IA que podem operar com algum grau de autonomia para alcançar objetivos, frequentemente tomando decisões e ações sem intervenção humana direta.
  ​
* Controle de Acesso Baseado em Atributos (ABAC): Um paradigma de controle de acesso onde as decisões de autorização são baseadas em atributos do usuário, recurso, ação e ambiente, avaliados no momento da consulta.
  ​
* Ataque Backdoor: Um tipo de ataque de envenenamento de dados onde o modelo é treinado para responder de uma maneira específica a certos gatilhos enquanto se comporta normalmente caso contrário.
  ​
* Viés: Erros sistemáticos nas saídas do modelo de IA que podem levar a resultados injustos ou discriminatórios para certos grupos ou em contextos específicos.
  ​
* Exploração de Viés: Uma técnica de ataque que aproveita os vieses conhecidos em modelos de IA para manipular saídas ou resultados.
  ​
* Cedar: linguagem e mecanismo de políticas da Amazon para permissões detalhadas usadas na implementação de ABAC para sistemas de IA.
  ​
* Cadeia de Pensamento: Uma técnica para melhorar o raciocínio em modelos de linguagem gerando passos intermediários de raciocínio antes de produzir uma resposta final.
  ​
* Disjuntores: Mecanismos que interrompem automaticamente as operações do sistema de IA quando limites específicos de risco são ultrapassados.
  ​
* Serviço de Inferência Confidencial: Um serviço de inferência que executa modelos de IA dentro de um ambiente de execução confiável (TEE) ou mecanismo equivalente de computação confidencial, garantindo que os pesos do modelo e os dados de inferência permaneçam criptografados, selados e protegidos contra acesso não autorizado ou adulteração.
  ​
* Carga de Trabalho Confidencial: Uma carga de trabalho de IA (por exemplo, treinamento, inferência, pré-processamento) executada dentro de um ambiente de execução confiável (TEE) com isolamento imposto por hardware, criptografia de memória e atestado remoto para proteger o código, os dados e os modelos contra acesso do host ou de co-inquilinos.
  ​
* Vazamento de Dados: Exposição não intencional de informações sensíveis por meio das saídas ou comportamento do modelo de IA.
  ​
* Envenenamento de Dados: A corrupção deliberada dos dados de treinamento para comprometer a integridade do modelo, frequentemente para instalar portas dos fundos ou degradar o desempenho.
  ​
* Privacidade Diferencial – A privacidade diferencial é uma estrutura matematicamente rigorosa para a divulgação de informações estatísticas sobre conjuntos de dados, protegendo a privacidade dos indivíduos. Ela permite que um detentor de dados compartilhe padrões agregados do grupo enquanto limita as informações que são vazadas sobre indivíduos específicos.
  ​
* Incorporação: Representações vetoriais densas de dados (texto, imagens, etc.) que capturam o significado semântico em um espaço de alta dimensionalidade.
  ​
* Explicabilidade – Explicabilidade em IA é a capacidade de um sistema de IA fornecer motivos compreensíveis para humanos para suas decisões e previsões, oferecendo insights sobre seu funcionamento interno.
  ​
* IA Explicável (XAI): sistemas de IA projetados para fornecer explicações compreensíveis para humanos sobre suas decisões e comportamentos por meio de várias técnicas e estruturas.
  ​
* Aprendizado Federado: Uma abordagem de aprendizado de máquina onde os modelos são treinados em múltiplos dispositivos descentralizados que possuem amostras de dados locais, sem trocar os próprios dados.
  ​
* Formulação: A receita ou método usado para produzir um artefato ou conjunto de dados, como hiperparâmetros, configuração de treinamento, etapas de pré-processamento ou scripts de compilação.
  ​
* Guardrails: Restrições implementadas para impedir que sistemas de IA produzam resultados prejudiciais, tendenciosos ou indesejáveis.
  ​
* Alucinação – Uma alucinação de IA refere-se a um fenômeno em que um modelo de IA gera informações incorretas ou enganosas que não são baseadas em seus dados de treinamento ou na realidade factual.
  ​
* Humano no Loop (HITL): Sistemas projetados para exigir supervisão, verificação ou intervenção humana em pontos críticos de decisão.
  ​
* Infraestrutura como Código (IaC): Gerenciamento e provisionamento de infraestrutura por meio de código em vez de processos manuais, permitindo a análise de segurança e implantações consistentes.
  ​
* Jailbreak: Técnicas usadas para contornar as salvaguardas de segurança em sistemas de IA, particularmente em grandes modelos de linguagem, para produzir conteúdo proibido.
  ​
* Privilégio Mínimo: O princípio de segurança que concede apenas os direitos de acesso mínimos necessários para usuários e processos.
  ​
* LIME (Explicações Localmente Interpretáveis e Agnósticas ao Modelo): Uma técnica para explicar as previsões de qualquer classificador de aprendizado de máquina aproximando-o localmente com um modelo interpretável.
  ​
* MCP (Protocolo de Contexto de Modelo): Um protocolo que permite que modelos de IA e agentes acessem ferramentas externas, fontes de dados e recursos por meio da troca de solicitações e respostas estruturadas e tipadas através de um transporte definido.
  ​
* Ataque de Inferência de Associação: Um ataque que tem como objetivo determinar se um ponto de dados específico foi utilizado para treinar um modelo de aprendizado de máquina.
  ​
* MITRE ATLAS: Panorama de Ameaças Adversárias para Sistemas de Inteligência Artificial; uma base de conhecimento de táticas e técnicas adversárias contra sistemas de IA.
  ​
* Ficha do Modelo – Uma ficha do modelo é um documento que fornece informações padronizadas sobre o desempenho, limitações, usos pretendidos e considerações éticas de um modelo de IA para promover a transparência e o desenvolvimento responsável de IA.
  ​
* Extração de Modelo: Um ataque onde um adversário consulta repetidamente um modelo-alvo para criar uma cópia funcionalmente similar sem autorização.
  ​
* Inversão de Modelo: Um ataque que tenta reconstruir os dados de treinamento analisando as saídas do modelo.
  ​
* Gestão do Ciclo de Vida do Modelo – A Gestão do Ciclo de Vida do Modelo de IA é o processo de supervisionar todas as etapas da existência de um modelo de IA, incluindo seu design, desenvolvimento, implantação, monitoramento, manutenção e eventual aposentadoria, para garantir que ele permaneça eficaz e alinhado com os objetivos.
  ​
* Envenenamento de modelo: Introdução de vulnerabilidades ou backdoors diretamente em um modelo durante o processo de treinamento.
  ​
* Roubo de Modelo/Furto: Extrair uma cópia ou aproximação de um modelo proprietário por meio de consultas repetidas.
  ​
* Sistema Multiagente: Um sistema composto por múltiplos agentes de IA interagindo, cada um com capacidades e objetivos potencialmente diferentes.
  ​
* OPA (Open Policy Agent): Um motor de políticas open-source que permite a aplicação unificada de políticas em toda a pilha.
  ​
* Aprendizado de Máquina com Preservação de Privacidade (PPML): Técnicas e métodos para treinar e implementar modelos de ML enquanto protegem a privacidade dos dados de treinamento.
  ​
* Injeção de Prompt: Um ataque onde instruções maliciosas são incorporadas nas entradas para substituir o comportamento pretendido de um modelo.
  ​
* RAG (Geração Aumentada por Recuperação): Uma técnica que aprimora grandes modelos de linguagem ao recuperar informações relevantes de fontes externas de conhecimento antes de gerar uma resposta.
  ​
* Red-Teaming: A prática de testar ativamente sistemas de IA simulando ataques adversariais para identificar vulnerabilidades.
  ​
* SBOM (Lista de Materiais de Software): Um registro formal que contém os detalhes e as relações da cadeia de suprimentos de vários componentes usados na construção de software ou modelos de IA.
  ​
* SHAP (Explicações Aditivas de Shapley): Uma abordagem de teoria dos jogos para explicar a saída de qualquer modelo de aprendizado de máquina, calculando a contribuição de cada característica para a predição.
  ​
* Autenticação Forte: Autenticação que resiste ao roubo de credenciais e à reprodução, exigindo pelo menos dois fatores (conhecimento, posse, inherência) e mecanismos resistentes a phishing, como FIDO2/WebAuthn, autenticação de serviço baseada em certificado ou tokens de curta duração.
  ​
* Ataque à Cadeia de Suprimentos: Comprometendo um sistema ao visar elementos menos seguros em sua cadeia de suprimentos, como bibliotecas de terceiros, conjuntos de dados ou modelos pré-treinados.
  ​
* Aprendizado por Transferência: Uma técnica onde um modelo desenvolvido para uma tarefa é reutilizado como ponto de partida para um modelo em uma segunda tarefa.
  ​
* Banco de Dados Vetorial: Um banco de dados especializado projetado para armazenar vetores de alta dimensionalidade (embeddings) e realizar buscas eficientes por similaridade.
  ​
* Varredura de Vulnerabilidades: Ferramentas automáticas que identificam vulnerabilidades de segurança conhecidas em componentes de software, incluindo frameworks de IA e dependências.
  ​
* Marcação d'água: Técnicas para incorporar marcadores imperceptíveis em conteúdo gerado por IA para rastrear sua origem ou detectar geração por IA.
  ​
* Vulnerabilidade Zero-Day: Uma vulnerabilidade previamente desconhecida que os atacantes podem explorar antes que os desenvolvedores criem e implementem uma correção.

