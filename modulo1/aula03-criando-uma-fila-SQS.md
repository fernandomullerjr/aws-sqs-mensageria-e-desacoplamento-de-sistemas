
# 03 - Criando uma fila SQS

Transcrição
[00:00] Agora que entendemos os benefícios principais da utilização do sistema de mensageria, vamos finalmente criar nossa primeira fila na AWS. Se você está empolgado, está interessado, está curioso, vem comigo que vamos desbravar isso neste momento.

[00:20] O primeiro passo a fazer é decidir qual região iremos trabalhar. No console da Amazon, no canto superior direito, você pode clicar na região, no meu caso North Virginia, ou Virginia do Norte, e ver todas as regiões disponíveis pelo AWS.

[00:38] No curso utilizaremos North Virginia porque é uma região que todas as funcionalidades novas são primeiro criadas lá e depois dos testes com sucesso distribuídas para outras regiões. Porém, para o conteúdo do curso, nada impede que você escolha outra região, inclusive você pode escolher o datacenter de São Paulo sem problema nenhum.

[01:02] Eu, por força do hábito, escolherei North Virginia. O segundo passo a fazer é buscar o sistema que vamos utilizar, no caso o sqs ou sistema de fila simples, da Amazon. Temos algumas maneiras de buscar esse serviço. No centro da tela temos o menu de find services, podemos clicar nele e digitar sqs, que é o acrônimo, e veremos que o simples queue service aparece.

[01:33] Uma outra opção, no canto superior esquerdo da tela, clicar em services e também digitar sqs. Ambas as opções são válidas e fica a seu critério qual você achar mais fácil.

[01:44] Clicando em simple service somos levados ao console da sqs da Amazon e podemos clicar em create queue, ou seja, criar fila. Todas as configurações que usaremos neste momento são as configurações padrão, inclusive o tipo da fila, que é a fila standard, ou seja, fila padrão.

[02:06] Em um futuro também exploraremos filas FIFO. O próximo passo é dar um nome para a nossa fila. Eu vou chamar nossa fila de Alura-test. Temos também as configurações, vou deixar novamente todas as configurações padrão e vou até o fim da tela clicar em create queue, criar fila.

[02:32] A fila é muito rápida para ser criada, só leva um ou dois segundos. Vou tirar as mensagens do topo da minha tela, e temos nossa primeira fila criada. Temos os metadados da nossa fila, o nome, o tipo da fila, uma url de conexão que usaremos no futuro, e entre outras coisas.

[02:58] A primeira coisa que faremos, no entanto, é enviar uma mensagem para nossa fila, afinal criamos uma fila e queremos enviar mensagens para ela. No canto direito superior temos o send and receive message, ou seja, enviar e receber mensagens. Vou clicar neste botão, e somos deparados com algumas configurações para o envio desta mensagem.

[03:22] No caso, com o message body, o corpo da mensagem. Ou seja, o que efetivamente iremos enviar para o sqs. No mundo de TI, no mundo de desenvolvimento é muito comum criarmos o famoso “olá, mundo”, e faremos a mesma coisa com a mensagem sqs.

[03:42] Vou digitar aqui “olá, mundo”, e vou clicar em send message, não vou mexer em nenhuma outra configuração. Clicado em send message, vemos que nossa mensagem foi enviada e está pronta para ser recebida.

[03:58] Clicando em ver os detalhes desta mensagem vemos que ela foi atribuída a um id, ou seja, internamente a Amazon gravou esta mensagem, e temos até o corpo dela codificado em md5.

[04:12] Fechando este pop-up podemos então fechar esse trecho e descer até poll for message, que é a busca por mensagens. Ou seja, ver se nossa mensagem realmente está na fila. Temos uma dica no messages available, que diz “você tem mensagens disponíveis”, no caso uma, mas queremos ter certeza disso.

[04:38] Então, no canto direito da tela, no poll for messages, vou clicar neste botão e vejo aqui que a seção de messages foi populada com uma mensagem. Clicando nesta mensagem vemos o trecho que contém o corpo dela, ou seja, o “olá, mundo”, então nossa mensagem foi recebida com sucesso.

[05:05] O que podemos fazer agora é fechar esse pop-up e até excluir essa mensagem. Ou seja, criamos a mensagem, lemos a mensagem, agora vamos exclui-la. Vou clicar em delete e confirmar a deleção.

[05:20] Voltando para o menu de filas, no canto superior esquerdo temos nossa fila Alura-test e nenhuma mensagem disponível porque acabamos de deletar. Ou seja, nessa aula conseguimos criar uma fila na nuvem, enviamos uma mensagem, lemos essa mensagem e finalmente excluímos essa mensagem para não ficar com nenhuma mensagem deixada para trás.