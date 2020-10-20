# Binários para fazer o Build do NuttX pro ESP32

## Como usá-los 

Acesse o repositório do Nuttx previamente clonado
 `cd ~/nuttxspace/nuttx`
e faça o download do bootloader de segundo estágio e da tabela de partição:

`wget XXX`

`wget XXX`

## Como gerá-los

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
  
3. Ative o ambiente virtual.

`. $HOME/esp/esp-idf/export.sh`

3. Desabilite o RTC 

 * Execute `make menuconfig` para acessar o menu de configuração.
 * Acesse *Bootloader Config -> * 

4. Faça o build para obter os binários.

`make`

5. Copie os binários gerados para o diretório do NuttX.

`cp build/bootloader/bootloader.bin ~/nuttxspace/nuttx/`

`cp build/partitions_singleapp.bin ~/nuttxspace/nuttx/partitions.bin`

Pronto, agora você já tem tudo que precisa da IDF e pode continuar com o processo de build do NuttX!


