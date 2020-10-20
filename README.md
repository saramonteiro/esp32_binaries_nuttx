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
  
  `make -C tools/esp32/ ${IDF_PATH}`

2. Copie um exemplo (hello-world) para fora do diretório da IDF.

3. Desabilite o RTC 

3. Faça o build para obter os binários.
