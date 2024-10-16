# Dominando-o-Armazenamento-na-Azure
Resposta ao desafio DIO - Dominando o Armazenamento na Azure
Criar uma conta de armazenamento no Azure é uma tarefa relativamente simples. Vou guiá-lo passo a passo por todo o processo, desde o acesso ao portal até a configuração das opções essenciais.

---

### Passo 1: Acesse o Portal do Azure
1. Vá para [portal.azure.com](https://portal.azure.com/) e faça login com suas credenciais.
2. No painel inicial, localize a barra de pesquisa e digite "Armazenamento". Clique em **Contas de Armazenamento** no menu suspenso que aparecerá.

### Passo 2: Inicie o Processo de Criação
1. Na página de Contas de Armazenamento, clique em **Criar** (botão +Criar no topo da página).
2. Você será redirecionado para uma nova página onde pode configurar os detalhes da sua conta de armazenamento.

### Passo 3: Configure os Detalhes Básicos
1. **Assinatura**: Selecione a assinatura na qual você deseja criar a conta de armazenamento.
2. **Grupo de Recursos**: Selecione um grupo de recursos existente ou crie um novo, se desejar organizar sua conta dentro de um grupo específico.
3. **Nome da Conta de Armazenamento**: Escolha um nome exclusivo para a conta de armazenamento. Este nome deve ser único em toda a plataforma Azure.
4. **Região**: Escolha a região onde deseja armazenar seus dados. É recomendável escolher uma região próxima de onde os dados serão mais utilizados para melhorar a performance.
5. **Desempenho**: Selecione **Standard** ou **Premium**, dependendo da necessidade de desempenho e do tipo de acesso.
6. **Replicação**: Escolha entre as opções de replicação, como **Locally-redundant storage (LRS)**, **Geo-redundant storage (GRS)**, **Zone-redundant storage (ZRS)**, etc.
O Azure oferece vários tipos de replicação de dados para atender diferentes necessidades de disponibilidade e redundância, com diferentes níveis de proteção para falhas locais, regionais e de desastres naturais. Cada tipo de replicação tem um caso de uso específico e impacta diretamente nos custos, então a escolha correta depende das necessidades do projeto e da criticidade dos dados. Abaixo estão os tipos de replicação oferecidos pelo Azure:

## 1. **Locally Redundant Storage (LRS)**
   - **Descrição**: LRS mantém três cópias de seus dados dentro de um único datacenter em uma região específica. Isso fornece proteção contra falhas de hardware no datacenter.
   - **Redundância**: Replicação interna em três cópias no mesmo datacenter.
   - **Vantagens**: Opção mais econômica, ideal para dados que podem ser facilmente recuperados ou que não requerem alta durabilidade contra desastres regionais.
   - **Caso de Uso**: Dados de desenvolvimento e teste, backups que podem ser facilmente recuperados, ou informações que têm baixa criticidade.

## 2. **Zone-Redundant Storage (ZRS)**
   - **Descrição**: ZRS mantém três cópias dos dados em três zonas de disponibilidade diferentes dentro da mesma região. Cada zona de disponibilidade possui infraestrutura independente (como energia, rede e refrigeração), o que protege os dados contra falhas de um datacenter específico.
   - **Redundância**: Replicação em três zonas de disponibilidade na mesma região.
   - **Vantagens**: Protege contra falhas regionais e é uma ótima escolha para dados que exigem alta disponibilidade e durabilidade.
   - **Caso de Uso**: Aplicações críticas que exigem continuidade de serviço mesmo em caso de falhas em um datacenter específico, como dados de aplicações SaaS.

## 3. **Geo-Redundant Storage (GRS)**
   - **Descrição**: GRS replica dados entre duas regiões geograficamente distantes, com três cópias em cada uma das regiões. Isso significa que, além das três cópias locais (LRS), o Azure faz a replicação dos dados para outra região emparelhada, de modo a garantir disponibilidade mesmo em caso de desastres que afetem uma região inteira.
   - **Redundância**: Seis cópias no total, três na região primária e três na região secundária emparelhada.
   - **Vantagens**: Oferece um nível adicional de durabilidade, garantindo que os dados estejam disponíveis em caso de falhas graves, como desastres naturais.
   - **Caso de Uso**: Dados altamente críticos que precisam ser protegidos contra falhas regionais, como arquivos de backup de longo prazo e dados de recuperação de desastres.

## 4. **Read-Access Geo-Redundant Storage (RA-GRS)**
   - **Descrição**: RA-GRS oferece o mesmo nível de replicação do GRS, mas com a vantagem adicional de permitir acesso de leitura à cópia de dados replicada na região secundária. Esse tipo de replicação garante que, em caso de falha na região primária, os dados ainda possam ser lidos na região secundária.
   - **Redundância**: Seis cópias, com acesso de leitura à região secundária.
   - **Vantagens**: Permite uma continuidade de acesso aos dados durante uma falha na região primária, sendo ideal para aplicativos que exigem alta disponibilidade de leitura.
   - **Caso de Uso**: Sistemas de backup e recuperação de desastres que exigem acesso imediato aos dados, como sistemas financeiros, que não podem ter interrupção de leitura.

## 5. **Geo-Zone-Redundant Storage (GZRS)**
   - **Descrição**: GZRS combina as vantagens do ZRS e GRS, replicando dados em múltiplas zonas de disponibilidade em uma região primária e replicando esses dados em outra região distante. Isso significa que os dados são protegidos contra falhas locais e regionais.
   - **Redundância**: Replicação entre zonas e entre regiões (total de nove cópias: três em cada zona da região primária e mais três na região secundária).
   - **Vantagens**: Oferece o mais alto nível de redundância e durabilidade. Garante proteção contra falhas de datacenter e de região, sendo adequado para cargas de trabalho extremamente críticas.
   - **Caso de Uso**: Aplicações essenciais para continuidade de negócios, onde é necessário garantir disponibilidade de dados mesmo em cenários de desastres regionais, como sistemas de bancos e infraestruturas de governo.

## 6. **Read-Access Geo-Zone-Redundant Storage (RA-GZRS)**
   - **Descrição**: RA-GZRS é similar ao GZRS, mas permite acesso de leitura à região secundária, garantindo uma continuidade de acesso em caso de falha na região primária.
   - **Redundância**: Nove cópias, com acesso de leitura na região secundária.
   - **Vantagens**: Proteção completa contra falhas de zona e de região, com acesso de leitura garantido em caso de indisponibilidade.
   - **Caso de Uso**: Sistemas de missão crítica com demanda contínua de leitura e alta disponibilidade, como sistemas de emergências, aplicativos de e-commerce e outras plataformas de serviço 24/7.

---

## Comparação Resumida dos Tipos de Replicação

| Tipo de Replicação | Redundância | Região Secundária | Acesso de Leitura na Região Secundária | Caso de Uso |
|--------------------|-------------|-------------------|---------------------------------------|-------------|
| **LRS**            | 3 cópias em 1 datacenter | Não | Não | Desenvolvimento, dados não críticos |
| **ZRS**            | 3 cópias em 3 zonas | Não | Não | Aplicativos com alta disponibilidade regional |
| **GRS**            | 3 cópias + 3 cópias remotas | Sim | Não | Dados críticos com alta durabilidade |
| **RA-GRS**         | 3 cópias + 3 cópias remotas | Sim | Sim | Continuidade de leitura em desastres |
| **GZRS**           | 3 cópias + 3 cópias por zona, replicação remota | Sim | Não | Cargas de trabalho extremamente críticas |
| **RA-GZRS**        | 3 cópias + 3 cópias por zona, replicação remota | Sim | Sim | Aplicativos essenciais com alta disponibilidade de leitura |

### Passo 4: Configure as Opções Avançadas
1. Clique na aba **Avançado**.
2. **Segurança**: Aqui você pode escolher se deseja habilitar o HTTPS apenas para acessar dados, controlar o acesso de rede, e definir políticas de criptografia.
3. **Conexão Privada**: Se desejar uma conexão direta e privada com a conta, configure as opções de conexão privada.

### Passo 5: Configure Redes e Controle de Acesso
1. Na aba **Rede**, você pode configurar redes virtuais e definir se deseja permitir ou negar o acesso público.
2. Escolha se deseja configurar firewalls ou aplicar uma política de segurança para limitar o acesso a determinadas redes.

### Passo 6: Configure Tags (Opcional)
1. Na aba **Tags**, você pode definir tags para facilitar a categorização e o gerenciamento de recursos.
2. As tags são opcionais, mas úteis para rastreamento de custos e organização de recursos em projetos complexos.

### Passo 7: Revise e Crie
1. Clique na aba **Revisar + Criar**.
2. O Azure fará uma verificação para garantir que todas as configurações estejam corretas.
3. Quando estiver pronto, clique em **Criar**. Isso iniciará o processo de implantação da conta de armazenamento.

---

### Passo 8: Gerencie e Acesse sua Conta de Armazenamento
1. Após a criação, vá para **Contas de Armazenamento** e selecione sua nova conta.
2. No painel da conta, você encontrará diversas opções para configurar e gerenciar seus serviços de armazenamento, como **Containers** (para Blobs), **Arquivos** e **Filas**.

---

### Conclusão
Agora, você tem uma conta de armazenamento configurada no Azure e pronta para uso! É possível gerenciar configurações avançadas, definir políticas de acesso, e otimizar o armazenamento para atender às necessidades específicas do seu projeto.

###Resumo de tipos de armazenamento

O Azure oferece diferentes tipos de armazenamento para atender a uma variedade de necessidades de armazenamento de dados, seja para aplicativos com alta performance, dados estruturados, armazenamento em arquivos ou backups. Esses tipos de armazenamento são configuráveis nas contas de armazenamento e otimizados para cenários específicos, incluindo armazenamento de objetos, arquivos, tabelas e filas. Abaixo estão os tipos de armazenamento disponíveis no Azure:

---

### 1. **Blob Storage**
   - **Descrição**: O armazenamento Blob (Binary Large Object) é o serviço de armazenamento de objetos do Azure. É ideal para armazenar grandes quantidades de dados não estruturados, como arquivos de mídia, logs e documentos.
   - **Tipos de Blobs**:
     - **Blobs de Bloco**: Ideais para arquivos de uso comum (textos, imagens, vídeos).
     - **Blobs de Página**: Usados principalmente para armazenamento de discos de máquinas virtuais.
     - **Blobs de Acréscimo**: Otimizados para dados que só recebem acréscimos, como logs de servidor.
   - **Camadas de Acesso**:
     - **Hot**: Armazenamento para dados acessados frequentemente.
     - **Cool**: Para dados que não são acessados com frequência e que podem ser armazenados por pelo menos 30 dias.
     - **Archive**: Armazenamento de longo prazo e mais econômico, para dados raramente acessados, como backups.
   - **Caso de Uso**: Ideal para armazenar mídia, backup de dados, dados de Big Data e armazenamento de arquivos que necessitam de alta durabilidade e escalabilidade.

### 2. **File Storage**
   - **Descrição**: Azure File Storage fornece armazenamento compartilhado em forma de arquivos, acessível via protocolo SMB (Server Message Block) e NFS (Network File System). Ele é gerenciado e acessível de várias VMs e dispositivos na mesma rede.
   - **Características**:
     - **Compatível com SMB e NFS**: Permite integração com sistemas Windows, Linux e MacOS.
     - **Snapshots**: Backup incremental de arquivos para recuperação.
     - **Azure File Sync**: Sincronização com servidores locais para integração de arquivos entre on-premises e Azure.
   - **Caso de Uso**: Aplicações que precisam compartilhar dados entre máquinas, armazenamento de arquivos de aplicações, e integração entre ambientes on-premises e nuvem.

### 3. **Queue Storage**
   - **Descrição**: O Azure Queue Storage oferece um sistema de filas, que permite a troca de mensagens entre componentes de um sistema de maneira assíncrona. Cada mensagem pode ter até 64 KB, e cada fila pode conter milhões de mensagens.
   - **Características**:
     - **Mensagens Assíncronas**: Ideal para comunicação desacoplada.
     - **Integração com Aplicações Web e Móveis**: Suporte para troca de mensagens em larga escala.
   - **Caso de Uso**: Ideal para aplicativos que exigem processamento em segundo plano ou distribuição de tarefas, como processamento de filas de pedidos em e-commerce ou para conectar microserviços de maneira desacoplada.

### 4. **Table Storage**
   - **Descrição**: O Azure Table Storage é uma solução de armazenamento NoSQL para dados estruturados, ideal para grandes volumes de dados de forma tabular, como logs de eventos e dados de dispositivos IoT.
   - **Características**:
     - **NoSQL**: Oferece armazenamento flexível e rápido, sem a necessidade de esquemas rígidos.
     - **Alta Escalabilidade**: Ótimo para armazenar grandes volumes de dados.
     - **Consulta por Partição e Linha**: Baseado em chaves de partição e chaves de linha, permitindo consultas rápidas.
   - **Caso de Uso**: Logs de aplicações, dados de telemetria de IoT, dados que necessitam de alta escalabilidade e que não exigem um banco de dados relacional completo.

### 5. **Disk Storage**
   - **Descrição**: O Azure Disk Storage é o tipo de armazenamento usado para discos de máquinas virtuais (VMs) no Azure. Ele permite criar discos gerenciados e personalizados, que podem ser usados por VMs para armazenamento persistente.
   - **Tipos de Discos**:
     - **Disco SSD Premium**: Projetado para aplicações que exigem alta IOPS e baixa latência, ideal para cargas de trabalho de produção críticas.
     - **Disco SSD Standard**: Boa opção para cargas de trabalho que exigem desempenho moderado a baixo custo.
     - **Disco HDD Standard**: Ideal para cargas de trabalho que não exigem alto desempenho, como servidores de arquivos ou backups.
   - **Caso de Uso**: Armazenamento persistente para VMs, bancos de dados de alta performance, aplicativos que exigem armazenamento com baixa latência.

---

### Comparação Resumida dos Tipos de Armazenamento

| Tipo de Armazenamento | Descrição | Caso de Uso | Observações |
|-----------------------|-----------|-------------|-------------|
| **Blob Storage**      | Armazenamento de objetos para grandes volumes de dados não estruturados | Armazenamento de mídia, logs, dados de Big Data | Camadas Hot, Cool e Archive para otimização de custo e desempenho |
| **File Storage**      | Armazenamento de arquivos compatível com SMB/NFS | Compartilhamento de arquivos entre VMs e dispositivos | Suporte a sincronização com on-premises |
| **Queue Storage**     | Sistema de filas para mensagens assíncronas | Processamento de tarefas em segundo plano, microserviços | Cada mensagem tem limite de 64 KB |
| **Table Storage**     | NoSQL para dados tabulares e altamente escaláveis | Logs de eventos, telemetria de IoT | Estrutura NoSQL com alta escalabilidade |
| **Disk Storage**      | Discos para VMs | Armazenamento persistente para bancos de dados e VMs | Opções SSD e HDD para diferentes necessidades de performance |

---

### Considerações Finais

A escolha do tipo de armazenamento depende das necessidades específicas do projeto:
- **Alta performance e baixa latência**: Use **Disk Storage Premium SSD** para bancos de dados e cargas de trabalho críticas.
- **Armazenamento econômico e escalável para objetos**: **Blob Storage** oferece opções otimizadas para dados acessados com pouca frequência.
- **Compartilhamento de arquivos**: **File Storage** facilita o compartilhamento de dados entre VMs e dispositivos.
- **Mensagens assíncronas**: **Queue Storage** permite comunicação entre microserviços e processamento em segundo plano.
- **Dados estruturados e escaláveis**: **Table Storage** é ideal para armazenar grandes volumes de dados em formato tabular.


###Migração com Azure

A migração de dados para o Azure pode envolver a movimentação de vários tipos de recursos, como bancos de dados, máquinas virtuais e dados de armazenamento. Abaixo está um tutorial detalhado para um processo de migração, com foco em migração de dados e arquivos para o Azure Blob Storage, que é um dos destinos mais comuns para armazenamento em nuvem. 

Vou guiar por um processo padrão que utiliza o **Azure Storage Migration Tool**, mas incluo também algumas outras ferramentas e métodos alternativos para diferentes necessidades.

---

### Passo 1: Planejamento da Migração
Antes de iniciar, é importante entender a quantidade de dados e o tempo estimado para migração. Siga esses passos iniciais:

1. **Avaliação dos Dados**: Identifique quais dados precisam ser migrados e sua estrutura (arquivos, dados de banco de dados, logs, etc.).
2. **Escolha da Ferramenta de Migração**: O Azure oferece várias opções, incluindo:
   - **AzCopy**: Para transferência de dados de grandes volumes em scripts.
   - **Azure Migrate**: Ferramenta abrangente para migração de VMs, bancos de dados e aplicativos.
   - **Azure Data Box**: Recomendado para grandes volumes de dados (terabytes ou petabytes).
   - **Azure Storage Migration Tool**: Para migração de arquivos e pastas para Blob Storage.

### Passo 2: Criar uma Conta de Armazenamento no Azure
1. Acesse o portal [Azure Portal](https://portal.azure.com/).
2. Na barra de pesquisa, busque por **Contas de Armazenamento**.
3. Clique em **+ Criar** e configure sua conta:
   - Escolha uma assinatura, grupo de recursos e região.
   - Defina o nome da conta e selecione o tipo de desempenho (Standard ou Premium).
   - Escolha o tipo de replicação mais adequado (LRS, GRS, etc.).
4. Clique em **Revisar + Criar** e em seguida em **Criar**.

### Passo 3: Configuração do Azure Storage Migration Tool
Se você optar por usar o Azure Storage Migration Tool, siga os passos abaixo:

1. **Baixar a Ferramenta**:
   - Acesse o site [Microsoft Azure Migration Tool](https://azure.microsoft.com/en-us/services/storage/migration/) e faça o download da ferramenta de migração.
2. **Instalar a Ferramenta**:
   - Siga as instruções de instalação e abra o aplicativo após a instalação.
3. **Autenticação no Azure**:
   - Abra a ferramenta e faça login com suas credenciais do Azure.
   - Conecte-se à sua conta de armazenamento, fornecendo o nome e a chave de acesso da conta criada no Passo 2.

### Passo 4: Configuração do Processo de Migração
1. **Seleção de Origem e Destino**:
   - **Origem**: Selecione o local dos dados que deseja migrar (pode ser um compartilhamento de rede, uma pasta local ou um drive externo).
   - **Destino**: Escolha a conta de armazenamento e o contêiner Blob para onde os dados serão migrados.
2. **Configurações de Migração**:
   - Escolha a **camada de armazenamento**: geralmente Hot, Cool ou Archive.
   - **Limite de largura de banda**: Defina uma limitação de velocidade de transferência se necessário (útil para evitar sobrecarga na rede).
3. **Opções de Configuração Adicionais**:
   - **Data Integrity**: Habilite a verificação de integridade dos dados.
   - **Erros e Retentativas**: Configure a política de erro para que a migração retente caso ocorra alguma falha temporária.

### Passo 5: Executar a Migração
1. Inicie a migração clicando em **Start Migration**.
2. A ferramenta começará a transferência dos dados. Você poderá ver o progresso e verificar se há erros em tempo real.
3. **Monitoramento**:
   - A ferramenta permite ver o andamento dos arquivos que foram migrados, além de oferecer logs detalhados de cada transferência.
   - Verifique se todos os arquivos foram copiados com sucesso e sem erros.

### Passo 6: Verificação Pós-Migração
1. **Verificar a Integridade dos Dados**:
   - Use a ferramenta para confirmar que todos os dados foram migrados corretamente, ou então faça uma amostragem manual.
2. **Testar o Acesso aos Dados**:
   - Tente acessar os dados migrados usando o Azure Storage Explorer (disponível para download gratuito) ou diretamente pelo Azure Portal.
   - Verifique se os dados e a estrutura estão corretos e se são acessíveis conforme esperado.
3. **Configurar Permissões de Acesso (se necessário)**:
   - No Azure Portal, configure permissões específicas para o acesso aos dados migrados, usando o controle de acesso baseado em função (RBAC) para definir quem pode acessar, ler ou modificar o conteúdo.

---

### Passo 7: Alternativas e Ferramentas Adicionais
Para diferentes cenários, você pode usar ferramentas alternativas:

1. **AzCopy**:
   - **Descrição**: Uma ferramenta de linha de comando usada para copiar dados para o Azure Blob Storage.
   - **Uso**:
     ```bash
     azcopy copy "local/file/path" "https://<storage_account>.blob.core.windows.net/<container_name>?<sas_token>"
     ```
2. **Azure Data Box**:
   - Ideal para grandes volumes de dados (terabytes a petabytes).
   - O dispositivo é enviado pela Microsoft, onde você carrega os dados localmente e depois o envia de volta para que eles sejam carregados diretamente na sua conta de armazenamento.
3. **Azure Migrate**:
   - Abrangente para migração de máquinas virtuais, bancos de dados e aplicações completas para o Azure.
   - Fornece funcionalidades de avaliação e preparação antes da migração, garantindo que o ambiente esteja pronto.

### Conclusão
Após concluir a migração e verificar a integridade dos dados, é importante monitorar o uso e custos no Azure. Configurar alertas e visualizar relatórios de uso podem ajudar a manter a previsibilidade de custos e a eficiência do ambiente no Azure.
