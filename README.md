# Use Grove sensors and actuators with the micro:bit

## Get started
- See https://github.com/tamberg/microbit-intro

## Attach the Grove adapter
TODO

## Blink an LED
TODO

## Turn a servo
<img src="images/servo.png" width="512" />

```
let position = 90
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
