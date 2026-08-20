## 1. O BIOS/UEFI (O "Gerente de Abertura")

Pense no BIOS/UEFI como o gerente de uma loja que chega primeiro, acende as luzes e checa se todas as ferramentas estão funcionado antes de abrir as portas para os clientes.

* **O que é:** Um firmware (código de baixo nível) gravado direto em um chip da placa-mãe.
* **UEFI:** É a evolução moderna do BIOS antigo, trazendo interface gráfica, suporte a mouse, compatibilidade com discos maiores e mais segurança.

### As 4 Funções Principais:
1. **POST:** Assim que você liga o PC, ele testa se os componentes essenciais (RAM, Processador, Placa de Vídeo, Armazenamento) estão operando.
2. **Configuração de Hardware:** Permite ajustar parâmetros físicos (frequências, voltagens/overclock, perfis XMP de memória).
3. **Gerenciamento de Boot:** Identifica em qual disco (SSD/HD) ou pendrive está o sistema operacional e inicia o carregador de inicialização.
4. **Secure Boot:** Camada de segurança do UEFI que impede a execução de softwares maliciosos durante a inicialização.

---

## 2. A Passagem de Bastão (Como a CPU e o BIOS Conversam)

Este processo ocorre nos primeiros segundos após o botão de ligar ser pressionado:

1. **Ponto de Partida (Endereço Fixo):** Ao receber energia, a CPU zera seus registradores e busca instruções em um endereço fixo pré-programado na placa-mãe.
2. **Leitura Direta:** Como a memória RAM ainda não foi configurada, a CPU lê o código do BIOS/UEFI diretamente do chip usando seu relógio interno (*clock*).
3. **Entrega de Controle:** Após testar e configurar o hardware, o BIOS/UEFI encontra o sistema operacional (Windows/Linux), carrega os arquivos essenciais na RAM e passa o comando para a CPU executar o SO.

---

## 3. O Processador e o Sistema Operacional

### Como o Processador Funciona
O processador opera essencialmente como uma calculadora de altíssima velocidade:
* Processa dados em formato binário (`0` e `1`).
* **Fluxo de Trabalho:** Busca dados na memória RAM $\rightarrow$ Armazena em um **Registrador** (memória interna ultra-rápida) $\rightarrow$ Executa a operação lógica/aritmética $\rightarrow$ Devolve o resultado para a RAM.

---

### Como o Sistema Operacional Assume o Controle

Para gerenciar múltiplos programas sem que um interfira no outro, a CPU trabalha com **Modos de Execução**:

| Modo | O que roda aqui? | Nível de Acesso |
| :--- | :--- | :--- |
| **Modo Usuário** | Aplicativos comuns (Navegador, Jogos, Word) | **Restrito:** Não pode acessar o hardware diretamente. |
| **Modo Kernel** | Núcleo do Sistema Operacional | **Total:** Acesso irrestrito a todo o hardware. |

#### Mecanismos de Transição e Multitarefa:

* **Interrupção do Temporizador (*Timer Interrupt*):** Um chip envia um sinal elétrico periódico (ex: a cada 10ms) que obriga a CPU a pausar o programa atual e dar atenção ao Sistema Operacional.
* **Chamadas de Sistema (*System Calls*):** Quando um app precisa de algo do hardware (ex: ler um arquivo), ele faz uma solicitação (*syscall*) que força a CPU a trocar para o Modo Kernel.
* **Escalonador (*Scheduler*):** O SO salva o estado atual do programa na memória (**Bloco de Controle de Processo - PCB**), escolhe a próxima tarefa da fila e a carrega na CPU. Isso garante a ilusão de que vários programas rodam exatamente ao mesmo tempo.

