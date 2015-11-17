# USLI Payload Pseudo-Code


The following is all _pseudo-code_ and follows a Arduino/C style syntax.

---

## Science Payload



#### Nanduino One
```
loop(){
	
	if(rocket_is_landed){

		for(int i = 0; i < sizeof(SD_Data_Size); i++){

			Serial.println(SD_Card_Store[i]);
		}
	}

	else{

		float accelerationX = adafruitDOF.collectData(acceleration.x());

		float accelerationY = adafruitDOF.collectData(acceleration.y());

		float accelerationZ = adafruitDOF.collectData(acceleration.z());


		float gyroscopeX = adafruitDOF.collectData(gyroscope.X());

		float gyroscopeY = adafruitDOF.collectData(gyroscope.Y());

		float gyroscopeZ = adafruitDOF.collectData(gyroscope.Z());


		float magnetometerX =  adafruitDOF.collectData(magnetometer.X());

		float magnetometerY =  adafruitDOF.collectData(magnetometer.Y());

		float magnetometerZ =  adafruitDOF.collectData(magnetometer.Z());


		float gpsLongitude = gpsModule.getLongitude();

		float gpsLatitude = gpsModule.getLatitude();

		float gpsAltitude = gpsModule.getAltitude();

		SD_Card_Store.store_all_data(ALL_DATA);

	}

}
```

##### Nanduino Two

```
loop(){

	if(rocket_is_landed){

		for(int i = 0; i < sizeof(SD_Data_Size); i++){

			Serial.println(SD_Card_Store[i]);
		}
	}

	else{

		var humidtyData = H1H4030.collectData();

		humidtyData.convertUnits();

		var	solarData = solarCell.collectData();

		var uvData = uvSensor.collectData();

	}
}

```

## Drag Flap System

```

loop(){
	
	if(rocket_is_accelerating){

		WAIT;
	}

	else if(rocket_is_at_apogee){

		CLOSE_FLAPS
	}

	else{

		var newDragFlapAngle = DO MAGIC MOD-CON THINGS HERE;

		var currentDragFlapAngle = getCurrentAngle();

		if( newDragFlapAngle > currentDragFlapAngle ){

			while currentDragFlapAngle != newDragFlapAngle{

				turnMotorUp();
			}

		}

		else{

			while currentDragFlapAngle != newDragFlapAngle{

				turnMotorDown();
			}

		}




	}





}

```
	

	