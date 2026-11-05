# PlxNative for Samsung Tizen

An experimental port of [PlxNative](https://github.com/GLinnik21/plx-native) for the
2019 Samsung The Frame running Tizen 5.0 on ARMv7. The goal is a native Plex client
that can be installed through Samsung Developer Mode without rooting the TV.

## Current status

- **Built locally.** The offline preview uses PlxNative’s Rust renderer, focus
  engine and Plex response parser to show three sample titles. Its Samsung host
  uses Tizen Multimedia Player to play bundled H.264 video with AAC audio.
- **Verified on the Mac.** The 1920×1080 preview rendered and passed navigation
  checks. The ARM build and signed Tizen package passed local checks.
- **TV test pending.** A separate probe ran Rust, drew graphics, handled remote
  input and played video with sound on the target Frame without root. The Plex
  preview itself still needs its first install and playback test on that TV.

The preview has no Plex sign-in, connection to a Plex server or playback from a
real Plex library. Search, subtitles, seeking, resume and broader TV compatibility
are outside this first milestone. There is no Tizen release to download yet.
The preview source and build notes are in `ports/tizen/` on the local development branch.

## Credits

- [PlxNative by Gleb Linnik and contributors](https://github.com/GLinnik21/plx-native)
  provides the upstream Rust code. The upstream project has the LG webOS guides,
  screenshots and releases.
- [Nuvio Native Legacy by iqui27 and contributors](https://github.com/iqui27/nuvio-native-legacy/blob/7cac4f25d11931b56c41cfefb952e4e183c45c1a/tizen-tpk/NuvioTpk40/Program40.cs)
  provided the Tizen 4/5 .NET host pattern and the in-memory ARM loader we adapted
  for compiled Rust. For this port, Rust’s thread-local storage uses pthread
  keys so the library works with the loader’s constraints.
- [SamsungDForum’s JuvoPlayer](https://github.com/SamsungDForum/JuvoPlayer) is the
  reference Nuvio credits for the `TVGLApplication` graphics host and separate
  native video window.

The port and the adapted loader are licensed under [GPL-3.0-or-later](LICENSE).
