# esp32-blink-pipeline-test
ESP32 Blink Pipeline Test

Simple example of automatically building, encrypting and uploading an ESP32 firmware.

To build the firmware via Docker, run the command:

```
docker run --rm -v $PWD:/project esp32-blink-pipeline
```

After, run the following command to flash the firmware to a connected board:

```
esptool.py -p (PORT) -b 460800 --before default_reset --after hard_reset --chip esp32  write_flash --flash_mode dio --flash_size detect --flash_freq 40m 0x1000 build/bootloader/bootloader.bin 0x8000 build/partition_table/partition-table.bin 0x10000 build/blink.bin
```

