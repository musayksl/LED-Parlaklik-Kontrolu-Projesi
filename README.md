# LED-Parlaklik-Kontrolu-Projesi
Potansiyometre İle LED Parlaklık Kontrolü

## Proje Tanımı

Bu proje, bir potansiyometre kullanarak bir LED'in parlaklığını manuel olarak ayarlamayı sağlar. Potansiyometre değerine göre LED'in parlaklığı anında değişir.

## Kullanılan Malzemeler

- Arduino UNO

- Potansiyometre (10K ohm)

- LED

- 220 Ohm Direnç

- Breadboard

- Jumper Kablolar

## Devre Bağlantısı

- Potansiyometre orta ucu (Vout) → A0 pinine

- Potansiyometre bir ucu → 5V, diğer ucu → GND

- LED uzun bacak (anot) → 220 Ohm → D9 pinine

- LED kısa bacak (katot) → GND

## Kod Açıklaması

Arduino analog pininden (A0) gelen potansiyometre değeri PWM ile LED parlaklığını ayarlar.
```cpp
int potPin = A0;
int ledPin = 9;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(potPin);
  int ledBrightness = map(potValue, 0, 1023, 0, 255);
  analogWrite(ledPin, ledBrightness);

  Serial.print("Potansiyometre Degeri: ");
  Serial.print(potValue);
  Serial.print(" | LED Parlakligi: ");
  Serial.println(ledBrightness);

  delay(10);
}
```

## Proje Açıklaması

Potansiyometreden gelen analog değer (0-1023) okunur.

Bu değer PWM sinyali (0-255) ile LED’in parlaklığına dönüştürülür.

Kullanıcı potansiyometreyi çevirerek parlaklığı manuel olarak ayarlar.
