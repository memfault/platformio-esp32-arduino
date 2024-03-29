# Sample platformio + espressif32-arduino memfault project

_NOTE: currently this example project is for reference only and does not build!_

## Changes to default project

This project was based on this example:

https://github.com/platformio/platform-espressif32/tree/develop/examples/espidf-arduino-wifiscan

The memfault tree was added with a git submodule:

```bash
❯ git submodule add https://github.com/memfault/memfault-firmware-sdk.git src/memfault/memfault-firmware-sdk
```

The `CMakeLists.txt` and `src/` files were copied over from the memfault example:

```bash
# copy project configuration files
❯ cp -r src/memfault/memfault-firmware-sdk/examples/esp32/apps/memfault_demo_app/{CMakeLists.txt,sdkconfig.defaults} ./
# copy application
❯ cp -r src/memfault/memfault-firmware-sdk/examples/esp32/apps/memfault_demo_app/main/* src/
```

## Testing

To test:

1. install platformio core [from these instructions](https://docs.platformio.org/en/latest//core/installation.html#super-quick-mac-linux):

   ```bash
   python3 -c "$(curl -fsSL https://raw.githubusercontent.com/platformio/platformio/master/scripts/get-platformio.py)"
   ```

2. make sure the `pio` binary is on path. for example you might need to do something like this:

   ```bash
   ln -s ~/.platformio/penv/bin/pio ~/.local/bin/
   ```

3. run the build command:

   ```bash
   pio run
   ```

4. to test on the board (esp-wrover-kit), run these commands to flash the board and open a serial terminal:

   ```bash
   pio run --target upload --target monitor
   ```
