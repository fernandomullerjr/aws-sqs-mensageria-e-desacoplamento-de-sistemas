
# 02 - O que é SQS

Transcrição
[00:00] Olá, se você tem interesse em saber como sistemas de mensageria funcionam na prática e a segurança que eles podem dar para as nossas aplicações, vem comigo que vou explicar tudo neste vídeo.

[00:12] Imaginemos que temos um sistema A, que pode ser um sistema de transações financeiras, um banco, ou qualquer coisa do gênero, e ele precisa se comunicar com outro sistema, esse sistema vamos chamar de sistema B, que pode ser, por exemplo, o Banco Central.

[00:28] No Brasil, toda transação financeira precisa ser efetivada no Banco Central, e como essa comunicação poderia acontecer? Imagine que você tem um banco e precisa mandar uma mensagem para o Banco Central falando “eu tenho uma nova transação financeira e eu quero gravar essa transação financeira junto a vocês, quais são as maneiras de fazer isso?”.

[00:48] Existem várias maneiras, mas neste vídeo abordaremos duas. A primeira delas é comunicação síncrona. Imagine que o sistema A faça uma chamada http para o sistema B, essa chamada pode ser uma chamada rest, pode ser uma chamada soap, e o sistema B falha, o Banco Central não está disponível no momento da chamada.

[01:08] Por que o Banco Central não estaria disponível? Um dos motivos é que quando estamos fazendo sistemas de rede nunca podemos confiar na rede. A rede não é confiável. Pode haver perda de pacotes, o client pode simplesmente perder a conexão, a internet pode de fato cair. Então, não podemos confiar na rede.

[01:33] O outro ponto é indisponibilidade no servidor, neste caso indisponibilidade no sistema B, então imagine que é começo do mês, todo mundo recebeu dinheiro e tem um monte de transações acontecendo no mesmo momento, onerou o sistema do Banco Central. O Banco Central ou vai responder muito demoradamente, com a latência muito alta, ou pode de fato ficar indisponível.

[01:52] E aí todo o tratamento de retentativa teria que ficar no sistema A. Ou seja, no próprio banco, ficar de tempos em tempos chamando Banco Central e falando “você está disponível? Você está disponível?”, até que conseguisse de fato efetuar a entrega desta mensagem.

[02:10] Isso acaba não sendo muito efetivo, porque onera o sistema A que tem que ficar tendo muita retentativa e pode ser que o sistema B demore muito tempo para voltar, então não é confiável.

[02:20] Como podemos resolver isso? Podemos resolver isso com uma comunicação assíncrona, onde o sistema A coloca uma mensagem em uma mensageria, em um broker, ou no nosso caso do curso, no sqs, o serviço de fila simples da Amazon.

[02:37] O que acontece então? O sistema B, quando disponível, pergunta para a mensageria se há mensagens novas, e se tiver a mensageria entrega essa mensagem e o sistema B processa de acordo, seja para gravar no banco, em um arquivo, ou qualquer que for que seja a execução que ele necessite fazer.

[02:55] Olhando por essa perspectiva, as vantagens são que a mensagem fica salva no broker, então não tem problema se a internet do sistema B não está funcionando ou o sistema B não está disponível. Isso gera uma tolerância a indisponibilidades. Não tem problema se o sistema B ficar fora por uma, duas, três horas ou até por alguns dias, pois a mensagem vai ficar salva temporariamente aqui no broker.

[03:22] Existe um limite, exploraremos esse limite ao longo do curso, mas é um limite alto, estamos falando de duas semanas de limite. Então, isso dá muita resiliência para nossas aplicações, porque tudo que precisamos é que o sistema A entregue a mensagem com sucesso para a mensageria.

[03:40] Trazendo isso para um caso real, para um caso de uso da nossa vida mesmo, qual seria um exemplo mais próximo? Seria o exemplo onde temos um remetente. Você quer entregar uma mensagem para um colega, para uma colega, e você pega um envelope, lacra, escreve seu texto e deixa na caixa de correio dessa pessoa.

[04:00] Essa pessoa pode ou não estar em casa no momento do recebimento, mas você, como remetente, fez o papel de deixar a mensagem em um local seguro. O destinatário, se não estiver em casa ou quando estiver em casa e checar a caixa de correio vai ver que tem uma mensagem, então de fato essa comunicação vai ter sido executada com sucesso, quando o destinatário pegar na caixa de correio a mensagem que foi entregue mais cedo.

[04:28] Agora imagine se a comunicação fosse síncrona. O remetente chega na casa do destinatário, o destinatário não está, está no trabalho, no médico, está fazendo alguma outra coisa. O remetente tem que voltar e tentar em outro momento. Seria muito cansativo e oneroso para o remetente.

[04:47] Dessa maneira, com uma comunicação assíncrona garantimos que a mensagem seja entregue, seja na hora ou em um momento posterior.