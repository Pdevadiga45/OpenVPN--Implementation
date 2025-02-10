# OpenVPN - Secure VPN Project

This project demonstrates the implementation of a secure VPN tunnel using OpenVPN. It includes configuration files for both the OpenVPN server and client, enabling a secure, encrypted connection between two devices on different networks.

## Overview

The goal of this project is to set up a functioning OpenVPN server and client such that all data transmitted over the tunnel is encrypted and secure. In this setup, the server runs on one device (with a public IP or properly forwarded port) and the client (on a separate Wi‑Fi network) connects using that public IP. The project includes:

- **Server Configuration (`server.ovpn`):** Configures the OpenVPN server with settings for the VPN network, TLS authentication, and encryption.
- **Client Configuration (`client.ovpn`):** Configures the OpenVPN client to connect securely to the server.
- **Certificates and Keys:** Generated using EasyRSA (instructions for generating these are provided in the project documentation).

## Requirements

- **Operating System:** Windows 10 (64-bit) or later.
- **Software:** OpenVPN 2.6.13 (use the `OpenVPN-2.6.13-I001-amd64.msi` installer).
- **Network Requirements:** UDP port 1194 must be open and forwarded (if behind NAT) on the server’s network.
- **Certificates/Keys:** CA, server, and client certificates and keys, along with the TLS authentication key (`ta.key`), generated via EasyRSA.

## Setup and Usage

### Server Setup

1. **Install OpenVPN:**  
   Run the installer `OpenVPN-2.6.13-I001-amd64.msi` as an administrator.

2. **Copy Files:**  
   Place the following files into the OpenVPN config directory (typically `C:\Program Files\OpenVPN\config\`):
   - `server.ovpn` (provided in this repo)
   - `ca.crt`
   - `server.crt`
   - `server.key`
   - `dh.pem`
   - `ta.key`

3. **Run the Server:**  
   Launch the OpenVPN GUI (right-click and select "Run as administrator") and start the server using the provided `server.ovpn` configuration.

### Client Setup

1. **Install OpenVPN:**  
   Install OpenVPN on your friend’s device.

2. **Copy Files:**  
   Place the following files into the client’s OpenVPN config directory:
   - `client.ovpn` (provided in this repo; update the `remote` directive with the server’s public IP or domain)
   - `ca.crt`
   - `client1.crt`
   - `client1.key`
   - `ta.key`

3. **Run the Client:**  
   Launch the OpenVPN GUI (run as administrator) and connect using the `client.ovpn` configuration.

### Testing the Connection

- **Ping Test:**  
  After a successful connection, open a command prompt on the client device and run:
  ```
  ping 10.8.0.1
  ```

  A successful ping confirms that the VPN tunnel is established and that packets are securely transmitted between the client and server.
