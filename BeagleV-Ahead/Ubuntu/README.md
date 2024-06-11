# Ubuntu BeagleV-Ahead Test Report

## Test Environment

### System Information

- Download link: https://files.beagle.cc/file/beagleboard-public-2021/images/xuantie-ubuntu-23.04-20230705.zip
- Reference installation document: https://docs.beagleboard.org/latest/boards/beaglev/ahead/02-quick-start.html

### Hardware Information

- BeagleV-Ahead
- USB-C Power Adapter / DC power supply
- USB-UART debugger

## Installation Steps

### Image Flashing

Install fastboot:
```bash
sudo apt-get install android-sdk-platform-tools
```

Unpack the installation package. Run the automatic flashing script:

```bash
unzip xuantie-ubuntu-23.04-20230705.zip
sudo ./fastboot_emmc.sh
```

### Logging into the System

Login to the system via serial port.

Default username: `root`
Default password: No password

## Expected Results

The system boots up successfully and can be logged into through the onboard serial port.

## Actual Results

The system boots up successfully, and login via the onboard serial port is successful.

### Boot Messages

Screen recording (from flashing the image to logging into the system):

```log

```

## Test Judgment Criteria

Test Success: Actual results match the expected results.

Test Failure: Actual results do not match the expected results.

## Test Conclusion

CFT
