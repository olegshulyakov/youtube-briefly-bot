# YouTube Briefly Bot

A Telegram bot written in Go that retells YouTube videos. It uses `yt-dlp` to fetch video transcripts and a Hugging Face model (or OpenRouter API) to summarize them. The bot is designed to be lightweight, easy to deploy, and extensible.

---

## Features

- **YouTube Transcript Extraction**: Uses `yt-dlp` to fetch video transcripts.
- **Text Summarization**: Integrates with Hugging Face models or OpenRouter API for summarization.
- **Telegram Bot**: Built using the `go-telegram-bot-api` library.
- **Dockerized**: Easy to deploy using Docker.
- **Linting**: Uses `golangci-lint` for code quality checks.

---

## Prerequisites

- Go 1.21 or higher
- Docker (optional, for containerized deployment)
- yt-dlp
- A Telegram bot token (get it from [BotFather](https://core.telegram.org/bots#botfather))
- LLM API key (OpenAI, OpenRouter,..)

---

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/olegshulyakov/go-briefly-bot.git
cd go-briefly-bot
```

### 2. Set Up Environment Variables

Create a `.env` file in the root directory:

#### Telegram

```env
TELEGRAM_BOT_TOKEN=<your_telegram_bot_token>
```

#### yt-dlp options (optional)

```env
# yt-dlp options
YT_DLP_ADDITIONAL_OPTIONS=--proxy socks5://user:pass@127.0.0.1:1080/ --cookies ./cookies.txt
```

#### OpenAI

```env
# OpenAI API
OPENAI_BASE_URL=https://api.openai.com/v1/
OPENAI_API_KEY=your_open_ai_provider_api_token
OPENAI_MODEL=GPT-4o-mini
```

#### LM Studio

```env
# OpenAI API
OPENAI_BASE_URL=http://127.0.0.1:1234/v1/
OPENAI_API_KEY=not-needed
OPENAI_MODEL=qwen2.5-3b-instruct
```

#### Ollama

```env
# OpenAI API
OPENAI_BASE_URL=http://localhost:11434/v1/
OPENAI_API_KEY=not-needed
OPENAI_MODEL=llama3.1:8b
```

### 3. Install Dependencies

Install Go dependencies:

```bash
go mod download
```

Install `yt-dlp`

### 4. Build and Run Locally

**REST API:**

```bash
go run cli/apis/rest/main.go
```

**Telegram Bot:**

```bash
go run cli/telegram/main.go
```

---

## Docker Deployment

### 1. Build the Docker Image

```bash
./.devops/Telegram-build.sh
```

### 2. Run the Docker Container

```bash
./.devops/Telegram-run.sh
```

---

## Usage

1. Start the bot by sending the `/start` command.
2. Send a YouTube video link to the bot.
3. The bot will fetch the transcript, summarize it, and send the summary back to you.

---

## Linting

This project uses `golangci-lint` for code quality checks. To run the linter:

```bash
golangci-lint run
```

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) for YouTube transcript extraction.
- [Hugging Face](https://huggingface.co/) for summarization models.
- [OpenRouter](https://openrouter.ai/) for API-based summarization.
- [go-telegram-bot-api](https://github.com/go-telegram-bot-api/telegram-bot-api) for Telegram bot integration.

---

## Support

If you encounter any issues or have questions, please [open an issue](https://github.com/olegshulyakov/github.com/olegshulyakov/go-briefly-bot/issues).
