# Task-2-KeshavBhise
# Repository For Automatic Irrigation System-Code
#define SOIL_PIN 34
#define RELAY_PIN 26

int moisture;
int percentage;

void setup() {

Serial.begin(115200);

pinMode(RELAY_PIN, OUTPUT);

digitalWrite(RELAY_PIN, LOW);

}

void loop() {

moisture = analogRead(SOIL_PIN);

//Convert to percentage

percentage = map(moisture, 4095, 0, 0, 100);

percentage = constrain(percentage,0,100);

Serial.print("Soil Moisture: ");

Serial.print(percentage);

Serial.println("%");


//Dry soil

if(percentage < 40)
{
digitalWrite(RELAY_PIN, HIGH);

Serial.println("Pump ON");
}


//Wet soil

else if(percentage > 60)
{
digitalWrite(RELAY_PIN, LOW);

Serial.println("Pump OFF");
}

delay(2000);

}
