# Arduino溫室效應實作

材料：DHT22、Arduino、杜邦線

接線圖：

![arduino-excel-dht22-data-logger](https://user-images.githubusercontent.com/93476768/157990860-b5e01f56-fade-45eb-9e97-92fd7fbc9bf0.png)

傳輸Excel: https://www.parallax.com/package/plx-daq/

程式：

    // Excel datalogger using Arduino and DHT22 sensor
 
    #include <DHT.h>              // Include DHT library code
 
    #define DHTPIN  2             // DHT22 data pin is connected to Arduino pin 2
 
    #define DHTTYPE DHT22         // DHT22 sensor is used
    DHT dht(DHTPIN, DHTTYPE);     // Initialize DHT library
 
    void setup() {
      Serial.begin(9600);         // Initialize serial communications with the PC
  
      dht.begin();                // Initialize the DHT library
  
      Serial.println("CLEARDATA");       // Clear all Excel sheet data
      // Label columns: A for date, B for time, C for temperature and D for humidity
      Serial.println("LABEL,Date,Time,Temperature,Humidity");
    }
 
    void loop() {
      Serial.print("DATA,DATE,TIME,");       // Write date and time on row A and row B respectively
      Serial.print(dht.readTemperature());   // Read temperature from sensor and send its value to Excel
      Serial.print(",");                     // Move to next column
      Serial.print(dht.readHumidity());      // Read humidity from sensor and send its value to Excel
      Serial.println(",");                   // Move to next column and start new row
 
      delay(1000);                           // Wait 1 second
    }
        RickyChen
        
        
 




   
