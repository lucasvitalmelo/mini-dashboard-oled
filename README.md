# Projeto com Arduino Nano e Display OLED 🌟

A motivaçao para esse projeto em geral foi a junção de dois amores e uma necessidade:
 **Amores**: Programação e Eletrônica
 **Necessidade**: Falta de um sensor de temperatura no carro e não poder controlar o brilho do painel de instrumentos.

## Funcionalidades 🚀
- **Controle de Brilho**: O brilho da fita LED é ajustado através de um encoder rotativo e é salvo na EEPROM, para ser recuperado após reiniciar o sistema.
- **Leitura de Temperatura**: O sensor LM35 é usado para ler a temperatura ambiente e exibir o valor no display OLED .

### Classes

- **RotaryEncoder**: Classe que lida com a leitura do encoder rotativo, permitindo ajustar o brilho da fita LED.
- **EncoderButton**: Classe que lida com o botão do encoder rotativo para navegar pelos menus.

### Funções Principais 📌

- **`setup()`**: Inicializa o display OLED, o encoder rotativo, o botão e o sensor de temperatura. Exibe a tela de introdução (splash screen).
- **`loop()`**: Atualiza o estado do botão e do encoder rotativo, além de controlar a mudança de brilho e a atualização do menu.
- **`updateMenu()`**: Atualiza o menu atual no display OLED, alternando entre temperatura, brilho, sobre o projeto e outros.
- **`showTemperature()`**: Exibe a temperatura atual, calculada a partir do valor do sensor LM35, em graus Celsius.
- **`showBrightness()`**: Exibe o nível de brilho atual da fita LED e um gráfico de barras  mostrando o valor.
- **`showAbout()`**: Exibe informações sobre o projeto.
- **`splashScreen()`**: Exibe o logo personalizado na tela inicial.
 
## Componentes 🔧

- **Arduino Nano**
- **Display OLED 128x32 (SSD1306)**
- **Sensor de Temperatura LM35**
- **Encoder Rotativo**
- **Fita de LED controlada via PWM**
- **MOSFET IRF540** para controle da fita de LED
- **EEPROM** para salvar configurações
- **Resistores** para proteção de componentes
- **Capacitores** para estabilização de tensão
- **Botão** para navegação entre menus
- **Fonte de alimentação externa** para a fita de LED

## Esquema de Conexões 🧩

### **Sensor de Temperatura LM35 🌡️**

- **VCC** → Pino **5V** do Arduino
- **GND** → Pino **GND** do Arduino
- **Saída (OUT)** → Pino analógico **A0** do Arduino

O **LM35** é um sensor analógico de temperatura que fornece uma tensão proporcional à temperatura ambiente. Conectando sua saída ao pino **A0** do Arduino, podemos ler a temperatura em graus Celsius.

### **Fita de LED e MOSFET IRF540 💡**

- **Drain do MOSFET** → Pino de controle da fita de LED
- **Source do MOSFET** → GND
- **Gate do MOSFET** → Pino PWM **9** do Arduino (para controle de brilho)
- **Fita de LED** → Fonte de alimentação externa (12V)
- **Resistor (220Ω)** entre o **Gate** do MOSFET e o pino PWM (para limitar a corrente no gate)
- **Capacitor (0.1µF)** entre **VCC** e **GND** da fita de LED (para suavizar picos de corrente)

O **MOSFET IRF540** controla a corrente que passa pela fita de LED. A tensão de controle no **Gate** (via pino PWM do Arduino) ajusta o brilho da fita de LED. O resistor e o capacitor ajudam a estabilizar e proteger os componentes.

### **Encoder Rotativo e Botão**

- **Pino A do Encoder** → Pino **2** do Arduino
- **Pino B do Encoder** → Pino **3** do Arduino
- **Botão do Encoder** → Pino **4** do Arduino
- **VCC do Encoder** → Pino **5V** do Arduino
- **GND do Encoder** → Pino **GND** do Arduino

O **encoder rotativo** é usado para ajustar o brilho da fita de LED. O botão embutido permite navegar entre os diferentes menus do display OLED.

### **Display OLED (SSD1306)**

- **VCC** → Pino **5V** do Arduino
- **GND** → Pino **GND** do Arduino
- **SCL** → Pino **A5** do Arduino (para comunicação I2C)
- **SDA** → Pino **A4** do Arduino (para comunicação I2C)

O **display OLED** exibe as informações sobre a temperatura, brilho da fita de LED e outros detalhes do projeto.

## Como Usar 📘

2. **Carregar o código**:
   - Compile e envie o código para o seu **Arduino Nano** usando o **Arduino IDE**.

3. **Operar o sistema**:
   - Use o **encoder rotativo** para ajustar o brilho da fita de LED.
   - Use o **botão** para navegar entre os menus.
   - O **display OLED** exibirá a temperatura atual, o nível de brilho e informações sobre o projeto.

## Licença 📜

Este projeto está licenciado sob a **Licença MIT** 📝 - veja o arquivo [LICENSE](LICENSE) para mais detalhes.
