## Onde entram os drivers e gerenciadores de recursos
 O papel dos drivers no Processador:
 Os drivers são programas que contêm instruções específicas para a CPU conversar com os componentes de hadware(placa de video, disco, rede). Quando um programa precisa usar o hadware, a CPU executa o código do driver, após o driver traduz ordens gerais do sistema em comandos diretos que o chip do dispositivo entende.

O papel dos gerenciadores de Recursos:
 O gerenciador de recursos(parte do núcleo ou kemel do sistema operacional) decide quando e quanto tempo cada processo fica na CPU. Ele utiliza um componente chamado escalanador(scheduler) para alternar rapidamente entre tarefas, dando a impressão de que tudo roda ao mesmo tempo. O gerenciador de memória configura a unidade de gerenciamento de memória(MMU) para definir quais dados vão para a memória física ou cache do processador.

 Como eles entram em ação
 Modo Núcleo/ Kernel, é o nivel mais acessado ao hadware. Os drivers e o gerenciador de recursos do sistema operacional(como o escalonador de processos e o gerenciador de memória) rodam nesse modo. Eles dão ordens diretas aos circuitos do computador. Já no modo usuário é onde rodam seus aplicativos padrões como o próprio navegador, jogos, editor de texto. Eles não tem acesso direto ao hadware e precisam pedir licença aos drivers e ao sistema.

 ## Função do driver e Gerenciador de recursos
 Gerenciador de recursos: Funcionam como uma "chefia", onde se comunicam com o processador quais tarefas executar em cada núcleo, quanto tempo cada aplicativo pode usar o processador e com a memória RAM deve ser dividida.

 Drivers: Funcioanam como um locutor ou seja se um programa quer impremir um documento, ele avisa o sistema operacional. O driver de impressão traduz esse pedido em instruções binárias e utiliza o processador para enviar os comandos de sinal elétrico corretos para a impressora.

## Papel dos barramentos e dispositivos de E/S nesse processo
 Barramentos: De forma geral os barramentos são responsáveis pela interligação e comunicação dos dispositivos em um computador. Note que, para o processador se comunicar com a memória e o conjunto de dispositivos de entrada e saída, há três setas, isto é, barramento: Um sendo chamado barramento de endereçoes, barramento de dados e barramento de controle. Como o nome deixa claro, é pelo barramento de dados que as informações trafegam. Por sua vez, o barramento de controle faz a sincronização das referidas atividades, habilitando ou desabilitando o fluxo de dados, por exemplo. Imagine que o processador necessita de um dado presente na memória. Pelo barramento de endereços(indica onde os dados processados devem ser retirados ou para onde são enviados), a CPU obtém a localização deste dado dentro da memória. Como precisa apenas acessar o dado, o processador indica pelo barramento de controle que esta é uma operação de leitura. O dado então  é  localizado e inserido no barramento de dados, por onde o processador finalmente, o lê.

 Dispositivos de E/S
 Entrada de dados: Facilita a recepção de dados vindo de dispositivos externos. Isso inclui teclado, mause sensores ou qualquer outro dispositivo de entrada.
 
 Saída de dados: Possibilita a transmissão de dados processados para dispositivos externos como monitores, impressoras denytre outros dispositivos de saida.
 
 A E/S coordena o controle e a comunição com dispositivos periféricos, garantindo que os dados sejam transferidos corretamente entre o computador e esses dispositivos. Ela se utiliza de interfaces específicas para se interagir com diferentes tipos de dispositivos. Por exemplo: dispositivos de armazenamento podem se comunicar através de interfaces como SATA  ou USB, enquanto alguns utilizam Ethernet ou WI-FI. Para lidar com a comunicação não simultânea entre o processador e os dispositivos externos , a E/S muitas vezes faz um uso de mecanismo de interrupção, permitindo com que os dispositivos externos notifiquem o processador sobre eventos significativos, como a conclusão de uma operação de leitura ou gravação. Ela pode envolver controladores específicos para gerenciar diferentes categorias de dispositivos. Esses controladores traduzem comandos para a  CPU em operações compreensíveis para os dispositivos, ajustando a comunicação. 

