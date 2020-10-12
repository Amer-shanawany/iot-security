# Data in-out

| Blok     | Data in                                                      | Data out                                                     |
| :------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ESP32MCU | **MQTT**<br/>"ZERO"<br/>move the carriage to the 0/0 position and recalibrate | **MQTT**<br/>"ACK_ZERO"<br/>acknowlegdment                   |
|          | **MQTT**<br/>"SETX*0123*SETY*0123*"<br />set the dimensions for the XY-system (units=mm) | **MQTT**<br/>"ACK_SETX*0123*SETY*0123*"<br/>acknowlegdment   |
|          | **MQTT**<br/>"POSX*0123*POSY*0123*"<br/>move the carriage to a desired position (units=mm) | **MQTT**<br/>"ACK_POSX*0123*POSY*0123*"<br/>acknowledgment   |
|          | **MQTT**<br/>"PHOT*0123456789UIOP*"<br />take a picture with the following code/filename | **HTTP (POST)**<br />*0123456789UIOP*.JPEG<br />save picture in the database<br />**MQTT**<br />"ACK_PHOT*0123456789UIOP*"<br />acknowledgement |
|          | **MQTT**<br/>"DISA"<br />disable stepper motors              | **MQTT**<br/>"ACK_DISA"<br/>acknowledgement                  |
| DRV8825  | - direction<br />- steps                                     | /                                                            |



...

```c#
const uint8_t DIRECTION = 2;

enum {
    DIRX,
    DIRY
};

typedef struct Position{
    uint16_t Position
} MotorAction

Position currentPosition[DIRECTION] = {{0}, {0}}
```

