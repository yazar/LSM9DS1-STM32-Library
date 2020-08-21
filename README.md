# LSM9DS1-STM32-Library

This is a library for LSM9DS1 9 DOF IMU Breakout. 
I have basically took the sparkfun library whick written for arduino ([here](https://github.com/sparkfun/LSM9DS1_Breakout)) and I rewritten it for STM32. I have used it with stm32f407vg discovery board, but this should be working in other versions to. 

I didn't have time for coding the SPI side so this has only I2C. 

## Usage

Use CubeMX to init the code with i2c

Add `lsm9ds1.c` , `lsm9ds1.h`, `LSM9DS1_Registers.h` and  `LSM9DS1_Types.h` files to your project.

Above `main()`, define variables:

```float ax, ay, az, gx, gy, gz, mx, my, mz;```

In `main()`, call this functions to initialize the sensor and set scales:

```
begin(0x6B,0x1E,&hi2c1);		// 0x6B I2C Address of accelerometer and gyroscope // 0x1E I2C Address of magnetometer
setMagScale(16);
setAccelScale(16);
setGyroScale(2000);
 ```
 
 Than use read functions to read the scaled sensor values into our variables:
 ```
readAccel(&ax,&ay,&az);
readGyro(&gx,&gy,&gz);
readMag(&mx,&my,&mz);
 ```
 
 Thats all, have fun :)
