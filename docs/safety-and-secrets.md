# Safety and Secrets

Do not publish your production streaming setup blindly. AI co-host projects often contain more sensitive data than expected.

## Never commit

- API keys
- OAuth tokens
- `.env` files
- Discord bot tokens
- Twitch tokens
- exact private server IPs if not necessary
- personal viewer data
- private prompts that reveal moderation strategy or credentials
- logs from real streams
- local launch scripts containing secrets

## Use templates

Commit files like:

- `.env.example`
- `start.example.bat`
- `config.example.yaml`

Keep real files ignored by git:

- `.env`
- `start.bat`
- `config.local.yaml`

## Chat and viewer memory safety

Viewer memory should be opt-in, minimal, and stream-relevant.

Good examples:

- “viewer likes strategy games”
- “viewer asked to be called by this nickname”
- “running joke from the community”

Bad examples:

- real names unless intentionally public
- addresses
- financial/health/private details
- anything from private DMs

## Co-host behavior safety

The AI should be designed to stay stream-safe:

- no doxxing
- no reading private data
- no pretending to be the streamer
- no unfiltered chat-to-speech
- no responding to every message
- clear moderation boundaries

## Public repo rule

The public repository should explain the system and provide safe examples. The private repository should contain the real production code and machine-specific setup.
