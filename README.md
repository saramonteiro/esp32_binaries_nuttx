ENGLISH
--------------------------------------------------------------------------------------------------------------

# Binaries to Build NuttX for ESP32

## How to use ready-made binaries

Access the previously cloned Nuttx repository
 `cd ~/nuttxspace/nuttx`
and download the second stage bootloader and the partition table:

`wget https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/bootloader.bin`

`wget https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/partitions.bin`

  
## How to generate binaries

1. Install the latest and **stable** version of ESP-IDF:

   * Install from Espressif's official tutorial: [Getting Started with ESP-IDF](https://docs.espressif.com/projects/esp-idf/en/stable/get-started/index.html).
  
   * Or install via a makefile embedded into NuttX:
  
  `cd ~/nuttxspace/nuttx`
  
  `make -C tools/esp32/ ${HOME}/esp/esp-idf`

2. Copy an example (hello-world) out of the IDF directory.

  * Access the directory where the IDF was installed:
 
 `cd ${HOME}/esp`
 
 * Copy the example.

 `cp -r ${HOME}/esp/esp-idf/examples/get-started/hello_world .`
 
 * Enter the example directory.
 
  `cd hello_world`
  
3. Disable RTC

 * To run the makefile, you must have the IDF virtual environment enabled. Run the following command to activate it:
 
 `. $HOME/esp/esp-idf/export.sh`
 
 * Run `make menuconfig` to access the configuration menu.
 
 * Access Bootloader Config -> Use RTC Watchdog in start code and click `N` to disable.
 
 ![Select Boot Config](https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/bootconfig.png)
 
 ![Disable the watchdog RTC in the initialization code](https://github.com/saramonteiro/esp32_binaries_nuttx/blob/main/rtcdisable.png)
 
 Save the configuration and go on!

4. Build it to get the binaries.

`idf.py build`

5. Copy the generated binaries to the NuttX directory.

`cp build/bootloader/bootloader.bin ~/nuttxspace/nuttx/`

`cp build/partition-table/partition-table.bin ~/nuttxspace/nuttx/partitions.bin`

Okay, now you have everything you need from IDF and you can continue with the NuttX build process!

PORTUGUÊS
--------------------------------------------------------------------------------------------------------------

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

`idf.py build`

5. Copie os binários gerados para o diretório do NuttX.

`cp build/bootloader/bootloader.bin ~/nuttxspace/nuttx/`

`cp build/partition-table/partition-table.bin ~/nuttxspace/nuttx/partitions.bin`

Pronto, agora você já tem tudo que precisa do IDF e pode continuar com o processo de build do NuttX!


