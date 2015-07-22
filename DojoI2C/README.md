O objetivo deste projeto � interligar em uma rede I2C v�rios Arduinos com o Garoa Dojo Shield para permitir a gera��o de anima��es coordenadas. 

https://garoa.net.br/wiki/DojoI2C

O objetivo da prova de conceito (feita em 11/12/14) foi demonstrar a capacidade de comunica��o via I2C entre Arduinos.

O hardware consistiu em tr�s Arduinos (um UNO, um DUEMILINOVE e um MEGA), cada um deles com um Garoa Dojo Shield. Al�m da interliga��o de SDA, SCL e GND, foram interligados o +5V, para que a alimenta��o de todos viesse da USB do mestre (conectado a um PC). Este esquema de alimenta��o deve ser inapropriado no caso de uma quantidade maiores de Arduinos.

O software carregado nos tr�s foi o mesmo. A defini��o do modo (Master ou Slave) e do endere�o (se slave) s�o armazenadas na EEProm. A configura��o � feita atrav�s da conex�o serial a um PC, por simplifica��o o endere�o � um d�gito de 1 a 9.

O formato das mensagens foi restringido a um byte. Na escrita do mestre, o byte controle os oito LEDs do display do escravo (sete segmentos mais o ponto decimal). Na leitura do mestre, o escravo informa a leitura do potenci�metro (dividida por 4 para ficar de 0 a 255). A expans�o destas mensagens para controlar mais sinais de sa�da e ler mais entrada (como o LDR no shield) � trivial e fica como exerc�cio para os implementadores futuros.

Como teste, o mestre comanda o display dos escravos (e o seu pr�prio) com o valor lido do seu potenci�metro (tamb�m dividido por quatro) e envia pela serial a leitura dos potenci�metros dos escravos. 

