Epiphyte
Peer-to-peer encrypted messenger over Tor. No servers. No phone numbers. No sign-up.

What is this
Epiphyte is a desktop chat application where each user runs their own Tor hidden service. When you open the app, it starts an embedded Tor process, generates a .onion address, and listens for incoming connections. To talk to someone, you exchange .onion addresses and connect directly. Messages never touch a third-party server.

How it works
Each instance of Epiphyte acts as both a client and a server. Your device hosts a Tor hidden service that your contacts connect to, and you connect to theirs. Messages are encrypted end-to-end before leaving your machine, and the Tor network handles routing so neither party reveals their IP address.

If a contact is offline, messages are queued locally and delivered automatically when they come back online.

Encryption
X25519 key exchange with a Double Ratchet protocol for forward secrecy
XSalsa20-Poly1305 for message encryption
Ed25519 signatures for authentication
Post-quantum hybrid layer mixed into the key derivation
Every message uses a new ephemeral key. Compromising a long-term key does not expose past messages.
Censorship resistance
Epiphyte bundles Tor with pluggable transports for use in censored networks:

Snowflake (WebRTC-based, effective in China)
obfs4 (randomized traffic obfuscation)
meek-azure (CDN fronting)
Users in censored regions select "Bridge" mode during setup. The app handles the rest.

Offline delivery
For situations where internet access is unavailable or too dangerous, Epiphyte supports exporting encrypted messages to files (for USB transfer) or QR codes. Only the intended recipient can decrypt them.

Requirements
Windows 10 or later
No additional software needed. Tor is bundled.
Building from source

cd epiphyte
build.bat
The build script installs dependencies, downloads the Tor expert bundle, and produces an installer at 
Epiphyte-Setup.exe
.

Limitations
Both users must be online simultaneously for real-time messaging
Tor connections add latency compared to direct internet
The project has not been independently audited
Windows only at this time
