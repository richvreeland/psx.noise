# 🕹️ psx noise

Galois LFSR — a 16-bit PRNG white noise generator derived from the Sony Playstation's Sound Processing Unit.

## Implementation Notes

- 16-bit Galois LFSR with taps at bits 10, 11, 12, 15
- Parity bit calculation: XOR(bit15, bit12, bit11, bit10) XOR 1
- Timer decrements by (step + 4) at 44.1kHz sample rate
- Timer resets to (0x20000 >> shift) when reaching 0
- Shift changes reset timer immediately (FF7 compatibility)
- Using ScriptProcessorNode for maximum browser compatibility

## Export Feature

- Exports all 64 combinations (4 steps × 16 shifts)
- Files trimmed to complete cycles for perfect seamless looping
- Duration ~2 seconds (exact length varies to match cycle boundaries)
- 1+ second preroll removed to eliminate fade-in artifacts
- 44.1kHz sample rate, 16-bit mono WAV format
- Files named by output frequency for easy sorting
- Filename format: psx_noise_{freq}Hz.wav
- Frequency range: ~67Hz to 15,750Hz

## Credits

Based on the PlayStation SPU noise generator implementation [described by jsgroth](https://jsgroth.dev/blog/posts/ps1-spu-part-4/).
