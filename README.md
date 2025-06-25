# Desafio_AZ104
Este repositório contém o resumo das lições aprendidas durante o desenvolvimento do Bootcamp Microsoft - Azure Administrator Certification (AZ-104) da DIO.

## Virtual Machine
As Máquinas Virtuais (VMs) no Azure são recursos de computação escaláveis e sob demanda. Elas oferecem controle total sobre o sistema operacional, com a Microsoft gerenciando a infraestrutura física subjacente. São ideais para desenvolvimento, testes e migração de aplicações, suportando sistemas como Windows e Linux. VMs possuem diversos tamanhos e configurações de disco, afetando diretamente custo e performance. O Azure garante alta disponibilidade com Conjuntos de Disponibilidade, Domínios de Falha e Domínios de Atualização. Suportam escalabilidade vertical (redimensionamento) e horizontal (VMSS). Os custos variam por tamanho, SO e uso, com opções como Instâncias Spot. Podem ser gerenciadas por diversas ferramentas como Portal, ARM, CLI e PowerShell.

## Virtual Machine Scale Set
Os Conjuntos de Dimensionamento de Máquinas Virtuais (VMSS) do Azure permitem criar e gerenciar um grupo de Máquinas Virtuais (VMs) idênticas e com balanceamento de carga. Eles são projetados para oferecer escalabilidade automática, permitindo que o número de instâncias de VM aumente ou diminua em resposta à demanda ou a um cronograma definido, sem a necessidade de pré-provisionamento.
O VMSS centraliza o gerenciamento, configuração e atualização de um grande número de VMs, sendo ideal para serviços de grande escala, computação, big data e workloads de contêineres. As VMs dentro de um VMSS são distribuídas em múltiplos domínios de falha e atualização para maximizar a disponibilidade e resiliência contra interrupções ou manutenções. Podem ser criados e gerenciados via Portal do Azure, CLI do Azure, Azure PowerShell ou modelos Azure Resource Manager (ARM). Um VMSS padrão suporta até 100 instâncias, podendo chegar a 1000 com configurações específicas. Eles combinam o modelo IaaS de VMs com funcionalidades PaaS, como escala e automação.

## Availability Sets
Conjuntos de Disponibilidade (Availability Sets) no Azure são um recurso para garantir alta disponibilidade de Máquinas Virtuais (VMs) dentro de um datacenter. Eles distribuem as VMs em diferentes **Domínios de Falha (FDs)**, que são racks físicos separados com fontes de energia e rede independentes, protegendo contra falhas de hardware. Também as alocam em **Domínios de Atualização (UDs)**, assegurando que as VMs sejam atualizadas sequencialmente durante manutenções planejadas para minimizar o tempo de inatividade. Conjuntos de Disponibilidade exigem no mínimo duas VMs e devem ser configurados na criação. Oferecem um SLA de 99,95% e são obrigatórios para usar balanceadores de carga.

## Storage Account
Uma conta de armazenamento do Azure é um contêiner lógico unificado para armazenar dados na nuvem. Ela oferece serviços como blobs (para dados não estruturados), arquivos (compartilhamentos SMB), filas (mensagens) e tabelas (dados NoSQL). Essas contas são altamente escaláveis, duráveis e disponíveis, acessíveis globalmente via HTTP/HTTPS. Existem tipos como Standard e Premium, e General-purpose v2 é o mais recomendado. A replicação (LRS, ZRS, GRS, etc.) garante redundância. O custo é pago pelo uso, otimizado por camadas de acesso (quente, esporádico, arquivo). A segurança é gerenciada por chaves de acesso e Assinaturas de Acesso Compartilhado (SAS), com criptografia de dados em repouso.

## Microsoft Entra ID
Microsoft Entra ID (anteriormente Azure Active Directory) é o serviço de gerenciamento de identidade e acesso baseado em nuvem da Microsoft. Ele centraliza a gestão de identidades, funções e acessos a recursos internos e milhares de aplicações SaaS, como Office 365 e Azure Portal.
O Entra ID oferece segurança robusta com recursos como autenticação multifator (MFA), proteção de identidade e redefinição de senha por autoatendimento (SSPR). Operando como PaaS, a Microsoft gerencia sua infraestrutura subjacente, liberando o cliente da manutenção. É um diretório multitenant e pode ser integrado ao Active Directory local via Microsoft Entra Connect, facilitando ambientes híbridos e oferecendo logon único (SSO).

## Virtual Network
Rede Virtual do Azure (VNet) é o componente fundamental para a construção de redes privadas na nuvem. Ela virtualiza sua rede local, permitindo comunicação segura entre Máquinas Virtuais (VMs), internet e, crucialmente, suas redes on-premises para cenários híbridos.
As VNets são um isolamento lógico dos recursos de nuvem, onde você define seus próprios espaços de endereçamento IP e sub-redes para segmentação e controle. Elas suportam emparelhamento (peering) para conectar VNets na mesma ou em diferentes regiões e são protegidas por Grupos de Segurança de Rede (NSGs) para filtrar o tráfego. O Azure gerencia a infraestrutura de rede subjacente, liberando você da complexidade de hardware físico.

## Network Security Group
Network Security Group (NSG) do Azure atua como um firewall de nível de nuvem. Ele contém uma lista de regras de segurança que permitem ou negam o tráfego de rede de entrada e saída para recursos conectados a Redes Virtuais (VNets) do Azure.
As regras do NSG são baseadas em uma 5-tupla (IP de origem/destino, porta de origem/destino e protocolo) e são processadas por prioridade (menor número = maior prioridade). NSGs podem ser associados a sub-redes (aplicando regras a todas as VMs na sub-rede) ou a interfaces de rede (para VMs específicas). Isso oferece proteção granular e flexibilidade para controlar o fluxo de tráfego, essencial para a segurança de IaaS.

## Peering
Emparelhamento (peering) no Azure permite a conexão direta entre Redes Virtuais (VNets), proporcionando comunicação segura, de baixa latência e alta largura de banda. Ele utiliza a rede backbone da Microsoft, eliminando a necessidade de gateways e, consequentemente, reduzindo custos e complexidade.
É ideal para cenários como replicação de dados e failover. Contudo, há um limite de 500 conexões de peering por VNet. É importante notar que o emparelhamento global não pode acessar o IP de front-end de um Azure Load Balancer na camada Básica, exigindo uma VPN VNet-to-VNet nesses casos.

## App Service Plan
É o recurso do Azure que define o poder computacional alocado para hospedar aplicações web, APIs, back-ends móveis e funções. Atuando como um servidor subjacente gerenciado pela Microsoft, abstrai a infraestrutura do usuário. Ele oferece diferentes SKUs (Basic, Standard, Premium, Isolated) com variados níveis de recursos e funcionalidades, como escalabilidade automática, zonas de disponibilidade e SLA, com VMs dedicadas para ambientes de produção. O SKU não pode ser alterado após a criação.
O Azure Web App é a aplicação PaaS que executa sobre um App Service Plan. Permite publicar código ou contêineres Docker em diversas linguagens (e.g., .NET, Java, Python). Os benefícios incluem alta disponibilidade, escala automática (em SKUs compatíveis), domínios customizados, certificados SSL e deployment slots para ambientes de preparo. A Microsoft gerencia a infraestrutura, liberando o foco no código da aplicação.

## Azure Container Services
Os serviços de contêiner do Azure oferecem plataformas de virtualização leve para aplicações, abstraindo a infraestrutura subjacente. O Azure Container Instances (ACI) é uma oferta PaaS que permite executar contêineres individuais ou grupos de contêineres rapidamente, sem a necessidade de gerenciar máquinas virtuais ou orquestradores. É ideal para workloads de curta duração, testes e automação.
Para orquestração robusta e alta disponibilidade de aplicações em contêineres em escala, o Azure Kubernetes Service (AKS) é a solução gerenciada. Ele permite criar e escalar clusters Kubernetes, onde o Azure gerencia o plano de controle e o usuário é responsável apenas pelos nodes de agente. Ferramentas como o Azure Container Registry (ACR) fornecem um repositório seguro para imagens Docker, e o Azure Web App for Containers estende o App Service para hospedar aplicações web containerizadas, com escala e gestão de infraestrutura pela plataforma.

## Azure Load Balancers
O Azure oferece uma gama de serviços para balanceamento de carga, cada um com funcionalidades distintas. O Azure Load Balancer opera na Camada 4 (transporte), distribuindo eficientemente tráfego TCP/UDP entre instâncias íntegras de serviços. É um serviço regional, adequado para balanceamento interno ou público, com SLAs de até 99,99% no SKU Standard.
Para requisitos mais avançados na Camada 7 (aplicação), o Azure Application Gateway é ideal para aplicações web, fornecendo terminação SSL, roteamento baseado em URL e um Web Application Firewall (WAF) para segurança. Ele também opera em nível regional.
Em cenários de distribuição global, o Azure Traffic Manager roteia o tráfego via resolução DNS, sem atuar em camadas OSI específicas, otimizando a entrega entre regiões. Complementarmente, o Azure Front Door é uma rede de entrega de aplicações que oferece balanceamento de Camada 7 global, aceleração de site, WAF e failover rápido, sendo uma alternativa de alto desempenho para aplicações distribuídas.

## Storage
O Azure oferece diversos serviços de armazenamento escaláveis e duráveis. A Azure Storage Account é a solução central para armazenar dados estruturados e não estruturados, acessível via HTTP/HTTPS. Ela suporta:
• Azure Blobs: repositório de objetos para grandes quantidades de dados não estruturados (texto, binários), ideal para imagens, vídeos, backups e análise de Big Data (Data Lake Storage Gen2). Pode ser Block Blobs (até 200GB) ou Page Blobs (até 1TB, para VMs e bancos de dados).
• Azure Files: compartilhamentos de arquivos gerenciados na nuvem, acessíveis via protocolos SMB/NFS, adequados para substituir servidores de arquivos locais e fornecer armazenamento persistente para contêineres.
• Azure Queues: Armazena grandes volumes de mensagens (até 64KB) para comunicação confiável e assíncrona entre componentes de aplicativos.
• Azure Tables: Banco de dados NoSQL de chave/valor para dados semiestruturados, oferecendo um design sem esquema e acesso rápido e econômico.
• Azure Disks: Volumes de armazenamento em nível de bloco para VMs do Azure, gerenciados pela plataforma.
Todos os dados são criptografados em repouso (SSE AES 256-bit) e em trânsito.

## Network Watcher
O Azure Network Watcher é um serviço regional do Azure Monitor, focado em diagnóstico e troubleshooting de rede. Ele provisiona automaticamente um resource group por região onde há Virtual Networks. Suas ferramentas incluem:
• Topology: Gera uma representação visual da rede, mostrando recursos e relações.
• Connection Monitor: Testa a conectividade entre endpoints, exigindo a instalação do Network Watcher Agent nas VMs e um Workspace do Log Analytics para armazenamento de dados.
• NSG Flow Logs: Registra informações detalhadas do tráfego que flui através de um Network Security Group, armazenando-as no Azure Storage para análise posterior. Complementado pelo Traffic Analytics, que oferece insights de tráfego e largura de banda.
• IP Flow Verify e Next Hop: Diagnostica problemas de conectividade e determina o roteamento correto.
O serviço é essencial para gerenciar a saúde e performance de redes no Azure.

## Azure Monitor
É a console central de monitoramento do Azure, reunindo LOGS e MÉTRICAS de recursos no Azure, em ambientes on-premises e de outras nuvens. Ele oferece ferramentas como Log Analytics para armazenamento e análise de logs utilizando KQL, e Metrics Explorer para métricas. É possível configurar alertas com base em regras e respostas automatizadas, como autoscale. O Application Insights e os Insights de Contêiner fornecem monitoramento de performance granular para aplicações e workloads em contêineres.

## Workspace do Log Analytics
O Workspace do Log Analytics é a **solução analítica central** do Azure Monitor para **coleta, armazenamento e análise** de **LOGS** (registros textuais) e **MÉTRICAS** (números de desempenho). Atuando como um **banco de dados de logs e métricas**, ele ingere dados de recursos no Azure, on-premises e outras nuvens, incluindo Event Logs do Windows, Syslog do Linux e logs do IIS. A Kusto Query Language (KQL) é utilizada para **recuperar, consolidar e analisar rapidamente** os dados coletados. Possibilita a configuração de **alertas com base em regras e respostas automatizadas**, como autoscale. É o destino para dados de monitoramento de diversas ferramentas e soluções, como Azure Sentinel e Application Insights, e oferece a criação de **workbooks e dashboards** para visualização e relatórios.
