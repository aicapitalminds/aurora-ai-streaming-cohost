# Build Your Own AI Streaming Co-host

This is a practical roadmap, not a copy-paste production setup.

## Phase 1: Basic voice loop

Goal: AI can listen and speak through your stream audio setup.

You need:

- a real-time voice model or voice API
- microphone capture
- speaker/output routing
- a clear way to set API keys through environment variables

Success test:

- you speak
- the AI responds out loud
- OBS can capture the AI audio

## Phase 2: Avatar in OBS

Goal: the AI has a visible character on stream.

You need:

- OBS browser source
- transparent HTML page
- Live2D or another avatar renderer
- local websocket or event bridge for expressions/lip-sync

Success test:

- avatar appears in OBS
- avatar mouth moves when AI speaks

## Phase 3: Stream context

Goal: the AI reacts to the stream, not just the microphone.

Options:

- periodic screenshots
- game state APIs
- OCR
- OBS scene/source state
- streamer hotkeys

Success test:

- the AI can comment on visible stream events without constant prompting

## Phase 4: Chat bridge

Goal: the AI sees selected Twitch/Discord chat messages.

You need:

- Twitch chat listener
- Discord listener if needed
- spam/relevance filter
- safety rules
- queue so the AI responds at good moments

Success test:

- only useful messages reach the AI
- the AI does not answer every message

## Phase 5: Viewer memory

Goal: Aurora remembers useful viewer context without becoming creepy.

Store only:

- stable preferences users volunteered
- running jokes
- safe stream-relevant facts
- moderation-safe interaction history

Do not store:

- private information
- sensitive personal data
- secrets
- anything a viewer would not expect to be remembered

## Phase 6: Show design

The technical system is only half the project. Decide:

- what role the co-host plays
- when she should speak
- what makes her funny/useful
- what boundaries protect the streamer and chat
- how viewers can intentionally interact with her
