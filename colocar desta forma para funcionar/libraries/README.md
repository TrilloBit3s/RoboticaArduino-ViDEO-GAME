# Arduino-TVout

Esta � uma biblioteca para gerar v�deo composto em um microcontrolador ATmega. Hospedado aqui para mant�-lo dispon�vel no Arduino IDE (e para download simples, j� que o Google Code original foi arquivado).

Este reposit�rio � baseado na �ltima vers�o publicada no Google Code, conhecida como Beta1. Ele foi corrigido para contornar problemas de compila��o associados ao uso de macros de montagem em vers�es mais recentes do Arduino IDE. Os problemas de compila��o com macros surgiram ap�s o Arduino 1.6.8.

Instale as 3 bibliotecas em seu caderno de desenho Arduino com a seguinte estrutura:

`` `
Caderno de desenho Arduino
    |
    + - bibliotecas
          |
          + - TVout
          | |
          | + --...
          |
          + - TVoutfonts
          | |
          | + --...
          |
          + - pollserial
                |
                + --...
`` `

Atualmente, a sa�da � NTSC ou PAL em uma resolu��o de 128x96 por padr�o. A biblioteca atualmente funciona em ATmega168,328,1280,2560,644p, 1284p, 32U4, AT90USB1286 e mais podem ser adicionados editando spec / hardware_setup.h.

Existem alguns problemas de temporiza��o com o m1284p, podem estar relacionados ao n�cleo sanguino.

MCU | SYNC | VIDEO | �UDIO | Arduino | SYNC | VIDEO | �UDIO
--- | --- | --- | --- | --- | --- | --- | ---
m168, m328 | B 1 | D 7 | B 3 | NG, Decimila, UNO | 9 7 11
m1280, m2560 | B 5 | A 7 | B 4 | Mega | 11 A7 (D29) | 10
m644, m1284p | D 5 | A 7 | D 7 | sanguino | 13 A7 (D24) | 8
m32u4 | B 5 | B 4 | B 7 | Leonardo | 9 8 11
AT90USB1286 | B 5 | F 7 | B 4 | - | - | - | -

## Conex�es

SYNC est� em OCR1A e AUDIO est� em OCR2A (exceto no Arduino Leonardo, onde AUDIO est� em OCR0A)

Existem alguns problemas de temporiza��o com o m1284p, podem estar relacionados ao n�cleo sanguino.

No NG, Decimila, UNO e Nano a sincroniza��o � no pino 9, v�deo no 7 e �udio no 11. No Mega2560 a sincroniza��o � no pino 11, o v�deo est� no A7 (D29) e o �udio est� no pino 10.