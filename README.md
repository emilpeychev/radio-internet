# LoRa-Based Internet Distribution Network

## Project Overview

This project aims to create a LoRa-based network for distributing internet access within a limited bandwidth of 300 kbps, which is equivalent to a 2G connection. The setup will utilize Raspberry Pi devices as gateways and the HopeRF RFM95W-868S2 modules for transmitting data. This network will enable browsing and text communication within the LoRa network coverage area.

## Hardware Requirements

| **Component**             | **Description**                                                                                  | **Quantity** | **Approx. Cost** |
|---------------------------|--------------------------------------------------------------------------------------------------|--------------|------------------|
| Raspberry Pi (3x)         | Acts as the LoRa gateway and central controller                                                   | 3            | $35 each         |
| RFM95W-868S2 Module       | LoRa transceiver module, used for both gateway and client devices                                 | 3+            | $10 each         |
| CrossAir CA-S01 Antenna   | High-gain (7.2 dBi) ceramic antenna for improved signal strength                                 | 3+            | $5 each          |
| Sleeve Dipole Antenna     | For urban areas, to be used with the gateway for better signal coverage                           | 1+            | $15 each         |
| Moxon Antenna             | For open areas, to be used with the gateway for longer-range signal transmission                  | 1+            | $25 each         |
| USB-to-SPI Adapter        | For connecting RFM95W to PC, if needed for configuration or direct communication                  | 1+            | $10 each         |
| Voltage Regulator         | For regulating voltage to RFM95W (3.3V from Raspberry Pi GPIO)                                    | 3            | $2 each          |
| Casing & Moisture Shield  | To protect the hardware, using hot glue or silicone gel                                           | N/A          | Varies           |

## Software and Firmware

| **Software/Firmware**     | **Purpose**                                                                                       | **Installation/Setup** |
|---------------------------|---------------------------------------------------------------------------------------------------|------------------------|
| Raspbian OS               | Operating system for Raspberry Pi                                                                 | Pre-installed          |
| SiK Firmware              | Open-source firmware for RFM95W-868S2 (optional, other firmware options are available)             | Download and flash     |
| MQTT Gateway Software     | Software to manage message queue and routing                                                      | Install via apt        |
| Squid Proxy               | Caching server for compressing and caching data                                                   | Install via apt        |
| FFmpeg                    | For video and audio compression/transcoding                                                       | Install via apt        |
| Gzip/Brotli               | Compression algorithms for web traffic                                                            | Configure in Nginx     |
| LoRaWAN Stack (Optional)  | For easier management of multiple LoRa gateways and cloud integration                             | Optional               |

## Network Architecture

### Basic Network Schema

1. **Raspberry Pi with RFM95W-868S2**:
    - Acts as the LoRa gateway and connects to the internet via Ethernet.
    - Transmits data through LoRa using the CrossAir CA-S01 antenna.
    - Supports multiple antennas for different environments (e.g., urban and open areas).

2. **Client Devices (PC/Mobile) with RFM95W-868S2**:
    - Equipped with RFM95W-868S2 and corresponding antennas.
    - Communicates directly with the LoRa network.

3. **Data Flow**:
    - Internet -> Raspberry Pi (Ethernet) -> LoRa Gateway (RFM95W) -> LoRa Clients (RFM95W on PC/Mobile).

## Antenna Comparison

| **Antenna**               | **Frequency Range** | **Gain**  | **Type**       | **Connector** | **Applications**                       |
|---------------------------|----------------------|-----------|----------------|---------------|---------------------------------------|
| **CrossAir CA-S01**       | 433 MHz, 868 MHz, 915 MHz | 5.7 dBi (avg), 7.2 dBi (max) | Ceramic Patch  | SMD PCB       | Short and long-range communications     |
| **Sleeve Dipole**         | 433 MHz              | 3 dBi     | Dipole         | SMA Connector | Urban areas, broad signal coverage       |
| **Moxon Antenna**         | 868 MHz              | 7 dBi     | Yagi           | SMA Connector | Open areas, long-range signal coverage   |

## Recommended Alternatives

### LoRa Gateway Solutions

1. **LoRaWAN Gateway**:
    - **Benefits**: Better integration with cloud-based services, easier management of multiple devices.
    - **Considerations**: Higher cost compared to simple LoRa transceivers.

2. **USB-to-SPI Adapter**:
    - **Purpose**: Allows connection of RFM95W to a PC for direct communication or configuration.
    - **Note**: Ensure compatibility with the RFM95W module.

### Antenna Choices

1. **For Urban Areas**: Sleeve Dipole Antenna
    - **Advantages**: Provides good coverage and is cost-effective for urban environments.

2. **For Open Areas**: Moxon Antenna
    - **Advantages**: Higher gain and better suited for longer distances in open areas.

## Additional Configuration and Considerations

- **Caching and Compression**: Use Squid Proxy, FFmpeg, and Gzip/Brotli to manage and compress data traffic for better performance.
- **Moisture Protection**: Use hot glue or silicone gel to shield hardware from moisture.
- **Voltage Regulation**: Use a 3.3V voltage regulator for the RFM95W module to ensure stable operation.

## Conclusion

This setup provides a comprehensive solution for creating a LoRa-based internet distribution network with Raspberry Pi devices and RFM95W modules. By selecting the appropriate antennas and configuration options, you can achieve reliable data transmission and internet access within the given bandwidth constraints.

