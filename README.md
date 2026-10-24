# kicad-adafruit-microsd

[![ERC/DRC](https://img.shields.io/github/actions/workflow/status/solar-cooker-UHasselt/kicad-adafruit-microsd/kibot.yml?branch=main&event=push&label=ERC%2FDRC)](https://github.com/solar-cooker-UHasselt/kicad-adafruit-microsd/actions/workflows/kibot.yml)
[![KiCad 10](https://img.shields.io/badge/KiCad-10-314CB0)](https://www.kicad.org/download/)

A breakout board for a microSD card over SPI. It has a push-push socket with card
detect, an activity LED, a 3.3 V regulator for the card and a 74HC4050 level shifter so
it works with 3.3 V and 5 V boards. It is a KiCad 10 port of
[Adafruit's microSD breakout](https://github.com/adafruit/MicroSD-breakout-board),
originally drawn in Eagle.

In the [solar cooker](https://github.com/solar-cooker-UHasselt) testing station, the
firmware ([arduino-code](https://github.com/solar-cooker-UHasselt/arduino-code))
writes every measurement to CSV files on the card over SPI.

[![3D render of the board, top side](https://solar-cooker-uhasselt.github.io/kicad-adafruit-microsd/microSD-render-top.png)](https://solar-cooker-uhasselt.github.io/kicad-adafruit-microsd/)

- [Board page](https://solar-cooker-uhasselt.github.io/kicad-adafruit-microsd/): 3D
  renders, drawings, schematic and board PDF, interactive BOM and the BOM CSV for
  Eurocircuits, rebuilt by CI on every push to `main`
- [PCB source](https://github.com/adafruit/MicroSD-breakout-board): Adafruit's Eagle
  files
- [Adafruit guide](https://learn.adafruit.com/adafruit-micro-sd-breakout-board-card-tutorial):
  pinout, wiring, card formatting and Arduino examples

## Installation

### Requirements

- [KiCad 10](https://www.kicad.org/download/), to open and edit the board
- [git](https://git-scm.com), to clone the repo
- Optional, for the checks: [just](https://just.systems)

### Clone

```bash
git clone https://github.com/solar-cooker-UHasselt/kicad-adafruit-microsd.git
```

Own symbols, footprints and 3D models are in `external/`, in the repo itself.

## Usage

Open `microSD.kicad_pro` in KiCad 10. The schematic and board open from there.

Before committing, run ERC and DRC, reports in `tmp/`:

```bash
just check
```

`just --list` shows the other recipes: PDFs, and the CI workflow run locally.

## Contributing

- Work on a branch and open a pull request to `main`. It merges once CI passes and a code
  owner (listed in [.github/CODEOWNERS](.github/CODEOWNERS)) approves it. `main`
  accepts no force pushes.
- CI runs ERC and DRC on every pull request, through the shared workflows in
  [kicad-ci](https://github.com/solar-cooker-UHasselt/kicad-ci). `just check` runs the
  same check locally. A push to `main` that changes more than Markdown also rebuilds
  the board page.
- Commits follow Conventional Commits, with one change per commit. Types, scopes and the
  ERC/DRC check are in
  [.agents/commit_conventions.md](.agents/commit_conventions.md).
- Changes to the board setup, CI or docs are made and tested in
  [kicad-adafruit-ds3231](https://github.com/solar-cooker-UHasselt/kicad-adafruit-ds3231)
  first, then copied here.

## Authors and acknowledgment

The board is Adafruit's design, by Limor Fried/Ladyada for Adafruit Industries
([PCB source](https://github.com/adafruit/MicroSD-breakout-board)). The KiCad 10 port is
by Lowie Van Vyve for the UHasselt solar cooker project.

Adafruit invests time and resources providing this open source design. Please support
Adafruit and open-source hardware by purchasing products from
[Adafruit](https://www.adafruit.com).

<details>
<summary>Adafruit's original README, included as its license asks</summary>

> **Adafruit MicroSD breakout board PCB**
>
> [Click here to purchase one from the Adafruit shop](http://www.adafruit.com/products/254)
>
> Not just a simple breakout board, this microSD adapter goes the extra mile - designed
> for ease of use.
>
> - Onboard 5v->3v regulator provides 150mA for power-hungry cards
> - 3v level shifting means you can use this with ease on either 3v or 5v systems
> - Uses a proper level shifting chip, not resistors: less problems, and faster
>   read/write access
> - Use 3 or 4 digital pins to read and write 2Gb+ of storage!
> - Activity LED lights up when the SD card is being read or written
> - Four #2 mounting holes
> - Push-push socket with card slightly over the edge of the PCB so its easy to insert
>   and remove
> - Comes with 0.1" header (unattached) so you can get it on a breadboard or use wires -
>   your choice
> - Tested and assembled here at the Adafruit factory
> - Works great with Arduino, with tons of example code and wiring diagrams
>
> This repo contains the PCB files for the Adafruit SPI Micro SD (transflash) breakout
> board
>
> **License**
>
> Adafruit invests time and resources providing this open source design, please support
> Adafruit and open-source hardware by purchasing products from
> [Adafruit](https://www.adafruit.com)!
>
> All text above must be included in any redistribution
>
> Designed by Limor Fried/Ladyada for Adafruit Industries. Creative Commons
> Attribution/Share-Alike, all text above must be included in any redistribution. See
> license.txt for additional information.

</details>

## License

[CC BY-SA 4.0](LICENSE). Adafruit's original design is licensed CC BY-SA 3.0, which
allows adaptations like this port under a later version with the same terms.
