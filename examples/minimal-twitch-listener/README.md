# Minimal Twitch Listener

This example placeholder describes the smallest useful Twitch chat listener for an AI co-host.

## Goal

Read Twitch chat messages and pass only selected messages to the co-host pipeline.

## Pseudocode

```python
async for message in twitch_chat:
    if not is_safe(message):
        continue
    if not is_relevant(message):
        continue
    interaction_queue.add({
        "source": "twitch",
        "user": message.user,
        "text": message.text,
        "timestamp": message.timestamp,
    })
```

## Design notes

- Do not text-to-speech every chat message.
- Add rate limits.
- Add moderation rules.
- Let the streamer override or clear the queue.
