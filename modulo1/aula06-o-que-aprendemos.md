# 06 - O que aprendemos?
 
Nesta aula, aprendemos:

O SQS – Simple Queue Service – É o serviço de mensageria da AWS e, nele, podemos enviar e receber mensagens sem provisionar nenhum servidor. Este modelo é altamente escalável e confiável, pois é a própria AWS que cuida da disponibilidade deste serviço.
Vimos a importância do desacoplamento de sistemas, em que os consumidores processam mensagens em sua própria disponibilidade e necessidade.
Analisamos as vantagens de chamadas assíncronas, que são tolerantes a falhas de rede ou indisponibilidade de sistemas. Chamadas síncronas, por outro lado, exigem 100% de disponibilidade do sistema que está sendo chamado, o que é algo muito difícil (se não impossível) de se atingir quando desenvolvemos na nuvem.
Por último, abrimos o console da AWS, selecionamos uma região, buscamos pelo serviço SQS, criamos uma fila e testamos o envio e recebimento de mensagens.