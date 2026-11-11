# ITTS IRIS – Guia do Usuário

O objetivo deste documento é apresentar o módulo **ITTS IRIS** e seus componentes.

---

## 1 – Introdução

### 1.1 - Introdução

**ITTS IRIS**
O IRIS (Identix RAIN Intelligence Suite) é o módulo ITTS para gestão de estoque e monitoramento de itens em tempo real.

### 1.2 - Funcionalidades:
- Gestão de Produtos e Estoque
- Movimentação de Itens entre etapas e locais
- Gestão e Uso de Provadores
- Histórico de Posição
- Histórico de Movimentação
- Histórico de Conferência

### 1.3 - Requisitos:
- Leitor RFID;
- 1 Tablet/Computador com Windows 10 ou superior para cada ponto de operação;
- Portas TCP/UPD para comunicação com o leitor permitida no firewall local.

### 1.4 - Gestão de Produtos e Estoque
Permite o controle dos produtos e estoque quantitativo e qualitativo dos itens em estoque.

### 1.5 - Movimentação de Itens entre etapas e locais
Tela para movimentar itens para uma nova etapa e um novo local. Os itens são identificados pela leitura RFID em tempo real ou pela pesquisa manual por identificador ou campo do produto.

### 1.6 - Gestão e Uso de Provadores
Cadastro dos provadores físicos da loja e controle do uso de cada provador, com o check-in e o check-out das peças pela leitura RFID. Inclui o dashboard e o relatório de uso dos provadores, com o tempo de permanência e as peças provadas.

### 1.7 - Histórico de Posição
Consulta da posição atual dos itens, com o status, a etapa e os campos do produto de cada item, e do ciclo de vida de cada item.

### 1.8 - Histórico de Movimentação
Consulta das entradas e saídas de itens entre as empresas, com a quantidade esperada e a quantidade processada de cada movimentação.

### 1.9 - Histórico de Conferência
Consulta das conferências realizadas, com os indicadores de itens conferidos, ausentes e divergentes de cada conferência.

### 1.10 - Acessando o Módulo
Os módulos disponíveis estarão visíveis com uma cor destacada na parte superior da tela principal.
Após o login, na tela inicial, selecione o módulo IRIS.
Ao acessar o módulo as funcionalidades disponíveis serão apresentadas.

## 2 – Gestão de Produtos e Estoque

### 2.1 - Produtos

Para acessar a gestão de produtos, selecione a opção “Produtos” no menu lateral. A listagem de produtos cadastrados será exibida.

**2.1.1 - Adicionando Produtos**
Para incluir um novo produto:
1. Selecione o botão “Adicionar”;
2. Informe o Grupo ao qual os itens serão cadastrados e o dispositivo que fará a leitura dos itens;
3. Selecione a opção "Iniciar Leitura". Assim que a leitura iniciar, uma mensagem de status da operação será apresentada;
4. Em caso de sucesso, a confirmação da leitura será apresentada, informando a quantidade de itens identificados. Também será apresentado a opção “Registrar entrada no Estoque”, essa opção além de inserir os produtos do sistema, também atualizando o status dos produtos lidos para "Em estoque". Selecione a opção "Registrar entrada no Estoque";
5. Em seguida, selecione a opção "Continuar" para confirmar a entrada dos produtos conforme os parâmetros selecionados. Uma mensagem de confirmação será apresentada;

Após a conclusão com sucesso, os novos produtos podem ser visualizados no grid na página de Produtos. Em caso de erro no processo, uma mensagem de falha será apresenta.

### 2.2 - Estoque
**2.2.1 - Acessando o Estoque**
Para visualizar o estoque atual, selecione a opção “Estoque” no menu lateral.

## 3 – Movimentação

### 3.1 - Movimentação de Itens

A tela de Movimentação de Itens permite movimentar itens para uma nova **etapa** e um novo **local**. Os itens podem ser incluídos na lista pela leitura RFID ou pela pesquisa manual.

Para acessar, selecione a opção **"Movimentação"** na tela inicial do módulo ou no menu lateral.

**3.1.1 - Requisitos**
- Dispositivo RFID padrão definido no navegador. Para definir, acesse **Dispositivos**, localize o leitor e selecione a opção **"Definir como Padrão"**. Sem o dispositivo padrão, a tela apresenta o aviso "Dispositivo RFID não configurado" e só permite incluir itens pela pesquisa manual;
- Permissão do grupo do usuário em "Movimentação de Itens": leitura para acessar a tela e inclusão para salvar a movimentação.

**3.1.2 - Incluindo itens pela leitura RFID**
1. Acesse a tela de Movimentação. A leitura é iniciada automaticamente no dispositivo padrão;
2. Aproxime os itens do leitor RFID;
3. Cada item lido é apresentado uma única vez na lista, com as colunas:
   - Item – Descrição e EPC do item;
   - Status – Status atual do item;
   - Etapa – Etapa atual do item;
   - Local – Local atual do item.

O contador acima da lista apresenta a quantidade de itens.

> Importante:
> Etiquetas que não pertencem a um item cadastrado no módulo IRIS não entram na lista.

**3.1.3 - Incluindo itens pela pesquisa**
Quando a etiqueta não pode ser lida, é possível incluir o item manualmente:
1. No campo **"Pesquisar em"**, selecione **"Identificador"** para pesquisar pelo EPC ou selecione um campo do produto;
2. Digite o texto completo ou parcial, com no mínimo 2 caracteres. O texto pode ser o início, o meio ou o final do valor;
3. Selecione a opção **"Pesquisar"** ou pressione Enter;
4. A janela de resultados apresenta a descrição, o EPC, o status e a etapa de cada item encontrado. Na pesquisa por campo, é apresentada também a coluna do campo selecionado;
5. Selecione a opção **"Adicionar"** no item desejado. O item entra na lista e o resultado passa a apresentar o rótulo **"Na lista"**;
6. Repita o passo anterior para incluir outros itens da mesma pesquisa e selecione a opção **"Fechar"**.

A pesquisa apresenta no máximo 50 resultados. Quando houver mais itens, é apresentada a mensagem para refinar a pesquisa. Se nenhum item for encontrado, é apresentada a mensagem "Nenhum item encontrado.".

A leitura RFID continua ativa durante a pesquisa.

**3.1.4 - Removendo itens da lista**
Para remover um item, selecione a opção de exclusão na linha do item e confirme a operação. O item removido não volta para a lista pela leitura RFID, mesmo com a etiqueta no campo do leitor. Para incluir o item novamente, use a pesquisa.

Para remover todos os itens e reiniciar a operação, selecione a opção **"Cancelar"** e confirme. Após o reinício, todas as etiquetas voltam a ser lidas.

**3.1.5 - Movimentando os itens**
1. Com os itens na lista, selecione a opção **"Movimentar"**. É necessário ter ao menos um item na lista;
2. Na janela **"Movimentar Itens"**, selecione a **Etapa** e o **Local** de destino dos itens. Os dois campos são obrigatórios;
3. Selecione a opção **"Salvar"**;
4. Em caso de sucesso, é apresentada a mensagem com a quantidade de itens movimentados. A lista é limpa e a leitura é reiniciada para uma nova movimentação.

Em caso de erro, as mensagens são apresentadas na janela e a lista de itens é mantida. Para fechar a janela sem movimentar, selecione a opção **"Cancelar"** da janela. A lista não é alterada.

> Importante:
> - Enquanto a janela "Movimentar Itens" estiver aberta, as novas leituras RFID são ignoradas. Assim, são movimentados somente os itens que estavam na lista.
> - Todos os itens movimentados juntos são registrados na mesma transação. A nova etapa e o novo local de cada item podem ser consultados no Histórico de Posição.

## 4 – Provadores

### 4.1 - Gestão e Manutenção de Provadores
A tela de Gestão e Manutenção permite cadastrar e configurar os provadores físicos da loja. Para acessar, selecione a opção **"Gestão e Manutenção"** na tela inicial do módulo ou no menu lateral.

No grid de dados é possível visualizar:
- Identificador – Número do provador;
- Sexo – Ícone masculino, feminino ou os dois ícones para provador unissex;
- Ativo – Situação do provador (Ativo ou Inativo).

**4.1.1 - Pesquisando provadores**
Selecione onde pesquisar (Identificador ou Sexo) e informe o texto na caixa de pesquisa.

**4.1.2 - Cadastrando provadores**
1. Selecione a opção **"Adicionar"**;
2. Informe os dados:
   - Quantidade – Quantidade de provadores que serão cadastrados;
   - Sexo – Unisex, Masculino ou Feminino;
   - Ativo – Indica se o provador está ativo.
3. Selecione a opção **"Salvar"**.

Os identificadores dos novos provadores continuam a numeração a partir do último provador cadastrado. Por exemplo: se o último provador é o 6 e são cadastrados 2 provadores, os novos provadores recebem os identificadores 7 e 8.

**4.1.3 - Ativando e inativando provadores**
Para alterar a situação de um provador, clique sobre o rótulo **"Ativo"** ou **"Inativo"** na linha do provador. Somente os provadores ativos podem ser usados no check-in.

**4.1.4 - Editando provadores**
Localize o provador na listagem, clique no botão **"Ações"** e selecione **"Editar"**. Altere o Sexo ou a situação e selecione a opção **"Salvar"**. O Identificador não pode ser alterado.

**4.1.5 - Excluindo provadores**
Localize o provador na listagem, clique no botão **"Ações"** e selecione **"Excluir"**. Confirme a exclusão na mensagem de alerta.

> Importante:
> A exclusão do provador exclui também o registro de uso atual do provador. Os dados do histórico de uso não são afetados.

### 4.2 - Uso dos Provadores
A tela de Provadores controla a entrada (check-in) e a saída (check-out) das peças nos provadores. Para acessar, selecione a opção **"Provadores"** na tela inicial do módulo ou no menu lateral.

**4.2.1 - Requisitos**
- Dispositivo RFID padrão definido no navegador. Para definir, acesse **Dispositivos**, localize o leitor e selecione a opção **"Definir como Padrão"**;
- Provadores ativos cadastrados na Gestão e Manutenção.

**4.2.2 - Tela inicial de uso**
Quando não há provadores ocupados, a tela apresenta a orientação "Faça uma leitura para iniciar – Aproxime a peça do leitor".

Quando há provadores ocupados, a tela apresenta um card para cada provador ocupado, com:
- Identificador do provador;
- Rótulo **"PROVADOR OCUPADO"**;
- Quantidade de peças no provador;
- Tempo de uso, atualizado em tempo real;
- Ícone do sexo do provador.

**4.2.3 - Fazendo o check-in**
1. Aproxime uma peça do leitor RFID:
   - Se a etiqueta não pertence a um produto cadastrado, é apresentado o alerta "Produto não cadastrado!";
   - Se a peça já está em um provador ocupado, o sistema abre o check-out desse provador (consulte o item 4.2.4).
2. Na janela **"Preferência do Provador"**, selecione o tipo de provador (Masculino, Feminino ou Unissex). Cada opção apresenta a quantidade de provadores livres e o total de provadores (exemplo: "Feminino 3/5"). As opções sem provador livre são apresentadas como **"Indisponível"**;
3. O sistema seleciona um provador livre do tipo escolhido e abre a tela **"CHECKIN"**, com o identificador do provador;
4. Aproxime as peças do leitor. Cada peça lida é incluída na lista, com a descrição, o EPC e o GTIN, e o contador de peças é atualizado;
5. Selecione a opção **"Salvar"** e confirme o check-in. É necessário ter ao menos uma peça na lista;
6. Remova as peças das proximidades do leitor, conforme a mensagem "Remova as peças!".

Após o check-in, o sistema retorna à tela inicial de uso, com o card do provador ocupado.

Na tela de check-in também é possível:
- Remover uma peça da lista, pela opção de exclusão na linha da peça;
- Remover todas as peças e reiniciar a leitura, pela opção **"Remover todos os itens"**;
- Trocar de provador, pela opção **"Escolher outro provador"**. A janela apresenta os provadores livres do mesmo sexo;
- Cancelar o check-in, pela opção **"Cancelar"**.

**4.2.4 - Fazendo o check-out**
Para iniciar o check-out, aproxime uma das peças do provador do leitor RFID na tela inicial de uso. O sistema abre a tela **"CHECKOUT"** do provador correspondente. Se a etiqueta não puder ser lida, clique no card do provador ocupado.

A tela de check-out apresenta as peças do check-in, com as colunas Item, Inconsistência e Leitura. Todas as peças iniciam com a leitura **"AUSENTE"**, e o contador apresenta a quantidade de peças ausentes.
1. Aproxime as peças do leitor. Cada peça lida passa para **"PRESENTE"** e o contador é atualizado;
2. Para cada peça que não pode ser lida, selecione a inconsistência na coluna **"Inconsistência"**: **"Tag Danificada"** ou **"Tag Perdida"**;
3. Selecione a opção **"Salvar"** e confirme o check-out;
4. Remova as peças das proximidades do leitor, conforme a mensagem "Remova as peças!".

Após o check-out, o sistema retorna à tela inicial de uso e o provador fica livre.

> Importante:
> - Não é permitido finalizar o check-out com peças ausentes sem inconsistência. Nesse caso, é apresentada a mensagem "Selecione a inconsistência para os itens ausentes".
> - Uma peça que fica cerca de 2 segundos sem leitura volta para "AUSENTE". Mantenha as peças próximas ao leitor até salvar.
> - Também é possível alterar a leitura da peça manualmente, clicando sobre o rótulo "AUSENTE" ou "PRESENTE".
> - Para reiniciar a conferência das peças, selecione a opção **"Reiniciar"**.

### 4.3 - Dashboard Provadores
O Dashboard Provadores apresenta os dados estatísticos de uso dos provadores. Para acessar, selecione a opção **"Dashboards"** na tela inicial do módulo ou no menu lateral e a aba **"Dashboard Provadores"**.

Informe o período nos campos de data inicial e final. Os indicadores apresentam:
- **Checkins** – Quantidade de check-ins no período;
- **Tempo Médio** – Tempo médio de uso dos provadores;
- **Média Peças** – Quantidade média de peças por check-in;
- **Inconsist.** – Quantidade de inconsistências informadas nos check-outs.

Os gráficos apresentam as **Peças Mais Provadas** e os **Horários de Pico** de check-in. Abaixo dos gráficos, o grid apresenta, para cada peça: Peça, Nº de Provas, Tempo Total (min), Tag Danificada e Tag Perdida.

### 4.4 - Relatório de uso de Provadores
O Relatório de uso de Provadores apresenta o uso dos provadores agrupado por mês, semana e data. Para acessar, selecione a opção **"Dashboards"** na tela inicial do módulo ou no menu lateral e a aba **"Relatório de uso de Provadores"**.

**4.4.1 - Consultando o relatório**
Informe o período nos campos de data inicial e final. Para cada data, o grid apresenta:
- Data do Registro;
- Nº de Checkins;
- Tempo Médio;
- Quant. Média de Itens;
- Nº de Inconsistências.

Expanda os agrupamentos de mês e semana para visualizar as datas. Expanda uma data para visualizar:
- **Registros de uso** – Provador, Entrada, Saída, Duração (min) e Itens Provados de cada check-in;
- **Estatísticas de uso peças** – Peça (GTIN), Provas, Tempo Total (min), Tags Danificadas e Tags Perdidas de cada peça.

**4.4.2 - Exportando o relatório**
Selecione a opção **"Exportar"** e escolha **"Para PDF"** ou **"Para Excel"**. O download do arquivo é feito com os dados do relatório.

## 5 – Histórico

As telas de histórico ficam na opção **"Histórico e Relatórios"**, na tela inicial do módulo ou no menu lateral. Cada histórico é apresentado em uma aba:
- **Relatório de Posição** – Histórico de Posição;
- **Relatório de Movimentação** – Histórico de Movimentação;
- **Histórico de Conferência** – Histórico de Conferência.

Todas as telas de histórico apresentam as opções:
- **Atualizar** – Carrega novamente os dados da tela;
- **Exportar** – Faz o download dos dados filtrados;
- **Mais Filtros** – Apresenta os filtros adicionais, como o filtro por período.

### 5.1 - Histórico de Posição
A tela de Histórico de Posição apresenta a posição atual de cada item: o status, a etapa e os valores dos campos do produto. Para acessar, selecione a opção **"Histórico e Relatórios"** e a aba **"Relatório de Posição"**.

No grid de dados é possível visualizar:
- Item – Descrição do item;
- Identificador – Código eletrônico (EPC) do item;
- Grupo – Grupo de produtos do item;
- Status – Status atual do item;
- Etapa – Etapa atual do item;
- Campos do produto – Uma coluna para cada campo do grupo de produtos marcado com a opção "Mostrar no grid", em ordem alfabética. Quando o item não tem valor no campo, é apresentado "-";
- Registro – Data e hora do último evento do item.

A linha **Total**, no final do grid, apresenta a soma dos campos numéricos dos itens da página.

**5.1.1 - Pesquisando itens**
- **Status** – Selecione um status no campo "Selecione um Status";
- **Etapa** – Selecione uma etapa no campo "Selecione uma Etapa";
- **Pesquisar** – Selecione onde pesquisar (Item, Grupo, Identificador ou um campo do produto) e informe o texto na caixa de pesquisa;
- **Mais Filtros** – Permite filtrar por período, pela data de **Registro**.

**5.1.2 - Consultando o ciclo de vida do item**
Para consultar o ciclo de vida de um item, localize-o na listagem, clique no botão **"Ações"** e selecione **"Ciclo de vida"**. A janela "Ciclo de Vida" apresenta os eventos do item, com as colunas:
- Data – Data e hora do evento;
- Local – Local do item no evento;
- Status – Status do item no evento;
- Etapa – Etapa do item no evento.

Selecione a opção **"Confirmar"** para fechar a janela.

**5.1.3 - Exportando o histórico**
Para exportar, selecione uma **Etapa**, execute o filtro e selecione a opção **"Exportar"**. Sem a etapa selecionada, é apresentada a mensagem "Selecione uma etapa e execute o filtro".

O arquivo é gerado no formato CSV, com o nome da etapa no nome do arquivo. O arquivo apresenta o grupo de produtos de cada item (coluna "Tipo"), os campos do produto e a data de registro.

### 5.2 - Histórico de Movimentação
A tela de Histórico de Movimentação apresenta as entradas e saídas de itens no estoque das empresas. Para acessar, selecione a opção **"Histórico e Relatórios"** e a aba **"Relatório de Movimentação"**.

No grid de dados é possível visualizar:
- Tipo – Entrada ou Saída;
- Data de Registro – Data e hora da movimentação;
- Origem – Empresa de origem;
- Destino – Empresa de destino;
- Embarque – Código do embarque da movimentação;
- Quantidade Esperada – Quantidade de itens esperados na movimentação;
- Quantidade Processada – Quantidade de itens movimentados.

As movimentações são apresentadas da mais recente para a mais antiga.

**5.2.1 - Pesquisando movimentações**
- **Empresa** – Selecione a empresa que será consultada. Este campo é apresentado somente para os usuários da empresa principal;
- **Tipo** – Selecione **"Entrada"** ou **"Saída"** no campo "Entrada ou Saída". Sem seleção, são apresentados os dois tipos;
- **Pesquisar** – Selecione onde pesquisar (Origem ou Destino) e informe o nome da empresa na caixa de pesquisa;
- **Mais Filtros** – Permite filtrar por período.

**5.2.2 - Visualizando os itens da movimentação**
Para visualizar os itens de uma movimentação, clique na seta no início da linha. São apresentados os itens movimentados, com a Descrição e a Quantidade de cada item.

Para visualizar os identificadores (EPCs) de um item, clique na seta no início da linha do item. Clique novamente na seta para ocultar os detalhes.

**5.2.3 - Exportando o histórico**
Selecione a opção **"Exportar"** para fazer o download da planilha com as movimentações filtradas. A planilha apresenta uma linha por item, com as colunas Tipo, Registro, Origem, Destino, Embarque, Qtd. Esperada, Qtd. Processada, Item e Identificador.

### 5.3 - Histórico de Conferência
A tela de Histórico de Conferência permite consultar as conferências realizadas e os resultados de cada uma. São apresentadas as atividades do tipo **"Conferência"** da empresa conectada, incluindo as conferências salvas pelo coletor (Conferência por Local).

Para acessar, selecione a opção **"Histórico e Relatórios"** e a aba **"Histórico de Conferência"**.

No grid de dados é possível visualizar:
- Local – Local onde a conferência foi realizada;
- Início – Data e hora de início da conferência;
- Conclusão – Data e hora de conclusão da conferência. Fica vazio quando a conferência não foi concluída;
- Status – Situação da conferência (Concluído, Liberado, Em execução, Rascunho, Cancelado, Abortado ou Erro).

As conferências são apresentadas da mais recente para a mais antiga.

**5.3.1 - Pesquisando conferências**
- **Pesquisar** – Informe o nome do local na caixa de pesquisa;
- **Status** – Selecione um status no campo de status. A opção "Todos os status" apresenta todas as conferências;
- **Mais Filtros** – Permite filtrar por período, pela data de **Início** ou de **Conclusão**, e alterar a ordenação (Início, Conclusão ou Local, em ordem A-Z ou Z-A) e a quantidade de registros por página.

**5.3.2 - Exportando o histórico**
Selecione a opção **"Exportar"** para fazer o download da planilha com as conferências filtradas. Além das colunas do grid, a planilha apresenta a quantidade de itens Conferidos, Ausentes e Divergentes de cada conferência.

**5.3.3 - Visualizando o detalhe da conferência**
Para visualizar o detalhe de uma conferência, localize-a na listagem, clique no botão **"Ações"** e selecione **"Visualizar"**.

O cabeçalho do detalhe apresenta o Local, o Modelo da atividade, o Status, o Início e a Conclusão da conferência.

Os indicadores apresentam:
- **Conferidos** – Itens esperados no local que foram lidos na conferência;
- **Ausentes** – Itens esperados no local que não foram lidos na conferência;
- **Divergentes** – Itens lidos na conferência que não eram esperados no local.

Abaixo dos indicadores é apresentada a lista de itens da conferência, com as colunas:
- Descrição – Descrição do item;
- EPC – Código eletrônico do item;
- Campos do produto – Uma coluna para cada campo do grupo de produtos marcado com a opção "Mostrar no grid", incluindo os campos herdados do grupo pai. Quando o item não tem valor no campo, é apresentado "-";
- Status – Conferido (verde), Ausente (vermelho) ou Divergente (amarelo).

A lista apresenta primeiro os itens Divergentes, depois os Ausentes e por último os Conferidos. Para filtrar a lista por um status, clique sobre o indicador desejado ou selecione o status no filtro da lista.

Selecione a opção **"Exportar"** para fazer o download da planilha com os itens da conferência, nas mesmas colunas da tela. Selecione a opção **"Voltar"** para retornar à listagem, com os filtros que estavam aplicados.

> Importante:
> - Os campos do produto apresentam os valores atuais do item, e não os valores do momento da conferência.
> - Só são apresentadas as conferências cujo modelo de atividade era do tipo "Conferência" no momento da criação.
> - Para ver a tela, o grupo do usuário precisa ter a permissão de leitura em "Histórico de Conferência" (tela Grupos).
