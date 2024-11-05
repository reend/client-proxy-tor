# Toralize: Redirect Network Connections through Tor

This program utilizes the SOCKS4 protocol to redirect network connections through the Tor network, providing enhanced privacy and anonymity.

## Starting Tor

Ensure that Tor is installed on your system.Before using the program, start the Tor service to ensure it is running as a local proxy:

```bash
sudo systemctl start tor
sudo systemctl enable tor
```

- `start`: Initiates the Tor service.
- `enable`: Ensures Tor starts automatically on system boot.

## Building the Project

Compile the project by running:

```bash
make
```

This command will compile the `toralize.c` file into a shared object `toralize.so`, which is used to override the standard `connect` function.

## Usage

To redirect a network request through Tor, use the `toralize` script. For example, to access a Google IP (you can use any IP address):

```bash
./toralize curl http://172.217.16.164
```

- `172.217.16.164` is an IP address for Google. Using an IP address instead of a hostname can enhance privacy by avoiding DNS lookups.

### Note

While you can use hostnames, using direct IP addresses is recommended for better privacy, as it prevents DNS queries from revealing your browsing intentions.

## How It Works

1. **LD_PRELOAD**: The `toralize` script uses `LD_PRELOAD` to load `toralize.so`, which overrides the standard `connect` function.
2. **SOCKS4 Protocol**: The program creates a SOCKS4 request to the local Tor proxy, redirecting the connection through the Tor network.
3. **Anonymity**: By routing connections through Tor, your real IP address is hidden from the destination server.

## Disclaimer

This tool is intended for educational purposes and should be used responsibly. Ensure compliance with all applicable laws and regulations when using Tor and this software.