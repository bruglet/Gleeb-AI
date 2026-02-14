# Gleeb.AI

A Discord bot leveraging Google Gemini for advanced conversation, content understanding, image/video/audio recognition, and more. Powered by spoilage.

Forked from [Gemini-Discord-Bot](https://github.com/hihumanzone/Gemini-Discord-Bot) by [hihumanzone](https://github.com/hihumanzone).

Now with containerization!

---

## Features

- **Conversational AI** powered by Google Gemini (Gemini 2.5 Flash Lite)
- **Image recognition** (supports images and code/text files)
- **Custom personalities per user, channel, or server**
- **Server and channel-wide chat history** options
- **Admin controls** for blacklisting/whitelisting users
- **Downloadable conversation/message history**
- **Multiple AI tools:** Google Search, code execution, and function calling
- **Status monitoring** (RAM, CPU, and reset timer)
- **Slash command and button-based UI**
- **Containerization:** Deploy to Docker and Podman containers seamlessly with automatic builds for new versions.

---

## Getting Started

### Prerequisites

- Podman and Quadlet via Systemd (recommended)
- Alternatively, Docker and Docker Compose
- Discord bot token ([create here](https://discord.com/developers/applications))
- Google Gemini API key ([get one here](https://aistudio.google.com/app/apikey))

### Setup

1. **Set up your container runtime:**
    - Download and move `gleebai.container` to ~/.config/containers/systemd/ (Podman & Quadlet)
    - Download `docker-compose.yml` (Docker Compose)
    - You could also manually run Docker and Podman commands. (not recommended)

2. **Configure environment variables:**
    - Fill in your Discord and Google API tokens in `gleebai.container` or `docker-compose.yml`.

3. **Start the bot:**
- Podman and Quadlet:
  ```
  systemctl --user daemon-reload
  systemctl --user start gleebai
  ```
- In same directory as `docker-compose.yml`, run `podman compose up -d` (Docker Compose)

*Note: You can also run this with not as a container via Node or by deploying to Vercel.*

---

## Usage

- **Invite the bot to your Discord server.**
- Use `/settings` to configure personal or channel preferences.
- Use `/server_settings` for server-wide admin controls.
- Upload supported files or image files and ask the bot about them.
- Use slash commands:
    - `/respond_to_all enabled:true|false` – Bot responds to every message in a channel
    - `/clear_memory` – Clear your personal conversation history
    - `/toggle_channel_chat_history enabled:true|false [instructions]` – Channel-wide conversation
    - `/blacklist user:@user` – Prevent a user from using the bot
    - `/whitelist user:@user` – Remove a user from the blacklist
    - `/status` – Show system status

---

## Customization

- Fork and modify `config.js` to change default personalities, activities, colors, and feature toggles. Make sure to pull new container once built by GitHub Actions.
- Persistent data (chat history, settings, blacklists, etc.) is stored in the `gleebai-config` volume.

---

## Admin & Security

- Only server admins can use admin commands (blacklist, whitelist, server settings).
- Blacklisted users cannot interact with the bot.

---

## Notes

- The bot stores chat history and settings locally. For production use, consider using persistent cloud storage.
- **Do not commit your `.env` or Quadlet file with secrets.**

---

## License

[MIT](LICENSE.md)
