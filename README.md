# Use Grove sensors and actuators with the micro:bit

## Get started
- See https://github.com/tamberg/microbit-intro

## Attach the Grove adapter
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

## Read a switch
TODO

## Read distance
TODO

## Read humidity
TODO

## Read temperature
TODO

## More
- https://github.com/tamberg/microbit-ghoust
- https://makecode.microbit.org/projects
- https://makecode.microbit.org/docs
