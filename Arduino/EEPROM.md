# EEPROM
以下のようにEEPROMを利用することができる。
ple 1：リスト表示
#include <EEPROM.h>
void setup() {
Serial.begin(9600);
}
void loop() {
int eep_size = EEPROM.length();
Serial.print("EEPROM SIZE:");
Serial.println(eep_size);
for (int i = 0 ; i < eep_size ; i++)
{
byte val = EEPROM[i];
Serial.print("#");
// fill by 0
for (byte zro = 1; zro < 4; zro++) if (i < pow(10, zro)) Serial.print("0");
Serial.print(i);          // address number
Serial.print(":");
// fill by 0
for (byte zro = 1; zro < 3; zro++) if (val < pow(10, zro)) Serial.print("0");
Serial.print(val);  // value
if (((i + 1) % 10) == 0) Serial.println();
else Serial.print("  ");
}
while (1);
}
