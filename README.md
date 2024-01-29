# Cloudflare Tunnel Client for Arch MIPS

This repository hosts the MIPS architecture-compatible build of the Cloudflare Tunnel client, specifically tailored for use with devices like the Xiaomi Router 3G running with openWRT. This build was derived from Cloudflare's official Tunnel client release `2024.1.5`.

## Background

I created this build to establish a Cloudflare Tunnel with our Xiaomi Router 3G running with openWRT, which operates on a MIPS architecture. After extensive testing and not finding any existing solutions, We successfully compiled a compatible version for MIPS architecture.

## Release

The Cloudflare Tunnel client release `2024.1.5` used for this build can be found at:
[Cloudflare Tunnel Client 2024.1.5 Release](https://github.com/cloudflare/cloudflared/releases/tag/2024.1.5)

## Contents

This repository contains two main files:
1. The binary file of cloudflard releases `cloudflared` for MIPS architecture.
2. The service script `cloudflared` for service management.

## Installation

To install and run this Cloudflare Tunnel client on your MIPS-based device, follow these steps:

### For Who Has Enough Disk Space

1. **Upload the Binary:**
   - Transfer the `cloudflared` binary to `/usr/bin/cloudflared` on your device.

2. **Configure and Upload the Service Script:**
   - Modify the `cloudflared` service script to include your specific token.
   - Upload the modified service script to `/etc/init.d/cloudflared`.

3. **Make Executable:**
   - Run `chmod +x /usr/bin/cloudflared` to make the binary executable.
   - Run `chmod +x /etc/init.d/cloudflared` to make it executable.

4. **Start the Service:**
   - To start the Cloudflare Tunnel, use `/etc/init.d/cloudflared start`.
   - You can also use stop and status.

5. **Enable Service on Boot:**
   - To have the Cloudflare Tunnel start on boot, use `/etc/init.d/cloudflared enable`.

6. **Monitoring Logs:**
   - To monitor the logs, use `logread`.

### For Who Has Problem With Disk Space

Like Xiaomi router 4A Gigabit that came with 16 MB disk space for that every time the router boot they will install the binary file from the internet.

1. **Configure and Upload the Service Script:**
   - Modify the `cloudflared` service script to include your specific token and you can change the release you want.
   - Upload the modified service script to `/etc/init.d/cloudflared`.

2. **Make Executable:**
   - Run `chmod +x /etc/init.d/cloudflared` to make it executable.

3. **Start the Service:**
   - To start the Cloudflare Tunnel, use `/etc/init.d/cloudflared start`.
   - You can also use stop and status.

4. **Enable Service on Boot:**
   - To have the Cloudflare Tunnel start on boot, use `/etc/init.d/cloudflared enable`.

5. **Monitoring Logs:**
   - To monitor the logs, use `logread`.

## Build Your Own Binary File

If you prefer to build your own binary file for the Cloudflare Tunnel client, follow these steps:

1. **Use a Linux Environment:**
   - Ensure you are working in a Linux environment as it provides the necessary tools and compatibility for building the binary.

2. **Install Go Language:**
   - Make sure Go language (GoLang) is installed on your system. You can download and install it from the [official Go website](https://golang.org/dl/).

3. **Download Cloudflare Tunnel Client Release:**
   - Download the Cloudflare Tunnel client release version you wish to build from the [Cloudflare Tunnel Client Releases](https://github.com/cloudflare/cloudflared/releases) page on GitHub.

4. **Navigate to the Build Directory:**
   - After extracting the downloaded release, navigate to the `cloudflared/cmd/cloudflared/` directory in the terminal.

5. **Run the Build Command:**
   - Execute the following command to build the binary for MIPS architecture:

     ```bash
     CGO_ENABLED=0 GOOS=linux GOARCH=mipsle GOMIPS=softfloat go build -a -installsuffix cgo -ldflags "-s -w -extldflags '-static'" .
     ```

6. **Locate the Built Binary:**
   - Upon successful completion of the build process, you will find a file named `cloudflared` in the same directory. This is your MIPS-compatible binary.

**Note:** The build command provided sets several environment variables to ensure compatibility with MIPS architecture. `CGO_ENABLED=0` disables CGo, enabling a fully static binary. `GOOS=linux` and `GOARCH=mipsle` target the Linux operating system and MIPS (little-endian) architecture, respectively. `GOMIPS=softfloat` ensures compatibility with systems not supporting hardware floating-point operations.


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



