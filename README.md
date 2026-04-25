# uart-sound-js

WIP *UART - Universal Asynchronous Receiver and Transmitter* by sound. In JavaScript from browser to browser.

## Functions
* Transmitting: `uartSound.tx(data, {config})`
* Receiving: `uartSound.rx({config})`
* Send test sound: `uart.text({{config})`
* Tuning receiving frequency: `uartSound.tuneRx(soundHighLow, {config})`
* Baud rate calculation: uart.baudrate({config})
  Calculates from bits per symbol (ASCII = 8 bits + start bit + i.e. 2 stop bits = 11 bits / character. 1024 bits/second = 93 baud

## Config entities:
* character encoding, i.e. [ASCII](https://en.wikipedia.org/wiki/ASCII)
* amount of stop bits (how long the stop-period is)
* stop bit shortening for receiving end
* low/high frequency for 0s and 1s
* bits/second

I'm guessing from one of the illustrations at the [Wikipedia-page for UART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter) that you measure the frequency in the middle of the period a bit is being sent:

<img width="2000" height="334" alt="Image" src="https://github.com/user-attachments/assets/4cc6ffa1-1acb-4a56-a7ad-ce9285aa9c99" />

UART-signal [EidenNor](https://commons.wikimedia.org/w/index.php?title=User:EidenNor&action=edit&redlink=1) - [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0)

*Example of a UART frame. In this diagram, one [byte](https://en.wikipedia.org/wiki/Byte) is sent, consisting of a start bit, followed by eight data bits (D1-8), and two stop bits, for a 11-bit UART frame. The number of data and formatting bits, the presence or absence of a parity bit, the form of parity (even or odd) and the transmission speed must be pre-agreed by the communicating parties. The "stop bit" is actually a "stop period"; the stop period of the transmitter may be arbitrarily long. It cannot be shorter than a specified amount, usually 1 to 2 bit times. The receiver requires a shorter stop period than the transmitter. At the end of each data frame, the receiver stops briefly to wait for the next start bit. It is this difference that keeps the transmitter and receiver synchronized. BCLK = Base Clock*

## Demo

* `uart-tx.html` - A page with a test- + a text input and a transmit-button
* `uart-rx.html` - A page with a tune + a receive-button

## Dev setup

As described on VSCode's [Port forwading](https://code.visualstudio.com/docs/debugtest/port-forwarding) documentation.

* `npx serve` - in demo/experiment folder in a terminal window
* open a panel in VSCode, click Ports-tab and Forward a Port
* Choose 3000
* Open in browser
* Open browser on phone and look at sync-tab to find URL
