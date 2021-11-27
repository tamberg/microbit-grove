# Use Grove with the micro:bit

## Get started with the micro:bit
- See https://github.com/tamberg/microbit-intro

## Grove sensors and actuators
This tutorial uses the following Grove sensors and actuators, plus an adapter:

- [Temperature & humidity sensor](https://wiki.seeedstudio.com/Grove-AHT20-I2C-Industrial-Grade-Temperature%26Humidity-Sensor/) (AHT20)
- [Button switch](https://www.seeedstudio.com/Grove-Button-p-766.html)
- [Rotary angle sensor](https://www.seeedstudio.com/Grove-Rotary-Angle-Sensor-p-770.html)
- [4-digit display](https://www.seeedstudio.com/Grove-4-Digit-Display.html)
- [Grove adapter](https://www.seeedstudio.com/Grove-Shield-for-micro-bit-v2-0.html) for micro:bit

## Attach the Grove adapter
Attach the micro:bit to the [Grove adapter](https://www.seeedstudio.com/Grove-Shield-for-micro-bit-v2-0.html) by sliding it into the connector.

Make sure the micro:bit led matrix display faces towards you.

## Open the Grove extension
TODO

## Blink an LED
Connect an LED to Grove Port *P0*.

<img src="images/grove-led.png" width="512" />

```
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500) // ms
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500) // ms
})
```

## Control a servo
Connect a servo to Grove Port *P0*, but power it with 5V.

<img src="images/servo.png" width="512" />

```
let position = 90 // degrees
input.onButtonPressed(Button.A, function () {
    position = Math.max(position - 10, 0)
    servos.P0.setAngle(position)
})
input.onButtonPressed(Button.B, function () {
    position = Math.min(position + 10, 180)
    servos.P0.setAngle(position)
})
```

## Display a value
Connect a 4-digit display to Grove Port *P0*.

<img src="images/display.png" width="512" />

```
let display = grove.createDisplay(DigitalPin.P0, DigitalPin.P14)
basic.forever(function () {
    display.show(input.temperature())
    basic.pause(100)
})
```

## Read a switch
Connect a switch to Grove Port *P0*.

<img src="images/switch-value.png" width="512" />

```
basic.forever(function () {
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
})
```

## Toggle a switch
Connect a switch to Grove Port *P0*.

<img src="images/switch-state.png" width="512" />

```
let state = 0
pins.onPulsed(DigitalPin.P0, PulseValue.High, function () {
    if (state == 0) {
        basic.showIcon(IconNames.Heart)
        state = 1
    } else { // state == 1
        basic.clearScreen()
        state = 0
    }
})
```

## Read a dial
Connect a 4-digit display to Grove Port *P0* and a rotary angle sensor to Grove Port *P1*.

<img src="images/distance.png" width="512" />

```
let display = grove.createDisplay(DigitalPin.P0, DigitalPin.P14)
basic.forever(function () {
    display.show(pins.analogReadPin(AnalogPin.P1))
    basic.pause(100)
})
```

## Read distance
Connect a 4-digit display to Grove Port *P0* and an ultrasonic sensor to Grove Port *P1*.

<img src="images/distance.png" width="512" />

```
let display = grove.createDisplay(DigitalPin.P0, DigitalPin.P14)
basic.forever(function () {
    display.show(grove.measureInCentimeters(DigitalPin.P1))
    basic.pause(100)
})
```

## Read humidity
Connect a AHT20 sensor to Grove Port *I2C*.

<img src="images/humidity.png" width="512" />

```
basic.forever(function () {
    basic.showNumber(grove.aht20ReadHumidity())
})
```

## Read temperature
Connect a AHT20 sensor to Grove Port *I2C*.

<img src="images/temperature.png" width="512" />

```
basic.forever(function () {
    basic.showNumber(grove.aht20ReadTemperatureC())
})
```

## More
- https://github.com/tamberg/microbit-ghoust
- https://makecode.microbit.org/projects
- https://makecode.microbit.org/docs
