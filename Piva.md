# BIOS

O BIOS/UEFI é o firmware de baixo nível gravado na placa-mãe. Sua função principal é preparar o hardware, testar componentes (POST) e inicializar o sistema operacional. O UEFI é a evolução moderna do BIOS, trazendo interface gráfica, suporte a mouse, mais segurança e discos rígidos gigantescos

# Funções principais do BIOS/UEFI

POST: Ao ligar o pc, ele testa componentes essenciais como memória RAM, processador, placa de vídeo e armazenamento para se certificar que estão operando corretamente.

Configuração de Hardware: Permite alterar parâmetros físicos antes do sistema operacional carregar, como frequências, voltagens (overclocking) e perfis de memória (XMP).

Gerenciamento de Boot: Identifica em qual disco (SSD/HD) ou pendrive está o sistema operacional e inicia o carregador de inicialização (boot loader).

Segurança de Inicialização (Secure Boot): Exclusivo do UEFI, impede a execução de códigos não autorizados ou maliciosos durante o processo de boot.

# Como o processador e o BIOS/UEFI se comunicam

A conversa entre a CPU e o firmware não é igual à comunicação com um software comum no Windows, pois o sistema operacional ainda não foi carregado. Essa comunicação ocorre de forma muito estruturada:

. Ponto de partida (Endereço Fixo): quando o computador está energizado, a CPU zera seus registradores e busca intruções em um endereço de memória fixo e pré-programado

. Leitura Direta: O processador começa a ler e executar as instruções passo a passo diretamente do chip do firmware. Como a memória RAM ainda não foi testada nem configurada, o processador lê esses dados com base em seu próprio relógio interno e nas velocidades padrão da placa-mãe

# Comunicação via Barramento e Portas

Ao ligar o computador, o BIOS/UEFI verifica os principais componentes de hardware, como processador, RAM e placa de vídeo, usando os barramentos da placa-mãe. Se estiverem funcionando corretamente, o sistema continua a inicialização. A memória CMOS armazena configurações do BIOS/UEFI, como data, hora e algumas configurações de hardware.

# Entrega de Controle

Depois de configurar o hardware, o BIOS/UEFI procura um dispositivo de armazenamento válido e encontra o *arquivo de inicialização do sistema operacional. Ele carrega esse arquivo na **memória RAM* e passa o controle do computador para o *sistema operacional*, que continua o processo de inicialização.


# Processador

O processador opera como se fosse uma calculadora: ele recebe os dados por meio de um código binário — formado por 0 e 1 —, processa, armazena e distribui esse volume de informações tendo como base as instruções presentes na sua memória interna. Quanto mais sofisticado o processador for, mais funções conseguirá desempenhar e com maior velocidade.

Seu funcionamento é complexo, mas pode ser descrito assim: o processador busca na Memória de Acesso Aleatório (RAM) os números, que são guardados em um registrador especial para operações aritméticas. Em seguida, procura mais um número presente na memória RAM e faz o mesmo caminho. Ambos os números são somados e processados, retornando para a memória RAM.

## O que acontece quando o sistema operacional asssume o controle do processador?

O sistema operacional (SO) assume o controle do processador através de interrupções e do mecanismo de mudança de modo de execução (Modo Usuário para Modo Kernel). Esse processo é o que permite a um SO multitarefa "pausar" um programa e dar vez a outro de forma imperceptível.

Para entender o melhor o funcionamento das transições, é essencial observar os seguintes mecanismos:

. Modos de Execução da CPU: O processador opera em dois níveis de privilégio: o Modo Usuário (onde rodam os aplicativos, com acesso restrito ao hardware) e o Modo Kernel/Sistema (onde o SO tem controle total e acesso irrestrito).

. Interrupção do Temporizador (Timer Interrupt): Um chip de hardware externo envia sinais elétricos em intervalos regulares (ex: a cada 10 milissegundos). Quando a CPU recebe esse sinal, ela suspende o programa atual e transfere o controle para o kernel do SO

. Chamadas de Sistema (System Calls): Quando um aplicativo precisa ler um arquivo ou acessar a internet, ele gera uma "interrupção de software" (instrução syscall). Isso força a CPU a chavear para o Modo Kernel, transferindo o controle para o sistema operacional processar a requisição.

. Escalonamento (Scheduler): Uma vez que o controle está com o kernel, o sistema operacional salva o estado do programa anterior na memória (Bloco de Controle de Processo - PCB), escolhe a próxima tarefa na fila e a carrega para execução na CPUs