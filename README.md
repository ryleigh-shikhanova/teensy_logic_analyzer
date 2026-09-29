# Teensy 8080 Logic Analyzer

A Teensy-based logic analyzer and test harness for monitoring an Intel 8080 CPU.

The Teensy connects directly to the 8080's address, data, and control buses and records CPU activity for debugging and emulator verification.

## Goals

- Monitor the 8080 address bus
- Monitor the 8080 data bus
- Capture control signals such as `SYNC`, `DBIN`, `WR`, `INT`, `HOLD`, and `HLDA`
- Log instruction and memory activity
- Use captured hardware behavior to verify an Intel 8080 emulator
- Eventually generate automated emulator tests from real CPU traces

## Hardware

Current setup includes:

- Teensy
- Intel 8080 CPU
- Intel 8224 clock generator
- Intel 8228 system controller
- SRAM
- Level/bus buffering hardware
- External +5 V, +12 V, and -5 V power supplies

## Bus Layout

The Teensy treats groups of pins as logical buses.

```cpp
constexpr uint8_t ADDRESS_PINS[16] = {
    // A0-A15
};

constexpr uint8_t DATA_PINS[8] = {
    // D0-D7
};
```

Control signals are defined individually:

```cpp
constexpr uint8_t PIN_SYNC = 0;
constexpr uint8_t PIN_DBIN = 0;
constexpr uint8_t PIN_WR   = 0;
constexpr uint8_t PIN_INT  = 0;
constexpr uint8_t PIN_HOLD = 0;
constexpr uint8_t PIN_HLDA = 0;
```

Actual pin assignments will be documented as the hardware design is finalized.

## Planned Features

- High-speed GPIO sampling
- Address and data bus decoding
- 8080 machine-cycle detection
- Instruction tracing
- Memory read/write logging
- Interrupt logging
- HOLD/HLDA bus arbitration
- Serial trace output
- Emulator test generation from hardware traces

## Project Status

Early development.

The current focus is wiring the 8080 system and implementing reliable bus capture on the Teensy.

## Related Projects

This project is intended to work alongside my Intel 8080 emulator and provide traces from real hardware that can be compared against emulator behavior.

## License

TBD
