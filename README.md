# Circuitos_Logicos
// Definição dos pinos do display de sete segmentos
const int segmentos[7] = {21, 19, 18, 5, 4, 2, 15}; // D21, D19, D18, D5, D4, D2, D15

// Números hexadecimais para exibir
const byte numeros[16] = {
  B0000001, // 0
  B1001111, // 1
  B0010010, // 2
  B0000110, // 3
  B1001100, // 4
  B0100100, // 5
  B0100000, // 6
  B0001111, // 7
  B0000000, // 8
  B0000100, // 9
  B0001000, // A
  B1100000, // B
  B0110001, // C
  B1000010, // D
  B0110000, // E
  B0111000  // F
};

void setup() {
  // Configura os pinos do display como saídas
  for (int i = 0; i < 7; i++) {
    pinMode(segmentos[i], OUTPUT);
  }
}

void loop() {
  // Exibe os números hexadecimais de 0 a 9
  for (int i = 0; i < 16; i++) {
    exibirNumeroHexadecimal(i);
    delay(700); // Aguarda 1 segundo entre cada número
  }
}

// Função para exibir um número hexadecimal no display de sete segmentos
void exibirNumeroHexadecimal(int numero) {
  if (numero >= 0 && numero <= 15) {
    byte padrao = numeros[numero];
    for (int i = 0; i < 7; i++) {
      digitalWrite(segmentos[i], bitRead(padrao, i));
    }
  }
}
