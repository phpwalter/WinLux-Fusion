# Configuring OpenSSL

OpenSSL, an open-source tool, is a robust cryptographic library widely used to secure communications over computer networks. Its versatility and powerful encryption algorithms make it an essential tool for many developers and system administrators. Configuring OpenSSL on a Windows environment can seem daunting for beginners, but with step-by-step guidance, you can swiftly set it up and harness its capabilities.

### Download and Installation

- Pull the latest binary from `https://wiki.overbyte.eu/wiki/index.php/ICS_Download`
- Decompress package into `L:\etc\openssl`
- Add new ENVIRONMENTAL VARIABLE
  - Name: openssl
  - Value: `%etc%\openssl`
- Add `%openssl%` to PATH
- Verify your installation with this command prompt
  - Open Command Window
  - Enter: `openssl version`
  - It should respond with:
```shell
OpenSSL 3.1.3 19 Sep 2023 (Library: OpenSSL 3.1.3 19 Sep 2023)
```



