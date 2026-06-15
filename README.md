# Aurora AI Streaming Co-host

Aurora is a public blueprint for building an AI streaming co-host: a real-time voice companion that can appear on stream as a Live2D character, react to the game/screen, connect with Twitch/Discord chat, and become part of the show rather than a normal chatbot.

This repository is the sanitized public version of the project. It explains what is possible and how the system is designed without exposing private production code, API keys, local IPs, stream credentials, or personal viewer data.

## What Aurora can do

- Speak naturally in real time using a live voice model.
- Listen to the streamer through a microphone.
- React to the game or desktop through vision/screen frames.
- Drive a Live2D avatar with lip-sync in OBS.
- Connect to external stream intelligence: Twitch chat, Discord, Hermes automation, viewer memory, and interaction queues.
- Act as a co-host with personality, timing, and stream-safe constraints.

## Architecture overview

```text
Gaming PC
  mic + screen + OBS + Live2D browser source
        |
        v
Real-time AI voice loop
  voice model + audio routing + lip-sync websocket
        |
        v
Stream automation server
  Twitch/Discord bridge + Hermes agent + memory/queue tools
        |
        v
Twitch stream
  streamer + AI co-host + chat interaction
```

Read more in `docs/architecture.md`.

## Why this exists

Most AI streaming demos are either simple text bots or disconnected avatars. Aurora explores a more ambitious idea: an AI co-host that is present, visible, audible, reactive, and integrated into the stream workflow.

The goal is not to replace the streamer. The goal is to add a second character to the show.

## Build-your-own path

Start here:

1. `docs/how-it-works.md`
2. `docs/build-your-own.md`
3. `docs/safety-and-secrets.md`
4. `examples/minimal-twitch-listener/README.md`
5. `examples/minimal-live2d-trigger/README.md`
6. `examples/minimal-chat-filter/README.md`

## Project status

Aurora is an active private production project. This public repo will be updated with sanitized progress, diagrams, examples, and lessons learned.

### 2026-06-15 sanitized progress note

- Prototyped additional browser-based avatar viewers and local asset packaging workflows for future stream presentation experiments.
- Continued iterating on the private runtime while keeping production launchers, secrets, logs, and personal viewer data out of the public repo.

## License

Documentation and example code are released under the MIT License unless noted otherwise. Live2D models, third-party SDKs, voice models, and platform APIs have their own licenses and terms.
