# Architecture

Aurora is built as a split system: the gaming PC handles real-time audio/visual work, while a server handles chat intelligence and automation.

## Components

### 1. Gaming PC

Responsibilities:

- Capture streamer microphone audio.
- Send audio to a real-time AI voice model.
- Optionally send screen/game frames for visual context.
- Play the AI voice back into the stream audio mix.
- Generate lip-sync values from the AI audio.
- Render the Live2D avatar as an OBS browser source.

Why Windows native matters:

- Stream audio routing often depends on VoiceMeeter, OBS, physical microphones, and virtual cables.
- WSL/Linux may not see the same audio devices reliably.

### 2. Live2D browser source

A transparent browser scene in OBS loads the avatar and listens to a local websocket. The Python/voice process sends mouth-open values, and the browser applies them to the Live2D model.

### 3. Stream automation server

Responsibilities:

- Listen to Twitch/Discord events.
- Filter chat messages for relevance and safety.
- Store useful viewer memory.
- Maintain an interaction queue so the co-host does not interrupt constantly.
- Send selected context to the AI co-host.

### 4. AI personality layer

Aurora needs more than a model call. The personality layer defines:

- who Aurora is
- what she should/should not say
- how long replies should be during live content
- how to react to chat
- when to stay quiet
- how to avoid derailing the stream

## Data flow

```text
Streamer mic -> real-time voice model -> AI audio -> VoiceMeeter/OBS
                                  |
                                  v
                              lip-sync websocket -> Live2D avatar

Twitch/Discord chat -> filter -> memory/queue -> selected context -> AI co-host

Screen/game frames -> vision model -> stream-aware reactions
```

## Design principle

The AI co-host should support the stream's pacing. Silence is a feature. The system should decide when Aurora has something useful, funny, or emotionally fitting to add.
