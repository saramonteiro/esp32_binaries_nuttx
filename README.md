# Binários para fazer o Build do NuttX pro ESP32

## Como usar os binários prontos 

Acesse o repositório do Nuttx previamente clonado
 `cd ~/nuttxspace/nuttx`
e faça o download do bootloader de segundo estágio e da tabela de partição:

`wget https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/bootloader.bin`

`wget https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/partitions.bin`


## Como gerar os binários

1. Instale a versão mais atual e **estável** do ESP-IDF:

  * Instale a partir do tutorial oficial da Espressif: [Getting Started with ESP-IDF](https://docs.espressif.com/projects/esp-idf/en/stable/get-started/index.html).
  
  * Ou instale através de um makefile embutido no NuttX:
  
  `cd ~/nuttxspace/nuttx`
  
  `make -C tools/esp32/ ${HOME}/esp/esp-idf`

2. Copie um exemplo (hello-world) para fora do diretório da IDF.

 * Acesse o diretório no qual o IDF foi instalado:
 
 `cd ${HOME}/esp`
 
 * Copie o exemplo.

 `cp -r ${HOME}/esp/esp-idf/examples/get-started/hello_world .`
 
 * Entre no diretório do exemplo.
 
  `cd hello_world`
  
3. Desabilite o RTC 

 * Para executar o makefile, é necessário estar com o ambiente virtual do IDF instalado. Execute o seguinte comando para ativá-lo:
 `. $HOME/esp/esp-idf/export.sh`
 * Execute `make menuconfig` para acessar o menu de configuração.
 * Acesse Bootloader Config -> Use RTC Watchdog in start code e clique em `N` para desabilitar.
 
 ![Selecione Boot Config](https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/bootconfig.png)
 
 ![Desabilite o watchdog RTC no código de inicialização](https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/rtcdisable.png)
 
 Salve a configuração e continue!

4. Faça o build para obter os binários.

`make`

5. Copie os binários gerados para o diretório do NuttX.

`cp build/bootloader/bootloader.bin ~/nuttxspace/nuttx/`

`cp build/partitions_singleapp.bin ~/nuttxspace/nuttx/partitions.bin`

Pronto, agora você já tem tudo que precisa da IDF e pode continuar com o processo de build do NuttX!


