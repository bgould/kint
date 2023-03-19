
<img src="https://github.com/bgould/kint-qt/raw/main/kb2040_kinesis_controller.jpg" width="362" height="289" align="right">

The kinT-QT keyboard controller is a replacement for your Kinesis Advantage or
Advantage 2 ergonomic keyboards.

It is based on the [kin-T controller](https://github.com/kinx-project/kint)
designed by Michael Stapelberg, which utilizes the line of Teensy
microcontrollers from PJRC.

kinT-QT is designed to be microcontroller-agnostic ... the matrix and
indicator LEDs to a pair of MCP23017 port expanders that are accessible via I2C,
so all of the functionality of the keyboard can be controlled by most microcontrollers
with 2 digital pins.

The PCB has footprints for [Adafruit Feather](https://www.adafruit.com/category/946)
boards, as well as for [Adafruit KB2040](https://adafru.it/5302) and other Pro Micro
compatibles. Connections from the microcontroller footprint to the I2C bus and
USB cable are configurable by solder jumpers, and extra prototyping space is provided
to allow for maximum flexibility.

## Quick overview

<table border="0" width="100%">
<tr>
<td width="33%">
<img src="https://github.com/bgould/kint-qt/raw/main/pcb-3d-render-front-v2023-03-18.png">
3D render (front, LEDs)
</td>
<td width="33%">
<img src="https://github.com/bgould/kint-qt/raw/main/pcb-3d-render-back-v2023-03-18.png">
3D render (back, components)
</td>
<td width="33%">
<a href="https://github.com/bgould/kint-qt/blob/main/schematic-v2023-03-18.pdf"><img
src="https://github.com/bgould/kint-qt/raw/main/thumbnail-schematic-v2023-03-18.jpg"></a>
schematic
</td>
</tr>
</table>

Primary firmware: https://github.com/bgould/keyboard-firmware/tree/main/devices/kinx

The above firmware has been tested with the following microcontroller development boards:
 * Adafruit Feather M0 Express
 * Adafruit Feather M4 Express
 * Adafruit Feather nRF52840 Express
 * Adafruit Feather RP2040
 * Adafruit KB2040

## Compatibility

The kint-QT keyboard controller was made for the Kinesis Advantage or Advantage 2
series.

The kinT keyboard controller is not compatible with the newer Kinesis Advantage
360 series, introduced in 2022, because the 360 is a split keyboard that uses an
entirely different form factor for its electronics ([Kinesis 360 teardown
photos](https://photos.app.goo.gl/BwgzHgaTz1RKBjqc6)).

The kinT keyboard controller is also not compatible with **very old Advantage**
keyboards, where the left and right keywell circuit boards plug directly into
the controller. See [issue #42](https://github.com/kinx-project/kint/issues/42)
for details and pictures.

## Building your own kinT keyboard controller

1. Follow [“Buying the board and components (Bill of
   materials)”](https://github.com/bgould/kint-qt#buying-the-board-and-components-bill-of-materials). When
   ordering from OSH Park (board) and Digi-Key (components), you’ll get the
   minimum quantity of 3 boards for 72 USD (24 USD per board), and one set of
   components for 49 USD.

   * If you have any special requirements regarding which Teensy microcontroller
     to use, this is the step where you would replace the Teensy 3.6 with your
     choice.

1. Wait for the components to arrive. When ordering from big shops like Digi-Key
   or Mouser, this typically takes 2 days to many places in the world.

1. Wait for the boards to arrive. This takes 6 days in the best case when
   ordering from OSH Park with their Super Swift Service option. In general, the
   longer you are willing to wait, the cheaper it is going to get.

1. Follow [the soldering
   guide](https://github.com/bgould/kint-qt#soldering). This will take about
   an hour.

1. [Install the firmware](https://github.com/bgould/kint-qt#installing-the-firmware)

## Installing the kinT replacement controller in your Kinesis keyboard

The easiest way is to remove the existing cable from the Kinesis keyboard, and
use a regular USB cable instead (going through the existing hole in the case, no
mod required).

If you want to keep using the existing Kinesis cable, you could build the [kinX
open hardware
hub](https://michael.stapelberg.ch/posts/2018-04-17-kinx-usb-hub/), which uses a
compatible connector.

Another way is to cut open a USB cable and solder it onto the matching pins of
the Kinesis cable.  You can confirm the pinout in the hardware design files for
the kinX hub.


## Compatibility: which Teensy to use?

The kinT keyboard controller was made for the Teensy 3.x and 4.x series of
devices, which are ARM based.



## Buying the board and components (Bill of materials)

To buy the board, you can:

* [order the kinT controller from OSH Park](https://oshpark.com/shared_projects/YSZAuKc0) starting at 72 USD
* [order the kinT controller from Aisler](https://aisler.net/p/JQIIIJSL) starting at 18 EUR
* [order the kinT controller from JLCPCB](https://github.com/bgould/kint-qt/tree/main/gerbers/jlcpcb)
* or upload the [kint.kicad_pcb
  file](https://github.com/bgould/kint-qt/blob/main/kicad/kint.kicad_pcb)
  to the manufacturing service you prefer.

To buy the components, check out the [kinT BOM in the Octopart BOM
tool](https://octopart.com/bom-tool/4AnOAR3f), from where you can conveniently
buy all components via Digi-Key or Mouser.

For your convenience, this is the full BOM (links go to Octopart):

| Part Number                                                                               | Count | Cost   | Description               | Note                                               |
|-------------------------------------------------------------------------------------------|-------|--------|---------------------------|----------------------------------------------------|
| [Teensy 3.6](https://octopart.com/dev-14057-sparkfun-76356774?r=sp)                       | 1     | $32.5  |                           | [your choice!](#compatibility-which-teensy-to-use) |
| [Würth 61301011121](https://octopart.com/61301011121-w%C3%BCrth+elektronik-18818159?r=sp) | 8     | $0.89  | 10 position 2.54mm header | 6 for Teensy<br>2 for KB500<br>0 for KB600         |
| [Molex 39-53-2135](https://octopart.com/39-53-2135-molex-7670149?r=sp)                    | 6     | $1.24  | 13 position FPC connector | 4 for KB500<br>6 for KB600                         |
| [Kingbright APT3216QBC/D](https://octopart.com/apt3216qbc%2Fd-kingbright-5355642?r=sp)    | 4     | $0.47  | 1206 SMD LED              | blue 470nm<br>chose your color!                    |
| [Vishay CRCW120610K0FKEAC](https://octopart.com/crcw120610k0fkeac-vishay-20811529)        | 4     | $0.10  | 1206 10K resistor         | value determines LED brightness                    |
|                                                                                           |       | $48.45 |                           |                                                    |

Note: with all parts (except for the Molex 39-53-2135 FPC connector), there is
no need to get the specific versions from the BOM above — if you have LEDs,
resistors and pin headers still lying around from other projects, feel free to
re-use them!

## Soldering

All the soldering connections on the kinT keyboard controller are easy to make,
so the whole assembly can be done at home, with a cheap soldering iron and basic
electronic hobby equipment. A build takes about 1 hour of time and involves a
little over 100 soldering connections.

For example, I used the [Miniware TS100 soldering
iron](https://hackaday.com/2017/07/24/review-ts100-soldering-iron/), which can
be found for 50-60 EUR or USD.

If you’re new to soldering, check out [this excellent soldering reference card
from adafruit](https://twitter.com/zekjur/status/952596267884056576).

You can also [watch me solder a kinT keyboard controller on live
stream](https://youtu.be/I0kwQbnhlfk?t=5880) (from 1:38:00 to 3:33:53). The
process can be done in under an hour if you’re not talking to a live audience at
the same time :-). I want to add an edited and higher-quality video, too.

### Soldering instructions for the Teensy 3.x or 4.x

1. Populate the FPC connectors J2, J3, J4, J7 (all keyboards) and J1, J8 for the
   newer Advantage 2 (KB600). Turn the board around and solder all their pins.

1. Solder resistors R1, R2, R3, R4 and the four LEDs onto the board.

   * LEDs are directional parts! Their marker marks the cathode, which is
     labeled as C on the kinT. For details about the marker, refer to the LED
     datasheet, e.g. the [Kingbright APT3216QBC/D data
     sheet](https://www.kingbrightusa.com/images/catalog/SPEC/APT3216QBC-D.pdf)
     if you are using the LED from the [Bill of Materials
     (BOM)](#buying-the-board-and-components-bill-of-materials).

   * If you’re new to SMD (Surface Mount Devices) soldering, check out [How to
     Hand Solder SMD](http://www.davidhaillant.com/smd-soldering/), which
     explains what I call the “One pad at a time” method.

1. Turn the board around and place (but don’t solder) **3 rows of pin headers**
   (top, bottom, vertical) in the Teensy holes.

   * The vertical pin header is required for powering the LEDs.

   * If you want your Teensy to be removable, you can use socket headers here
     instead. [See the instructions below](#using-socket-headers).

1. Place your Teensy on top of the pin header and solder all its pins.

1. Turn the board around and solder all the pin header pins.

1. For the older Advantage (KB500) keyboard, populate pin headers J5, J6 and
   solder their pins.

## Installing the firmware

You can use the QMK Configurator online build tool to compile the QMK firmware for
your kinT keyboard controller, or customize your layout.

Alternatively, you can install the pre-built, tested firmware file (default QMK
keymap and settings) we offer, for example to test whether issues are related to
your self-compiled firmware.

| Teensy           | QMK Configurator                                                                                                                                         | pre-built, tested firmware                                                                                                              |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Teensy++ 2.0     | [QMK Configurator (kint2pp)](https://config.qmk.fm/#/kinesis/kint2pp/LAYOUT)                                                                             | [kinesis_kint2pp_default.hex](https://github.com/bgould/kint-qt/blob/main/default-firmware/kinesis_kint2pp_default.hex) (2020-07-09) |
| Teensy 3.6       | [QMK Configurator (kint36)](https://config.qmk.fm/#/kinesis/kint36/LAYOUT)                                                                               | [kinesis_kint36_default.hex](https://github.com/bgould/kint-qt/blob/main/default-firmware/kinesis_kint36_default.hex) (2020-07-09)   |
| Teensy 4.0 / 4.1 | <s>[QMK Configurator (kint41)](https://config.qmk.fm/#/kinesis/kint41/LAYOUT)</s> (currently [broken](https://github.com/qmk/qmk_firmware/issues/16440)) | [kinesis_kint41_default.hex](https://github.com/bgould/kint-qt/blob/main/default-firmware/kinesis_kint41_default.hex) (QMK 0.17.9)   |

You can install these .hex files with the [Teensy
Loader](https://www.pjrc.com/teensy/loader.html).

To compile your own firmware, see [QMK: Get
Started](https://docs.qmk.fm/#/?id=get-started) and refer to the [full Teensy
compatibility chart](#reference-full-teensy-compatibility-chart) above to find
the QMK branch to work with.

