/* 
 By Arteen Mirzaei
 September 14th 2020
 Version 1.2
 Changes Made:

 Added 600 LED capacity

 Default to FIVE_FIFTEEN();

 0-179 -> Roofline 1
 180-375 -> Roofline 2
 376-570 -> Roofline 3
 ____________________________

 149-150 -> Gap 1
 299-300 -> Gap 2
 449-450 -> Gap 3
 
 
*/
/******************  LIBRARY SECTION  *************************************/
#include <FastLED.h>
/*****************  LED LAYOUT AND SETUP  *********************************/
// Just one strip of 570 (Uses 620 to assure no errors)
#define NUM_LEDS 640
/*****************  DECLARATIONS  *****************************************/
// Defined the LED list
CRGB leds[NUM_LEDS];
/*****************  GLOBAL VARIABLES  *************************************/
const int stripPin = 7; // LED Strip Pin Value
const int switch0 = 11, switch1 = 12, switch2 = 13; // Push Buttons Pin Value(s)
const int led_white = 8, led_yellow = 9, led_red = 10; // Individual LED's Pin Value(s)
const int num_loops = 600; // How many times you want a loop to run
const int brightness = 255, brightness2 = 200;
int pressed, pressed1, pressed2; // Button's Value
bool button_pressed = true; // If the button is Pressed or not (Stored Variable)
/*****************  SETUP FUNCTIONS  **************************************/
void setup() 
{
  Serial.begin(115200);
  pinMode(switch0, INPUT);
  pinMode(switch1, INPUT);
  pinMode(switch2, INPUT);
  pinMode(led_yellow, OUTPUT);
  pinMode(led_red, OUTPUT);
  pinMode(led_white, OUTPUT);
  FastLED.addLeds<WS2812B, stripPin, GRB>(leds, NUM_LEDS);
}

/*****************  PATTERNS (FUNCTIONS)  *********************************/
void BUTTON_CHECK(int switch_name) { // Registers Button Inputs and returns an escape value
  
  int pressed = digitalRead(switch_name);
  
  if (pressed == HIGH) {
    button_pressed = false;
  }
  return button_pressed;
  
}


void RUNNING_COLOUR(int hue, int saturation, int brightness, int delay_num, int i, int switch_name) { // Turns all LEDs to one colour (one at a time)
  delay(delay_num);
  leds[i] = CHSV(hue, saturation, brightness);
  FastLED.show();
  BUTTON_CHECK(switch_name);
}

void RUNNING_COLOUR_3(int hue, int saturation, int brightness, int delay_num, int i, int switch_name, int sign) {
  int i_1;
  int i_2;
  if (sign == 1) {
    i_1 = i + 1;
    i_2 = i + 2;
  }
  else {
    i_1 = i - 1;
    i_2 = i - 2;
  }
  delay(delay_num);
  leds[i] = CHSV(hue, saturation, brightness);
  leds[i_1] = CHSV(hue, saturation, brightness);
  leds[i_2] = CHSV(hue, saturation, brightness);
  FastLED.show();
  BUTTON_CHECK(switch_name);
}

void RGB_PATTERN() {

  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();

  delay(500);
  
  button_pressed = true;
  
  for (int i = 0; i <= num_loops; i+=33) {

    for (int x = 0; x < 10; x++) {
      leds[i+x] = CRGB(191, 0, 0);
    }
    leds[i+10] = CRGB(0, 0, 0);
    for (int x = 0; x < 10; x++) {
      leds[i+x+11] = CRGB(191, 191, 191);
    }
    leds[i+21] = CRGB(0, 0, 0);
    for (int x = 0; x < 10; x++) {
      leds[i+x+22] = CRGB(0, 0, 191);
    }
    leds[i+32] = CRGB(0, 0, 0);
  }
  FastLED.show();
  
  while(button_pressed) {
    BUTTON_CHECK(switch1);
    delay(50);
  }
  
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  delay(500);
  
}

void WHITE_BLACK() {

  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();

  delay(500);

  button_pressed = true;

  for (int i = 0; i <= num_loops; i++) {
    if (i % 2 == 0) {
      leds[i] = CRGB(255, 255, 255); 
    }
    else {
      leds[i] = CRGB(0, 0, 0);
    }
  }

  FastLED.show();

  while(button_pressed) {
    BUTTON_CHECK(switch1);
    delay(50);
  }

  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  delay(500);
  
}

void RED_GREEN() {
  
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();

  button_pressed = true;

  int add = 0;
  
  for (int i = 0; i <= num_loops / 12; i++) {  
    
    for (int i = add; i <= 2 + add; i++) {
      leds[i] = CRGB(255, 0, 0); //ORANGE (218, 66, 0)
    }
    for (int i = 6 + add; i <= 8 + add; i++) {
      leds[i] = CRGB(0, 255, 0); //PURPLE
    } 
    add += 12;
    FastLED.show();
  }

  delay(500);

  while(button_pressed) {
    BUTTON_CHECK(switch2);
    delay(50);
  }
  
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  delay(500);
}

void HALLOWEEN() {

  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();

  button_pressed = true;

  int add = 0;
  
  for (int i = 0; i <= num_loops / 12; i++) {  
    
    for (int i = add; i <= 2 + add; i++) {
      leds[i] = CRGB(218, 66, 0); //ORANGE (218, 66, 0)
    }
    for (int i = 6 + add; i <= 8 + add; i++) {
      leds[i] = CRGB(102, 0, 204); //PURPLE
    } 
    add += 12;
    FastLED.show();
  }

  delay(500);

  while(button_pressed) {
    BUTTON_CHECK(switch2);
    delay(50);
  }
  
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  delay(500);
  
}

void FIVE_FIFTEEN() {

  delay(500);
  
  button_pressed = true;

  int x = 0;

  for (int i = 0; i <= 40; i++) {
      
    for (int i = x; i <= (2 + x); i++) {
      leds[i] = CRGB(191, 110, 27);
    }
  
    x += 15;
  }
  FastLED.show();

  while(button_pressed) {
    BUTTON_CHECK(switch2);
    delay(50);
  }
  
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  delay(500);
  
}


void RGW_PATTERN_1() {

  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  
  button_pressed = true;

  while(button_pressed) { // Loops the Pattern


    // Every two LEDs, Shows a Red Colour (~150 Millisecond per LED)
    for (int i = 0; i <= num_loops; i+=2) {

      RUNNING_COLOUR(0, 255, brightness, 150, i, switch0);

      BUTTON_CHECK(switch0); // Reads a Button Input
      
    }

    // Same As Last Loop, but for a Green Colour
    for (int i = (num_loops + 1); i >= 0; i-=2) {

      RUNNING_COLOUR(92, 255, brightness, 150, i, switch0);
      
      BUTTON_CHECK(switch0);

    }


    // Clears all LEDs to Colourless in reverse order (From LED 60 -> 0) (1 LED every ~25 Milliseconds)
    for (int i = num_loops; i >= 0; i-=1) {
      
      RUNNING_COLOUR(0, 0, 0, 25, i, switch0);

      BUTTON_CHECK(switch0); // Reads a Button Input
      
    }
    
    for (int i = 0; i <= num_loops; i++) {

      BUTTON_CHECK(switch0); // Reads a Button Input

      // If the loop count is an even number, light the LED Red
      if (i % 2 == 0) {
        RUNNING_COLOUR(0, 255, brightness, 150, i, switch0);
      } 
      // If the loop count is odd, light the LED Green
      else {
        RUNNING_COLOUR(92, 255, brightness, 150, i, switch0);
      }
    }

    // Clears all LEDs to Colourless in reverse order (From LED 60 -> 0) (1 LED every ~25 Milliseconds)
    for (int i = num_loops; i >= 0; i-=1) { 

      RUNNING_COLOUR(0, 0, 0, 25, i, switch0);
      
    }

    
    for (int i = 0; i <= 1; i++) {

      BUTTON_CHECK(switch0); // Reads a Button Input
      
      delay(50);

      // Sets all LEDs to White (for ~50 Milliseconds)
      fill_solid(leds, NUM_LEDS, CHSV(0, 0, brightness));
      FastLED.show();
       
      delay(50);

      // Turns All LEDs off
      fill_solid(leds, NUM_LEDS, 0);
      FastLED.show();
      
      // Repeat This Pattern (Two White Flashes total)
    }
  }
}

void RGW_PATTERN_3()
{
  button_pressed = true;

  delay(150);

  while(button_pressed) { // Loops the Pattern


    // Every two LEDs, Shows a Red Colour (~150 Millisecond per LED)
    for (int i = 0; i <= num_loops; i+=12) {

      RUNNING_COLOUR_3(0, 255, brightness, 150, i, switch0, 1);

      BUTTON_CHECK(switch0); // Reads a Button Input
      
      if (not button_pressed) {
        break;
      }
      
    }

    if (not button_pressed) {
      break;
    }
    
    // Same As Last Loop, but for a Green Colour
    for (int i = (num_loops - 1); i >= 0; i-=12) {

      RUNNING_COLOUR_3(92, 255, brightness, 150, (i - 3), switch0, 2);
      
      BUTTON_CHECK(switch0);
  
      if (not button_pressed) {
        break;
      }

    }

    if (not button_pressed) {
      break;
    }


    // Clears all LEDs to Colourless in reverse order (From LED 60 -> 0) (1 LED every ~25 Milliseconds)
    for (int i = num_loops; i >= 0; i-=1) {
      
      RUNNING_COLOUR(0, 0, 0, 25, i, switch0);

      BUTTON_CHECK(switch0); // Reads a Button Input
      
      if (not button_pressed) {
        break;
      }
      
    }

    if (not button_pressed) {
      break;
    }

    int add = 0;
    
    for (int i = 0; i <= num_loops; i+=3) {

      BUTTON_CHECK(switch0); // Reads a Button Input
 
      if (not button_pressed) {
        break;
      }

      // If the loop count is an even number, light the LED Red
      if (i % 2 == 0) {
        add += 1;
        Serial.println(add);
        if (add % 2 == 0) {
          RUNNING_COLOUR_3(0, 255, brightness, 150, i, switch0, 1); // 0, 6, 12, 18, 24
        }
        else {
          RUNNING_COLOUR_3(92, 255, brightness, 150, i, switch0, 1);
        }
      } 
    }

    // Clears all LEDs to Colourless in reverse order (From LED 60 -> 0) (1 LED every ~25 Milliseconds)
    for (int i = num_loops; i >= 0; i-=1) { 

      RUNNING_COLOUR(0, 0, 0, 25, i, switch0);

      if (not button_pressed) {
        break;
      }
      
    }

    
    for (int i = 0; i <= 1; i++) {

      BUTTON_CHECK(switch0); // Reads a Button Input
 
      if (not button_pressed) {
        break;
      }
      
      delay(50);

      // Sets all LEDs to White (for ~50 Milliseconds)
      fill_solid(leds, NUM_LEDS, CHSV(0, 0, brightness));
      FastLED.show();;
  
      delay(50);

      // Turns All LEDs off
      fill_solid(leds, NUM_LEDS, 0);
      FastLED.show();
       
      // Repeat This Pattern (Two White Flashes total)
    }
  }

  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
}

void PAC_MAN() {

  button_pressed = true;
  
  while (button_pressed) { // Loops the pattern
    
    delay(150);

    fill_solid(leds, NUM_LEDS, CHSV(0, 0, (brightness - brightness2)));
    FastLED.show();
    
    leds[0] = CHSV(64, 255, brightness - brightness2); // Spawns Pac-Man Colour on the First LED
    
    for (int i = 0; i <= (num_loops + 10); i++) {
      
      // Moves the Pac-Man Dot up one space each time 
      leds[i] = CHSV(0, 0, (brightness - brightness2));
      leds[i + 1] = CHSV(64, 255, brightness - brightness2);

      BUTTON_CHECK(switch1); // Reads a Button

      
      if (not button_pressed) {
        break;
      }
      
      // Spawns and Moves all the Ghosts (And the White trail behind the last Ghost)
      if (i >= 5) { 
       leds[i - 9] = CHSV(0, 0, (brightness - brightness2));
       leds[i - 8] = CHSV(213, 255, brightness - brightness2);
       leds[i - 7] = CHSV(0, 255, brightness - brightness2);
       leds[i - 6] = CHSV(10, 255, brightness - brightness2);
      } 
      if (i >= 4) {
       leds[i - 5] = CHSV(140, 255, brightness - brightness2); 
      }

      delay(50);
      FastLED.show();
      
    }
    if (not button_pressed) {
      
      fill_solid(leds, NUM_LEDS, 0);
      FastLED.show();

    }
    
    }
  
}

void SOLID_WHITE() {

  button_pressed = true;

  fill_solid(leds, NUM_LEDS, CRGB(255, 197, 143));
  FastLED.show();

  delay(500);

  while(button_pressed) {

    BUTTON_CHECK(switch2);
    
    delay(50);
   
  }

  delay(500);
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
}

void RUN_50_50() {

  delay(300);

  int speed_value = 1;
  
  button_pressed = true;
  
  while (button_pressed) {
    
    for (int i = 0; i <= 179; i++) {

      RUNNING_COLOUR(0, 255, brightness, speed_value, i, switch1);
      
      RUNNING_COLOUR(92, 255, brightness, speed_value, 179 - i, switch1);

      RUNNING_COLOUR(0, 255, brightness, speed_value, i + 180, switch1);
      
      RUNNING_COLOUR(92, 255, brightness, speed_value, 375 - i, switch1);

      RUNNING_COLOUR(0, 255, brightness, speed_value, i + 375, switch1);

      RUNNING_COLOUR(92, 255, brightness, speed_value, 570 - i, switch1);

      
      if (not button_pressed) {
        break;
      }
      
    }

    for (int i = 0; i <= 89; i++) {

      RUNNING_COLOUR(0, 0, 0, speed_value, 89 - i, switch1);

      RUNNING_COLOUR(0, 0, 0, speed_value, i + 89, switch1);

      RUNNING_COLOUR(0, 0, 0, speed_value, 89 + 179 - i, switch1);

      RUNNING_COLOUR(0, 0, 0, speed_value, i + 89 + 179, switch1);

      RUNNING_COLOUR(0, 0, 0, speed_value, 89 + 375 - i, switch1);

      RUNNING_COLOUR(0, 0, 0, speed_value, i + 89 + 375, switch1);

      if (not button_pressed) {
        break;
      }

    }

    for (int i = 0; i <= 179; i++) {

      RUNNING_COLOUR(0, 255, brightness, speed_value, i, switch1);
      
      RUNNING_COLOUR(92, 255, brightness, speed_value, 179 - i, switch1);

      RUNNING_COLOUR(0, 255, brightness, speed_value, i + 179, switch1);

      RUNNING_COLOUR(92, 255, brightness, speed_value, 359 - i, switch1);

      RUNNING_COLOUR(0, 255, brightness, speed_value, i + 375, switch1);

      RUNNING_COLOUR(92, 255, brightness, speed_value, 570 - i, switch1);
      
      if (not button_pressed) {
        break;
      }
    }
    
  }
  
  fill_solid(leds, NUM_LEDS, 0);
  FastLED.show();
  
}
/*****************  MAIN LOOP  ****************************************/
void loop() 
{
 
  int pressed = digitalRead(switch0); // Reads the Button Input (Button 1)
  int pressed1 = digitalRead(switch1); // Reads the Button Input (Button 2)
  int pressed2 = digitalRead(switch2); // Reads the Button Input (Button 3)

  //for (int i = 0; i <= num_loops; i++) {
  //   leds[i] = CRGB(0, 255, 0);
  //}
  //FastLED.show();

  //for (int i = 0; i <= num_loops; i++) {
    //if (i % 2 == 0) {
      //leds[i] = CRGB(100, 100, 100); 
    //}
    //else {
      //leds[i] = CRGB(0, 0, 0);
    //}
  //}

  //FastLED.show();

  //int add = 0;
  
  //for (int i = 0; i <= num_loops / 12; i++) {  
    
    //for (int i = add; i <= 2 + add; i++) {
      //leds[i] = CRGB(255, 0, 0);
    //}
    //for (int i = 6 + add; i <= 8 + add; i++) {
      //leds[i] = CRGB(0, 255, 0);
    //} 
    //add += 12;
  //}
  //FastLED.show();

  int x = 0;

  for (int i = 0; i <= 40; i++) {
      
     for (int i = x; i <= (2 + x); i++) {
       leds[i] = CRGB(191, 110, 27);
     }
  
     x += 15;
   }
  FastLED.show();
  
  if (pressed == HIGH) { // Detect Button 1's Input
    fill_solid(leds, NUM_LEDS, 0);
    FastLED.show();
    digitalWrite(led_red, HIGH);     
    RGW_PATTERN_3();
    delay(150);
  }
  else if (pressed1 == HIGH){ // Detect Button 2's Input
    fill_solid(leds, NUM_LEDS, 0);
    FastLED.show();
    digitalWrite(led_yellow, HIGH);
    RGB_PATTERN();
    delay(150);
  }
  else if (pressed2 == HIGH) {
    fill_solid(leds, NUM_LEDS, 0);
    FastLED.show();
    digitalWrite(led_white, HIGH);
    WHITE_BLACK(); 
    delay(150);
  }
  else { // If nothing is detected in the moment, Repeat the Loop (Every ~1 Millisecond)
    digitalWrite(led_red, LOW);
    digitalWrite(led_yellow, LOW);
    digitalWrite(led_white, LOW);
    delay(1);
  }

}
// 255, 147, 36 -> Warm White (100%)
// 191, 110, 27 -> Warm White (75%)
// 128, 74, 18 -> Warm White (50%)
