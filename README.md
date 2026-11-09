# NMEA Wi-Fi Bridge

*A small DIY project for getting NMEA 0183 data from a boat's chartplotter or fish finder to a phone or tablet over Wi-Fi.*

I built this because I wanted to get data from my own fish finder onto a mobile device without running another cable across the boat. It turned into a little ESP8266-based project — and I thought it might be useful to other boaters and anglers too.

This is a personal hobby project, not a commercial product. The idea is simple: share what works, document the build, and make it easier for someone else to try.

## What does it do?

The bridge receives NMEA 0183 data from a marine instrument and forwards it over a local Wi-Fi network as UDP packets.

In simple terms:

```text
Chartplotter / fish finder
          |
      NMEA 0183
          |
     RS-422 receiver
          |
       ESP8266
          |
    Wi-Fi / UDP broadcast
          |
     Phone or tablet
```

A navigation app that can receive NMEA data over UDP can then use the information without a direct cable connection to the chartplotter.

- **Wireless connection** — send instrument data to a phone or tablet over Wi-Fi.
- **No cloud account or internet connection required** — the NMEA data is sent over the local network.
- **Simple, inexpensive hardware** — the prototype uses readily available modules.
- **Useful alongside existing equipment** — keep using your chartplotter; the bridge provides another way to access its NMEA output.

## My current setup

The first working version was built and tested with:

| Part | What I used |
|---|---|
| Controller | LOLIN D1 mini V4 (ESP8266) |
| NMEA interface | YL-128 RS-422 receiver board with MAX490 |
| NMEA source | Lowrance Elite-4 HDI |
| NMEA speed | 4800 baud |
| Wireless output | UDP broadcast over Wi-Fi |
| Tested client | Navionics Boating on Android |

This is a tested example, not a list of the only compatible devices. Other chartplotters, fish finders and apps may work too, provided their NMEA settings and UDP support are compatible.

## Current status

The basic NMEA-to-Wi-Fi forwarding works with the setup listed above.

A few things are still evolving:

- Wi-Fi client (STA) mode has been tested.
- Standalone access-point mode is experimental. Connection behaviour, especially with iOS devices, still needs work.
- More chartplotters, phones and navigation apps need to be tested.

I'll add more wiring details, setup notes and troubleshooting tips as the documentation grows.

## Android companion app

There is also a small Android app that discovers the bridge on the local network and opens its web interface:

[NMEA Bridge Android](https://github.com/zoychikf1/NMEA-Bridge-Android)

The companion app is separate from the NMEA data connection. If your navigation app can receive the bridge's UDP broadcast directly, you do not need the discovery app just to receive NMEA data.

## A note about the project

This is a DIY hobby project, not certified marine equipment. It is provided as-is, without warranty. Please check your wiring and installation carefully, and do not rely on it as your only source of navigation or safety information. Your existing marine instruments should remain the primary equipment.

## Tried it on your boat?

I'd be glad to hear about other working combinations. If you test the bridge, please share:

- chartplotter or fish finder model;
- NMEA output settings / baud rate;
- phone or tablet model and operating system;
- navigation app used;
- anything that did not work as expected.

Bug reports, corrections and practical suggestions are welcome. The whole point is to make this useful to fellow boaters and anglers.

---

*Built on a boat, tested on the water, improved when time allows.*
