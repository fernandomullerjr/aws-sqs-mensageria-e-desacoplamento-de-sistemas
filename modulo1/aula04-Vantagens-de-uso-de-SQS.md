
# 04 - Vantagens de uso de SQS


Durante uma discussão, a implementação de uma funcionalidade de disparo de e-mails, a liderança sugeriu que, ao fim de toda compra no E-Commerce, todas as chamadas para o sistema de envio de e-mails fossem feitas utilizando o protocolo HTTP, pois, uma vez realizada com sucesso, pode-se ter a certeza de que os dados foram trafegados de maneira eficaz.

Maria Luíza, sugeriu, no entanto, que o uso de mensagerias poderia ser mais efetivo e gostaria de implementar esta funcionalidade utilizando o AWS SQS, pois julga que o envio de e-mails, apesar de importante, não é algo crítico para o funcionamento do sistema e poderia ser implementado assincronamente.

É correto afirmar que:

Mensagerias desacoplam os produtores dos consumidores, guardando, temporariamente, as mensagens. Assim, os consumidores podem consumi-las em seu próprio tempo e disponibilidade.


Alternativa correta! O grande benefício de mensagerias é o desacoplamento de sistemas. Os consumidores perguntam, de tempos em tempos, para o broker se existe alguma mensagem nova. Isso garante que, caso o consumidor esteja indisponível, a mensagem estará sã e salva no broker, aguardando para ser consumida, sendo essa, uma arquitetura tolerante a falhas de rede ou indisponibilidade de sistemas, encaixando-se com perfeição na funcionalidade de envio de e-mails.