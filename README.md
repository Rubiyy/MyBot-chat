# MyBot - A Maubot Plugin for Matrix

MyBot is an intelligent chat assistant plugin for the Matrix network, built on the Maubot framework. It leverages the Hugging Face Phi-3 model by Microsoft to provide natural language interactions and assistance across Matrix rooms.

## Features

- Natural language conversations using the Phi-3 model
- Configurable system prompts and personalities
- Multiple backend support (Hugging Face, OpenAI, Anthropic)
- Context-aware responses with conversation memory
- Customizable response parameters
- Resource-optimized for better performance

## Prerequisites

- Python 3.8 or higher
- Maubot instance
- CUDA-compatible GPU (recommended) or CPU with sufficient memory
- Required Python packages (see requirements.txt)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/rubiyy/mybot-chat.git
cd mybot-chat
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Build the plugin:
```bash
mbc build
```

4. Upload the generated mybot.llm.chat.mbp file to your Maubot instance

## Configuration (Optional)

Modify the `base-config.yaml` file in your Maubot instance:

```yaml
allowlist: []  # Set to false for public access
default_backend: "phi3"
backends:
  phi3:
    type: huggingface
    model_name: "microsoft/Phi-3-mini-128k-instruct"
    max_new_tokens: 150
    max_context_length: 1000
    temperature: 0.7
    top_k: 50
    top_p: 0.95
    repetition_penalty: 1.3
    default_model: "microsoft/Phi-3-mini-128k-instruct"
    default_system_prompt: "You are a helpful personal assistant called MyBot."
```

## Usage

### Basic Commands

- `!llm info` - Display current configuration
- `!llm backend <name>` - Switch to a different backend
- `!llm model <model>` - Change the model
- `!llm system <prompt>` - Set a new system prompt
- `!llm clear` - Clear conversation history

### Conversation

Simply talk to the bot in any room where it's invited. It will respond naturally to messages that don't start with "!".

## Memory Management

The bot maintains a conversation history limited to 5 messages to optimize performance and ensure relevant responses. All conversations are stored in the Maubot database.

## Performance Optimization

### GPU Usage
- The bot automatically detects CUDA availability
- Uses 80% of available GPU memory by default
- Falls back to CPU if insufficient GPU memory

### CPU Mode
- Implements efficient memory management
- Uses model quantization for better performance
- Caches responses for frequently asked questions

## Error Handling

The bot includes comprehensive error handling for:
- Memory allocation issues
- Model loading failures
- Network connectivity problems
- Invalid user inputs

## Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/AmazingFeature`
3. Commit your changes: `git commit -m 'Add AmazingFeature'`
4. Push to the branch: `git push origin feature/AmazingFeature`
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [Maubot](https://github.com/maubot/maubot) for the bot framework
- [Hugging Face](https://huggingface.co) for the Phi-3 model
- [Matrix](https://matrix.org) for the communication protocol
