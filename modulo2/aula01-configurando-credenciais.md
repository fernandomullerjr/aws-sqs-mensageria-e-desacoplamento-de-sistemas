# 01 - Configurando credenciais

# Transcrição

[00:00] Já criamos nossa fila no AWS, já mandamos e recebemos mensagens, já excluímos mensagens, mas tudo através do console web. Seria interessante começarmos também a trabalhar com a linha de comando. E por que seria interessante trabalhar com a linha de comando?

[00:18] Quando você está fazendo acesso a um servidor remoto, a algum servidor que não possui interface gráfica, você só vai ter acesso à linha de comando, então você precisa saber executar alguns comandos a fim de debug, trouble shooting, outras coisas.

[00:30] Então, muito útil para a área de DevOps e até para desenvolvimento mesmo. O primeiro passo é criar um usuário na conta do AWS para que seja essa ponte entre a nossa máquina de desenvolvimento local e o ambiente da nuvem. Como fazemos isso?

[00:50] Vamos buscar por um serviço, dessa vez chamado por IAM, que é o serviço de gerenciamento de identidade de acesso. Dentro do serviço de IAM vamos clicar em users, no canto esquerdo, e adicionar um usuário, no topo, no botão azul.

[01:07] Qual o nome do usuário? Eu vou dar o nome do usuário de Alura-sqs, mas você pode dar o nome que você quiser. No tipo de acesso precisamos colocar somente acesso programático. Por que acesso programático? O que isso significa? Significa que esse usuário só vai ter acesso de chamadas de API, via aplicações, ou linha de comando.

[01:30] Esse usuário não vai ter acesso à interface gráfica da web, como temos com usuário de administrador. O próximo passo é clicar em permissões e vou clicar no terceiro item do grupo de permissões. Vou selecionar para anexar as políticas de acesso diretamente.

[01:47] Vou digitar SQSFullAccess, selecionar essa política, clicar em próximo para buscar as tags. Não vou adicionar nenhuma tag. Finalmente vou para a página de revisão. Vou criar o usuário, e vou ser apresentado com o access key id e o secret access key, que são as chaves de acesso e a senha, basicamente, desse usuário.

[02:12] Essa informação só é mostrada no console web uma vez, então se você quiser acesso permanente você vai precisar clicar em download csv. O que vamos fazer com as chaves? Vamos usar essas chaves na linha de comando. Como configuramos a linha de comando?

[02:25] A documentação do AWS é muito bem definida, como fazemos isso? Na documentação oficial, no AWS CLI, que é o nome do client da linha de comando, você tem instalação para Linux, para MacOS, para Windows e até para docker, caso você esteja fazendo este curso no docker.

[02:48] Qual o próximo passo? Pegar essas credenciais, ir para a linha de comando com o AWS CLI instalado e executar alguns comandos. Se você tiver qualquer dúvida em como instalar o AWS CLI é só mandar uma mensagem que você será ajudado.

[03:05] Indo para a linha de comando então, vou digitar ‘AWS help’, e esse comando é só para saber se o client da AWS foi instalado com sucesso. Temos o AWS help e vimos um monte de informação. Ou seja, está instalado. Se você ver algo como AWS comando não reconhecido, ou algo do gênero, é porque não funcionou a instalação, sugiro que você ou deixe sua dúvida ou revisite a documentação.

[03:33] Feito isso, o próximo passo é copiar o access key id. Copio o access key id e vou digitar AWS configure, de configuração. Configurar. Vou colar esse access key id e vou também copiar os access key desta vez, que é a segunda informação perguntada.

[03:52] Colei o access key, a outra pergunta é qual região queremos trabalhar. A região padrão é norte Virgínia, us east 1, então vou deixar o enter, e o formato que queremos ver quando fizemos a chamada de API, vou deixar JSON. Provavelmente o seu vai estar none, então sugiro que você coloque JSON para ficar com uma visualização um pouco mais bonita.

[04:15] Feito isso precisamos testar se isso de fato funciona. Como podemos testar os comandos para conectar no AWS sqs? Podemos digitar AWS sqs help, essa é até uma maneira de se você não souber utilizar API, utilizar o comando, você pode digitar AWS sqs help que a documentação é muito boa.

[04:36] Vou começar a apertar enter e ver quais são as chamadas que posso fazer para o console do AWS. Vou dar enter e vejo que tenho os comandos disponíveis, depois de apertar enter uma vez vejo os comandos disponíveis. Em qual estamos interessados?

[04:55] Neste momento, esse list-queues parece muito interessante, porque criamos uma fila no AWS, gostaríamos de ver se ela de fato está disponível via linha de comando.

[05:05] No meu editor vou apertar q, pode ser que seu editor seja uma chave diferente para apertar. No meu caso estou usando o Vim então aperto q para sair da documentação, e vou digitar o seguinte agora AWS sqs list-queues, que foi o comando disponibilizado pelo próprio client.

[05:30] Dou enter. Vejo a resposta em JSON, no formato que eu tinha escolhido, que temos os queueUrls, ou seja, as URLs das filas que temos criadas no AWS. No caso, temos aqui sqs Alura-test na região us east 1.

[05:50] Para testar se isso realmente funciona, só para você ter certeza absoluta, vou rodar o AWS configure novamente e vou colocar qualquer coisa no lugar do access key id, e no secret access key. Se eu fizer essa requisição novamente para o console da AWS tenho que receber uma mensagem de acesso inválido, acesso negado, token inválido, ou alguma coisa do gênero.

[06:15] Se eu executar o comando AWS sqs list-queues novamente, vou ficar com uma tela preta, veja que as filas já não apareceram. Se eu apertar q agora vejo a mensagem dizendo que um erro ocorreu, que o token de segurança incluído na requisição é inválido.

[06:34] Para você configurar o usuário no AWS é só seguir esses passos, configura o access key id e o secret access key e está tudo feito, estamos prontos para começar a usar a linha de comando.