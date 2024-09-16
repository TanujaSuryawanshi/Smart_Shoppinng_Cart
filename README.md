# Smart_Shoppinng_Cart

#include <SPI.h>
#include <MFRC522.h>
#define SS_PIN 10
#define RST_PIN 9
#define Buzzer 2
#define LED1 3
#define LED2 4


char input[12];
int count = 0;
 
int a;
int p1 = 0, p2 = 0, p3 = 0, p4 = 0;
int c1 = 0, c2 = 0, c3 = 0, c4 = 0;
 
double total = 0;
int count_prod = 0;



// #include <SPI.h>
// #include<Wire.h>
// //#include <MFRC522.h>
// #include <LiquidCrystal_I2C.h>
 
// //#define SS_PIN 10  // SS pin for RC522 RFID reader
// //#define RST_PIN 9  // RST pin for RC522 RFID reader
 
// //MFRC522 mfrc522(SS_PIN, RST_PIN);
// LiquidCrystal_I2C lcd(0x27, 16, 2);  
 
// void setup() {
//   Serial.begin(9600);
//   //SPI.begin();              
//  // mfrc522.PCD_Init();(((
//  Wire.begin()   ;  
//   lcd.begin(16, 2);
//   lcd.backlight();     
//   lcd.setCursor(0, 0);
//   lcd.print("Smart Shopping Cart");
//   lcd.setCursor(0, 1);

//   lcd.print("Ready to scan");
//   while(1);}



// FOR THE LCD................

#include<LiquidCrystal_I2C.h>
#include <Wire.h>
LiquidCrystal_I2C lcd(0x27,16,2);

void setup()
{
  pinMode(A4 , INPUT_PULLUP);
  pinMode(2,OUTPUT);
  pinMode(3,OUTPUT);
  pinMode(4,OUTPUT);

  lcd.clear();
  Wire.begin();
  lcd.backlight();
  Serial.begin(9600);
  // lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("AUTOMATIC BILL");
  delay (2000);
  lcd.setCursor(0,1);
  lcd.print("SHOPPING CART");
  delay (2000);
  lcd.setCursor(3,1);
  lcd.print("SUPER MARKET");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Plz Add item");
}
void loop()
{
 count = 0;
 while (serial.available() && count < 12)
 {
  input[count]= Serial.read();
  count++;
  delay(5);
 }
 int a = digitalRead(A4);

 if ((strncmp(input,"",12)== 0) && (a == 1) )
 {
void setup ()
{
  pinMode(A4, INPUT_PULLUP);
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(4, OUTPUT);
 
  lcd.clear();
  Wire.begin();
  Serial.begin(9600);
  lcd.setCursor(0, 0);
  lcd.print(" AUTOMATIC BILL");
  delay (2000);
  lcd.setCursor(0, 1);
  lcd.print(" SHOPPING CART ");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("WELCOME TO");
  delay (2000);
  lcd.setCursor(3, 1);
  lcd.print("SUPER MARKET");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Plz Add iTem");
 
 
// }
  
// void loop()
// {
  count = 0;
  while (Serial.available() && count < 12)
  {
    input[count] = Serial.read();
    count++;
    delay(5);
  }
  int a = digitalRead(A4);
 
  if ((strncmp(input, "", 12) == 0) && (a == 1))
  {
 
    lcd.setCursor(0, 0);
    lcd.print("Butter Added ");
    lcd.setCursor(0, 1);
    lcd.print("Price :- 10.00 ");
    p1++;
    digitalWrite(2, HIGH);
    digitalWrite(3, HIGH);
    digitalWrite(4, LOW);
    delay(2000);
    total = total + 10.00;
    count_prod++;
    digitalWrite(2, LOW);
    digitalWrite(3, LOW);
    digitalWrite(4, HIGH);
 
  }
  else if ((strncmp(input, "70 92 D8 55", 12) == 0) && (a == 0))
  {
    if (p1 > 0)
    {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Butter Removed!!!        ");
      digitalWrite(2, HIGH);
      digitalWrite(3, HIGH);
      digitalWrite(4, LOW);
      delay(2000);
      p1--;
      total = total - 10.00;
      count_prod--;
      lcd.clear();
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, HIGH);
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Total Price :-");
 
      lcd.setCursor(0, 1);
      lcd.print(total);
    }
    else
    {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Not in cart!!! ");
      digitalWrite(2, HIGH);
      digitalWrite(3, HIGH);
      digitalWrite(4, HIGH);
      delay(2000);
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, LOW);
      lcd.clear();
    }
  }
 
 
  if ((strncmp(input, "70 92 D8 55", 12) == 0) && (a == 1))
  {
    lcd.setCursor(0, 0);
    lcd.print("Milk Added");
    lcd.setCursor(0, 1);
    lcd.print("Price :- 20.00 ");
    p2++;
    digitalWrite(2, HIGH);
    digitalWrite(3, HIGH);
    digitalWrite(4, LOW);
    delay(2000);
    total = total + 20.00;
    count_prod++;
    digitalWrite(2, LOW);
    digitalWrite(3, LOW);
    digitalWrite(4, HIGH);
 
  }
 
  else if ((strncmp(input, "D1 48 D3 0D", 12) == 0) && (a == 0))
  {
    if (p2 > 0)
    {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Milk Removed!!!  ");
      digitalWrite(2, HIGH);
      digitalWrite(3, HIGH);
      digitalWrite(4, LOW);
      delay(2000);
      p2--;
      total = total - 20.00;
      count_prod--;
      lcd.clear();
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, HIGH);
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Total Price :-");
      lcd.setCursor(0, 1);
      lcd.print(total);
    }
    else
    {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Not in cart!!!        ");
      digitalWrite(2, HIGH);
      digitalWrite(3, HIGH);
      digitalWrite(4, HIGH);
      delay(2000);
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, LOW);
      lcd.clear();
    }
  }
 
 
if ((strncmp(input, "D1 48 D3 0D", 12) == 0) && (a == 1))
  {
    lcd.setCursor(0, 0);
    lcd.print("Tea Added       ");
    lcd.setCursor(0, 1);
    lcd.print("Price :- 25.00      ");
    p3++;
    digitalWrite(2, HIGH);
    digitalWrite(3, HIGH);
    digitalWrite(4, LOW);
    delay(2000);
    total = total + 25.00;
    count_prod++;
    digitalWrite(2, LOW);
    digitalWrite(3, LOW);
    digitalWrite(4, HIGH);
 
  }
 
  else if ((strncmp(input, "D1 48 D3 0D", 12) == 0) && (a == 0))
  {
    if (p3 > 0)
    {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Tea Removed!!!        ");
      digitalWrite(2, HIGH);
      digitalWrite(3, HIGH);
      digitalWrite(4, LOW);
      delay(2000);
      p3--;
      total = total - 25.00;
      count_prod--;
      lcd.clear();
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, HIGH);
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Total Price :-");
      lcd.setCursor(0, 1);
      lcd.print(total);
    }
    else
    {
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Not in cart!!!        ");
      digitalWrite(2, HIGH);
      digitalWrite(3, HIGH);
      digitalWrite(4, HIGH);
      delay(2000);
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, LOW);
      lcd.clear();
    }
  }
}


  lcd.setCursor(0,0);
  lcd.print("Butter Added");
  lcd.setCursor(0,1);
  lcd.print("price :- 10.00");
  p1++;
  digitalWrite(2,LOW)
 }
}

// FOR THE MFRC522...................


MFRC522 rfid(SS_PIN, RST_PIN);

byte led1 = 0;
byte led2 = 0;

void loop() {
  Serial.begin(9600);
  Serial.println("Please put your card..");
  SPI.begin();
  rfid.PCD_Init();
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(Buzzer, OUTPUT);
}

void loop() {
  if ( ! rfid.PICC_IsNewCardPresent())
    return;
  if ( ! rfid.PICC_ReadCardSerial())
    return;

  Serial.print("NUID tag is :");
  tone(Buzzer, 700);
  delay(200);
  noTone(Buzzer);
  String ID = "";
  for (byte i = 0; i < rfid.uid.size; i++) {
    Serial.print(rfid.uid.uidByte[i] < 0x10 ? " 0" : " ");
    Serial.print(rfid.uid.uidByte[i], HEX);
    ID.concat(String(rfid.uid.uidByte[i] < 0x10 ? " 0" : " "));
    ID.concat(String(rfid.uid.uidByte[i], HEX));
    delay(300);
  }
  Serial.println();
  ID.toUpperCase();

  if (ID.substring(1) == "70 92 D8 55" && led1 == 0 ) {
    digitalWrite(LED1, HIGH);
    Serial.println("LED1 is ON..");
    led1 = 1;
  } else if (ID.substring(1) == "70 92 D8 55" && led1 == 1 ) {
    digitalWrite(LED1, LOW);
    Serial.println("LED1 is OFF..");
    led1 = 0;
  } else if (ID.substring(1) == "D1 48 D3 0D" && led2 == 0 ) {
    digitalWrite(LED2, HIGH);
    Serial.println("LED2 is ON..");
    led2 = 1;
  } else if (ID.substring(1) == "D1 48 D3 0D" && led2 == 1 ) {
    digitalWrite(LED2, LOW);
    Serial.println("LED2 is OFF..");
    led2 = 0;
  } else {
    Serial.print("Wrong card!Please put correct card!");
  }
}


// FOR THE PUSH BUTTON...............


void setup() {
  pinMode(2, INPUT);
  pinMode(3, OUTPUT);
}
void loop() {
  bool value = digitalRead(2);
  if (value == 0) {
    digitalWrite(3, HIGH);
  } else {
    digitalWrite(3, LOW);
  }
}
