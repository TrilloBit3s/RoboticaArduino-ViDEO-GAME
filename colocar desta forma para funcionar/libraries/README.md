# Arduino-TVout

Esta é uma biblioteca para gerar vídeo composto em um microcontrolador ATmega. Hospedado aqui para mantê-lo disponível no Arduino IDE (e para download simples, já que o Google Code original foi arquivado).

Este repositório é baseado na última versão publicada no Google Code, conhecida como Beta1. Ele foi corrigido para contornar problemas de compilação associados ao uso de macros de montagem em versões mais recentes do Arduino IDE. Os problemas de compilação com macros surgiram após o Arduino 1.6.8.

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

Atualmente, a saída é NTSC ou PAL em uma resolução de 128x96 por padrão. A biblioteca atualmente funciona em ATmega168,328,1280,2560,644p, 1284p, 32U4, AT90USB1286 e mais podem ser adicionados editando spec / hardware_setup.h.

Existem alguns problemas de temporização com o m1284p, podem estar relacionados ao núcleo sanguino.

MCU | SYNC | VIDEO | ÁUDIO | Arduino | SYNC | VIDEO | ÁUDIO
--- | --- | --- | --- | --- | --- | --- | ---
m168, m328 | B 1 | D 7 | B 3 | NG, Decimila, UNO | 9 7 11
m1280, m2560 | B 5 | A 7 | B 4 | Mega | 11 A7 (D29) | 10
m644, m1284p | D 5 | A 7 | D 7 | sanguino | 13 A7 (D24) | 8
m32u4 | B 5 | B 4 | B 7 | Leonardo | 9 8 11
AT90USB1286 | B 5 | F 7 | B 4 | - | - | - | -

## Conexões

SYNC está em OCR1A e AUDIO está em OCR2A (exceto no Arduino Leonardo, onde AUDIO está em OCR0A)

Existem alguns problemas de temporização com o m1284p, podem estar relacionados ao núcleo sanguino.

No NG, Decimila, UNO e Nano a sincronização é no pino 9, vídeo no 7 e áudio no 11. No Mega2560 a sincronização é no pino 11, o vídeo está no A7 (D29) e o áudio está no pino 10.