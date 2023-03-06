rpi-pico-builder
==========
Based upon https://github.com/xingrz/rpi-pico-builder

Build environment for Raspberry Pi Pico (RP2040) C/C++ SDK

```sh
docker pull kmpm/rpi-pico-builder:latest
```

## Usage

### Linux

1. Clone [pico-sdk](https://github.com/raspberrypi/pico-sdk)
2. Clone [pico-examples](https://github.com/raspberrypi/pico-examples), or [set up](https://github.com/raspberrypi/pico-sdk#quick-start-your-own-project) your own project
3. ```sh
   docker run --rm -it \
    -v /path/to/your/pico-sdk:/pico-sdk \
    -v /path/to/your/pico-examples:/project \
    kmpm/rpi-pico-builder:latest \
    bash -c 'mkdir -p build && cd build && cmake .. && make blink'
   ```
4. Copy `build/blink/blink.uf2` into the RPI-RP2 drive

### Windows - Powershell
You can do almost the same as above but the `docker run` part needs some changing.
- Powershell uses backticks instead of backslash for breaking lines.
- the volume parameters needs to be quoted and with absolute path.
  `$(Get-Location)`returns the same as `pwd`in linux shell.


```powershell
docker run --rm -it `
   -v "$(Get-Location)/3rdparty/pico-sdk:/pico-sdk" `
   -v "$(Get-Location):/project" `
   kmpm/rpi-pico-builder:latest `
   bash -c 'cd build && make'
```
