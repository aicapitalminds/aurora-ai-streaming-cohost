# How It Works

Aurora combines several pieces into one streaming character.

## Real-time voice

A live voice model receives microphone audio and returns generated speech audio. This makes the AI feel present because it can respond without a slow text-to-speech pipeline.

Key requirements:

- low-latency microphone streaming
- output audio routing into OBS
- interruption handling so the mic pauses while the AI speaks
- clear failure states when the API or audio devices are unavailable

## Vision / screen awareness

The system can periodically capture screen frames and send them as visual context. This lets the co-host react to what is happening in the game or browser.

The important design choice is rate limiting. Vision frames should be useful, not constant noise.

## Live2D avatar

The avatar is rendered in a browser source. The voice process calculates mouth movement from the generated audio and sends values over a websocket.

This avoids needing the Live2D renderer and voice model in the same runtime.

## Chat intelligence

Raw chat should not go directly to the voice model. A good co-host needs a filter and queue:

1. read incoming chat
2. score relevance
3. block unsafe/private/spam content
4. remember important viewer facts only when appropriate
5. choose the best moment to respond
6. send concise context to the voice model

## Stream-safe behavior

A streaming co-host needs rules that normal assistants do not:

- do not talk over key gameplay moments
- do not read every chat message out loud
- avoid personal/private information
- keep replies short
- match stream energy
- stay in character
- fail visibly rather than silently
