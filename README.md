# ISO 6346 Container & Chassis Check-Digit Validator — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-container-validator.svg)](https://crates.io/crates/stanzaapi-container-validator)
[![Documentation](https://docs.rs/stanzaapi-container-validator/badge.svg)](https://docs.rs/stanzaapi-container-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> MOD-11 check digit validator and ISO 6346 size/type decoder for intermodal shipping containers, chassis, and trailers.

Official high-performance, asynchronous Rust client library for **ISO 6346 Container & Chassis Check-Digit Validator**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/container-validator)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/container-validator)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-container-validator = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-container-validator
```

---

## 🚀 Quickstart

```rust
use stanzaapi_container_validator::ContainerValidatorClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    let client = ContainerValidatorClient::new(None, None);

    let response = client.validate("MSKU0123456").await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "owner_code": "MSK",
    "category": "U",
    "serial_number": "012345",
    "check_digit": 6
  }
}
```

---

## 🔗 Useful Links

* [ISO 6346 Container & Chassis Check-Digit Validator Interactive Sandbox](https://stanzaapi.com/tools/container-validator)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/stanzaapi/container-validator-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
