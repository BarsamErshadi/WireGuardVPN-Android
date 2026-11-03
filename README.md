# WireGuardVPN for Android

A native Android VPN client built with Kotlin and Jetpack Compose. It connects over WireGuard, and adds stealth modes that tunnel traffic through an obfuscated SOCKS5 bridge for networks that block regular VPN traffic.

## Features

- **Three connection modes:** direct WireGuard (UDP), Stealth, and WARP (via Cloudflare).
- **Custom tunnel bridge:** `TunProxy` reads raw IP packets from Android's TUN interface and relays them through a SOCKS5 proxy: TCP via CONNECT, DNS over TCP, and other UDP traffic (games, QUIC) via UDP ASSOCIATE.
- **Exit network choice:** send stealth traffic out through a residential or a direct (datacenter) exit.
- **Server management:** add WireGuard servers (keys, address, endpoint, allowed IPs); profiles are stored encrypted with AES-256 (EncryptedSharedPreferences).
- **Live dashboard:** connection status, upload and download speed, session totals and uptime.
- **Verified in-app updates:** checks `update.json`, downloads the new APK and verifies its SHA-256 hash before installing.
- **DNS choice:** pick the DNS server used inside the tunnel.

## Tech stack

Kotlin · Jetpack Compose (Material 3) · Navigation Compose · ViewModel and coroutines · Android `VpnService` · WireGuard Go backend · sing-box · kotlinx.serialization · AndroidX Security Crypto

Min SDK 26 (Android 8.0) · Target SDK 36

## Project structure

```
app/src/main/java/com/barsam/wireguardvpn/
├── ui/          Compose screens: dashboard, servers, traffic, settings
├── services/    VpnService, TunProxy (SOCKS5 bridge), encrypted profile store, update manager
└── models/      WireGuard config parsing and connection models
```

## Install

Download the latest APK from [Releases](https://github.com/BarsamErshadi/WireGuardVPN-Android/releases).
