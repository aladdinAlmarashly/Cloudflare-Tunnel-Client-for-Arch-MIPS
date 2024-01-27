# Cloudflare Tunnel Client for Arch MIPS

This repository hosts the MIPS architecture-compatible build of the Cloudflare Tunnel client, specifically tailored for use with devices like the Xiaomi Router 3G running with openWRT. This build was derived from Cloudflare's official Tunnel client release `2024.1.5`.

## Background

I created this build to establish a Cloudflare Tunnel with our Xiaomi Router 3G running with openWRT, which operates on a MIPS architecture. After extensive testing and not finding any existing solutions, We successfully compiled a compatible version for MIPS architecture.

## Release

The Cloudflare Tunnel client release `2024.1.5` used for this build can be found at:
[Cloudflare Tunnel Client 2024.1.5 Release](https://github.com/cloudflare/cloudflared/releases/tag/2024.1.5)

## Contents

This repository contains two main files:
1. The binary file `cloudflared` for MIPS architecture.
2. The init script `cloudflared` for service management.

## Installation

To install and run this Cloudflare Tunnel client on your MIPS-based device, follow these steps:

1. **Upload the Binary:**
   - Transfer the `cloudflared` binary to `/usr/bin/cloudflared` on your device.

2. **Configure and Upload the Init Script:**
   - Modify the `cloudflared` init script to include your specific token.
   - Upload the modified init script to `/etc/init.d/cloudflared`.

3. **Make Executable:**
   - Run `chmod +x /usr/bin/cloudflared` to make the binary executable.
   - Run `chmod +x /etc/init.d/cloudflared` to make the binary executable.

4. **Start the Service:**
   - To start the Cloudflare Tunnel, use `/etc/init.d/cloudflared start`.

5. **Enable Service on Boot:**
   - To have the Cloudflare Tunnel start on boot, use `/etc/init.d/cloudflared enable`.

6. **Monitoring Logs:**
   - To monitor the logs, use `logread -f`.

## Configuration

The included configuration file should be modified to include your specific Cloudflare Tunnel token. This step is crucial for the service to connect to your Cloudflare account and function correctly.

## Contributing

Contributions to improve the build or add features are welcome. Please follow the standard procedures for contributing to open-source projects on GitHub.

## Disclaimer

This build is provided as-is, and while it has been tested on Xiaomi Router 3G, it may or may not work on other MIPS architecture devices. Please use it at your own risk.

## Contributors

This project exists thanks to all the people who contribute. A special thanks to:

1. **Omar Marashly:** [Omar's GitHub Profile](https://github.com/omarMarashly)
2. **Aladdin Almarashly (Me):** [My GitHub Profile](https://github.com/aladdinAlmarashly)
3. **Aziz Marashly:** [Aziz's GitHub Profile](https://github.com/aziz-marashly)

## License

This project is distributed under the same license as the original Cloudflare Tunnel client. Refer to the license details in the original [Cloudflare Tunnel client repository](https://github.com/cloudflare/cloudflared).



