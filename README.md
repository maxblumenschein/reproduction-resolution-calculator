# Reproduction Resolution Calculator

A single-file browser tool for planning flat-art digitisation setups. Given a camera sensor, a lens, and an artwork size (or a target distance or DPI), it calculates the achievable resolution, coverage, working distance, depth of field, and optical magnification.

## Features

- **Three solve modes**
  - *Artwork size → Distance + DPI* — enter the artwork dimensions, get the required camera-to-artwork distance and resulting DPI
  - *Distance → Artwork + DPI* — enter the sensor-plane-to-artwork distance, see what area is covered and at what DPI
  - *Target DPI → Artwork + Distance* — enter a desired DPI and optionally an artwork size, get the required working distance
- **Sensor presets** — Fujifilm GFX100S, GFX100S Multishot 4×, Nikon D850, Opus Apollo IR, i2s Suprascan 80mm
- **Artwork presets** — A4–A0, common centimetre formats, imperial sheet film sizes
- **Margin offset** — adds a configurable border around the artwork before calculating
- **Optical detail** — repro ratio, lens extension, effective aperture, depth of field, ground sample distance
- **Diagram** — schematic cross-section of the optical path with labelled distances

## Usage

Open `repro-resolution_calculator.html` directly in any modern browser. No build step, no dependencies beyond the Google Fonts stylesheet.

## Calculations

Thin-lens formula: `1/f = 1/u + 1/v`, where `u` is the object distance (lens principal plane to artwork) and `v` is the image distance (lens to sensor). The total sensor-plane-to-artwork distance is `T = u + v`.

- **Magnification** `M = v / u = sensor_size / artwork_coverage`
- **DPI** `= pixel_count × 25.4 / coverage_mm`
- **Effective aperture** `N_eff = N × (1 + M)`
- **Depth of field** `= 2 × CoC × N_eff / M²` (CoC = 2 × pixel pitch)

Camera orientation (portrait vs. landscape) is chosen automatically to maximise magnification for the given artwork.
