# Projeto de Controle de Joystick com RP2040

## 🎯 Objetivos

- Compreender o funcionamento do conversor analógico-digital (ADC) no RP2040.
- Utilizar o PWM para controlar a intensidade de dois LEDs RGB com base nos valores do joystick.
- Representar a posição do joystick no display SSD1306 por meio de um quadrado móvel.
- Aplicar o protocolo de comunicação I2C na integração com o display.

## 📜 Descrição do Projeto

O joystick fornecerá valores analógicos correspondentes aos eixos X e Y, que serão utilizados para:

### Controle de LEDs RGB

- **LED Azul**: O brilho será ajustado conforme o valor do eixo Y. Quando o joystick estiver na posição central (valor 2048), o LED permanecerá apagado. Movendo o joystick para cima (valores menores) ou para baixo (valores maiores), o LED aumentará seu brilho gradualmente, atingindo a intensidade máxima nos extremos (0 e 4095).
- **LED Vermelho**: O brilho será ajustado conforme o valor do eixo X. Quando o joystick estiver na posição central (valor 2048), o LED estará apagado. Movendo o joystick para a esquerda (valores menores) ou para a direita (valores maiores), o LED aumentará de brilho, sendo mais intenso nos extremos (0 e 4095).
- Os LEDs serão controlados via PWM para permitir variação suave da intensidade luminosa.

### Display SSD1306

- Exibir um quadrado de 8x8 pixels, inicialmente centralizado, que se moverá proporcionalmente aos valores capturados pelo joystick.

### Botão do Joystick

- Alternar o estado do LED Verde a cada acionamento.
- Modificar a borda do display para indicar quando foi pressionado, alternando entre diferentes estilos de borda a cada novo acionamento.

### Botão A

- Ativar ou desativar os LEDs PWM a cada acionamento.

## 🛠️ Componentes Utilizados

- LED RGB, com os pinos conectados às GPIOs (11, 12 e 13).
- Botão do Joystick conectado à GPIO 22.
- Joystick conectado aos GPIOs 26 e 27.
- Botão A conectado à GPIO 5.
- Display SSD1306 conectado via I2C (GPIO 14 e GPIO 15).

## 📋 Requisitos do Projeto

1. **Uso de Interrupções**: Todas as funcionalidades relacionadas aos botões devem ser implementadas utilizando rotinas de interrupção (IRQ).
2. **Debouncing**: Implementar o tratamento do bouncing dos botões via software.
3. **Utilização do Display 128 x 64**: Demonstrar o entendimento do princípio de funcionamento do display, bem como a utilização do protocolo I2C.
4. **Organização do Código**: O código deve estar bem estruturado e comentado para facilitar o entendimento.

## 🚀 Como Executar

1. Clone este repositório.
2. Configure o ambiente de desenvolvimento para RP2040.
3. Conecte os componentes conforme especificação.
4. Compile e faça upload do código para a placa.
5. Monitore via Serial Monitor (115200 baud).

## 📦 Estrutura do Projeto

```
main.c
include/
├── led.h
├── pin.h
├── button.h
├── ssd1306_font.h
├── ssd1306_i2c.h
└── ws2812.h
```

## 📝 Notas de Implementação

- Certifique-se de que todos os pinos estão corretamente conectados conforme especificado.
- Utilize um ambiente de desenvolvimento compatível com a placa RP2040.
- Para qualquer dúvida ou problema, consulte a documentação oficial do RP2040 e das bibliotecas utilizadas.