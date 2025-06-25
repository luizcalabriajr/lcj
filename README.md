# lcj

##Criação de Ambiente para Desenvolvimento
Objetivo: Criar uma rede isolada com uma máquina virtual para desenvolvedores usarem em testes.

Tarefas:

Criar um Resource Group chamado RG-Dev.

Criar uma Virtual Network chamada VNet-Dev com duas subnets (frontend e backend).

Criar uma VM Windows Server 2022 com IP público na subnet frontend.

Criar uma NSG com regras que permitam acesso RDP (porta 3389) apenas do seu IP.

Instalar IIS na VM e testar via navegador.

##Gerenciamento de Acesso com RBAC
Objetivo: Garantir que somente o time de rede possa alterar configurações da VNet.

Tarefas:

Criar um grupo no Azure AD chamado NetAdmins.

Adicionar seu usuário de teste a esse grupo.

Aplicar a Role Network Contributor no escopo da VNet VNet-Dev.

Validar que o usuário pode editar a VNet, mas não pode deletar a VM.

##Backup e Recuperação de Dados
Objetivo: Garantir que uma VM tenha backup diário com retenção de 30 dias.

Tarefas:

Criar um Recovery Services Vault.

Criar uma política de backup diária com retenção de 30 dias.

Associar a VM do cenário 1 ao cofre de backup.

Iniciar um backup manual e verificar o status.

Simular uma exclusão da VM e restaurá-la com o backup feito.

##Monitoramento com Alertas
Objetivo: Criar alertas para monitorar o uso de CPU de uma VM.

Tarefas:

Habilitar o Azure Monitor para a VM.

Criar um Log Analytics Workspace e conectá-lo à VM.

Criar um alerta que dispare quando a CPU passar de 80% por mais de 5 minutos.

Configurar um grupo de ação com envio de e-mail.

Forçar carga na VM para validar se o alerta funciona.

##Implementação de Política de Governança
Objetivo: Impedir que recursos sejam criados fora da região Brazil South.

Tarefas:

Criar uma política personalizada que restrinja a criação de recursos a Brazil South.

Atribuir a política ao Subscription.

Testar a criação de um recurso em East US e verificar se é bloqueado.

Testar a criação em Brazil South e verificar se é permitido.

##Escalonamento Automático de VMs
Objetivo: Garantir economia automatizando o escalonamento de máquinas virtuais.

Tarefas:

Criar uma VM em um Scale Set com duas instâncias.

Configurar regras de escalonamento baseadas na CPU (ex: escala para 3 instâncias se CPU > 75%).

Testar o aumento/redução de instâncias usando o Azure Load Generator ou stress tool.

Verificar logs de escalonamento.

##Configuração de Site-to-Site VPN
Objetivo: Simular a conexão segura entre o Azure e um datacenter local (usando endereço IP simulado).

Tarefas:

Criar uma Gateway Subnet e um VPN Gateway.

Criar uma conexão com IP público simulado (ex: 40.112.45.23).

Definir uma Shared Key e políticas de IP.

Verificar o status da conexão (ficará como “Conectando” sem IP real, mas serve como treino).

##Gestão de Custos e Tags
Objetivo: Organizar e acompanhar os custos de diferentes ambientes.

Tarefas:

Criar recursos com tags como: Environment=Dev, Owner=Luiz.

Usar Azure Cost Management para filtrar gastos por tag.

Criar alertas de custo mensal por grupo de recurso.
