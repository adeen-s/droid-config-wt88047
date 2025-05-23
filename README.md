# Sailfish OS Configuration for Xiaomi Redmi 2 (wt88047)

FAQ: https://github.com/mer-hybris/hadk-faq

Release: [XDA Developers](https://xdaforums.com/t/rom-alpha-sfos-sailfishos-2-0-1-11-for-redmi-2.3395904/page-3)

This repository contains the device-specific configuration files for running Sailfish OS on the Xiaomi Redmi 2 (codename: wt88047). It provides hardware adaptation layers, system configurations, and device-specific settings needed to port Sailfish OS to this Android device.

## Device Information

- **Device**: Xiaomi Redmi 2
- **Codename**: wt88047
- **Vendor**: Wingtech (manufactured for Xiaomi)
- **Architecture**: ARM
- **SoC**: Qualcomm Snapdragon (MSM platform)
- **Display**: 4.7" with 1.33 pixel ratio
- **Modem**: Supported ✅

## What is Sailfish OS?

Sailfish OS is a Linux-based mobile operating system developed by Jolla. This project enables running Sailfish OS on Android devices by utilizing the Android Hardware Abstraction Layer (HAL) through the libhybris compatibility layer.

## Project Structure

```
├── droid-configs-device/     # Submodule with common droid configuration framework
├── patterns/                 # Package pattern definitions
│   ├── jolla-configuration-wt88047.yaml
│   ├── jolla-hw-adaptation-wt88047.yaml
│   └── jolla-ui-configuration-wt88047.yaml
├── rpm/                      # RPM package specification
│   └── droid-config-wt88047.spec
└── sparse/                   # Device-specific configuration files
    ├── etc/                  # System configuration
    ├── lib/                  # System libraries and services
    ├── system/               # Android system integration
    ├── usr/                  # User space binaries and scripts
    └── var/                  # Variable data and environment configs
```

## Supported Features

### ✅ Working Features
- **Display**: Hardware composer integration with Qt5
- **Touch Input**: Touchscreen and hardware keyboard support
- **Audio**: PulseAudio with Android HAL integration
- **Bluetooth**: HCI over SMD with automatic MAC address detection
- **WiFi**: WLAN module support with automatic loading
- **Camera**: Dual camera support (primary 8MP, secondary 2MP)
  - Multiple resolution modes (4:3 and 16:9)
  - Flash, focus, and white balance controls
  - Video recording support
- **GPS**: Location services via hybris
- **FM Radio**: Hardware FM radio support
- **USB**: Multiple USB modes (MTP, mass storage, developer mode)
- **Cellular**: Modem and telephony support
- **SD Card**: Automatic mounting
- **Sensors**: Various hardware sensors
- **LED Notifications**: Hardware notification LED support

### 📱 Camera Specifications
- **Primary Camera**: 3264x2448 (8MP), 1920x1080 video
- **Secondary Camera**: 1600x1200 (2MP), 1280x720 video
- **Features**: Auto/manual focus, flash modes, ISO control, white balance

### 🔊 Audio Features
- **PulseAudio**: Android HAL integration
- **Call Audio**: In-call audio routing
- **Media Playback**: GStreamer 1.0 multimedia framework
- **Audio Recording**: Qt5 multimedia capture support

## Installation

This configuration is designed to be used with the Sailfish OS Hardware Adaptation Development Kit (HADK). 

### Prerequisites
- Sailfish OS SDK
- Android source tree for wt88047
- HADK environment set up

### Building
1. Clone this repository into your HADK workspace
2. Initialize the droid-configs-device submodule:
   ```bash
   git submodule update --init --recursive
   ```
3. Follow the standard HADK build process
4. The configuration will be automatically included in the build

## Configuration Highlights

### Hardware Composer
- **Platform**: hwcomposer
- **Graphics**: EGL platform integration
- **Input**: Touch events via `/dev/input/event0`

### Audio Configuration
- **Sample Rate**: 48kHz
- **Channels**: Stereo support
- **Routing**: Automatic audio policy management
- **Bluetooth**: A2DP and HFP support

### System Services
- **Bluetooth**: Automatic HCI initialization
- **WiFi**: Module auto-loading with proper timing
- **USB**: Mode detection and switching
- **GPS**: Qualcomm location services

## Development

### Key Configuration Files
- `sparse/var/lib/environment/compositor/droid-hal-device.conf`: Display and input configuration
- `sparse/etc/pulse/arm_droid_default.pa`: Audio system configuration  
- `sparse/etc/dconf/db/vendor.d/jolla-camera-hw.txt`: Camera hardware settings
- `sparse/usr/bin/droid/droid-hcismd-up.sh`: Bluetooth initialization script

### Customization
Device-specific configurations can be modified in the `sparse/` directory. Changes to hardware parameters should be made carefully and tested thoroughly.

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Test your changes thoroughly
4. Submit a pull request with detailed description

### Reporting Issues
When reporting issues, please include:
- Sailfish OS version
- Hardware revision
- Detailed steps to reproduce
- Relevant log files

## Related Projects

- [Sailfish OS](https://sailfishos.org/) - The mobile operating system
- [libhybris](https://github.com/libhybris/libhybris) - Android HAL compatibility layer
- [droid-hal-configs](https://github.com/mer-hybris/droid-hal-configs) - Common configuration framework

## License

This project follows the licensing terms of the Sailfish OS ecosystem. Individual components may have different licenses - please check specific files for details.
The custom code added by me is licensed under the MIT License. Feel free to use it however you like.

## Acknowledgments

- Jolla and the Sailfish OS community
- mer-hybris project contributors
- Device porters and testers
- Xiaomi for the hardware platform

---

**Note**: This is a community port. Use at your own risk. Always backup your device before flashing custom firmware.
