# DTMF Encoder/Decoder

This project is a Dual-Tone Multi-Frequency (DTMF) encoder and decoder, developed as part of the **High Performance Coding** class. The system is designed to encode a text message into DTMF tones and decode the tones back into text.

## Features
- Encode text messages into DTMF tones stored in a `.wav` file
- Decode DTMF tones using two different methods:
  - **Frequency-based decoding** (using Fourier Transform)
  - **Time-domain decoding** (using correlation analysis)
- High-performance implementation with execution time analysis

## Quick Start Guide
### 1. Compile the project
```sh
mkdir -p build
cd build
cmake ..
make -j$(nproc)
cd ..
```

### 2. Encode a message
Save your message in a text file:
```sh
echo "hello, world!" > message.txt
```
Then encode it into a `.wav` file:
```sh
./build/dtmf_encdec encode message.txt message.wav
```
Example output:
```
Encoding alone took 0.014179 seconds
```

### 3. Decode the message
#### Frequency-based decoder:
```sh
./build/dtmf_encdec decode message.wav
```
Example output:
```
Using 0.539966 as silence amplitude threshold
Decoding alone took 0.017162 seconds
Decoded: hello, world!
```

#### Time-domain decoder:
```sh
./build/dtmf_encdec decode_time_domain message.wav
```
Example output:
```
Using 0.539966 as silence amplitude threshold
Decoding alone took 0.001462 seconds
Decoded: hello, world!
```

## Constraints and Limitations
This implementation assumes:
1. A fixed duration of **0.2s per character**.
2. A **0.2s pause** between characters.
3. A **0.05s pause** between multiple keypresses for the same character.

## Report
The report for this project's, in french, can be found [here](docs/Report.pdf)


## Disclaimer
This project was developed for educational purposes as part of a **High Performance Coding** course. While optimized for speed, it is not intended for production use in critical systems.

## License
This project is released as open-source under the MIT License. Feel free to contribute or modify as needed!
