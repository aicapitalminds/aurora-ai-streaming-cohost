# Minimal Chat Filter

A co-host should be selective. The chat filter decides which messages are worth passing to the AI.

## Scoring dimensions

- Is the message addressed to the AI or streamer?
- Is it safe to read/respond to on stream?
- Is it spam or repeated content?
- Is it relevant to the current game/topic?
- Is the streamer currently in a moment where interruption is bad?
- Has Aurora spoken recently?

## Pseudocode

```python
def should_queue(message, stream_state):
    if message.is_mod_action:
        return False
    if contains_private_or_unsafe_content(message.text):
        return False
    if stream_state.in_cutscene_or_high_focus_moment:
        return False
    if message.mentions_aurora:
        return True
    if message.has_high_relevance_score:
        return True
    return False
```

## Principle

Silence is part of the product. A good co-host speaks when it improves the show.
