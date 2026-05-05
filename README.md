// ===== RÉCEPTEUR =====
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (receivedNumber == 2) {
        basic.showLeds(`
            . . . . .
            . # . . .
            . . . . .
            . . . # .
            . . . . .
            `)
    } else if (receivedNumber == 3) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . #
            `)
    } else if (receivedNumber == 4) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
    } else if (receivedNumber == 5) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
    } else if (receivedNumber == 6) {
        basic.showLeds(`
            # . . . #
            # . . . #
            # . . . #
            . . . . .
            . . . . .
            `)
    } else if (receivedNumber == 7) {
        basic.showArrow(ArrowNames.West)
    } else if (receivedNumber == 8) {
        basic.showArrow(ArrowNames.East)
    } else {
        basic.showNumber(receivedNumber)
    }
})
// ===== ÉMETTEUR =====
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(7)
})
input.onButtonPressed(Button.AB, function () {
    radio.sendNumber(input.temperature())
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(8)
})
input.onGesture(Gesture.Shake, function () {
    dé = Math.randomRange(1, 6)
    radio.sendNumber(dé)
})
let dé = 0
// ===== SETUP =====
radio.setGroup(91)
