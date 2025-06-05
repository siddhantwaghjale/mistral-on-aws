# AI Assistant with Amazon Bedrock & MCP Tools

This project provides a chat interface to interact with AI models from Amazon Bedrock while giving them access to external tools like Google Maps, time utilities, and memory management via the Model Context Protocol (MCP). The application supports both text and image inputs, allowing multimodal interactions with the AI models.

## Features

- Chat with large language models through Amazon Bedrock
- Support for both text and image inputs (multimodal capabilities)
- Integration with various MCP tool servers (Google Maps, Time, Memory)
- Terminal-based chat interface (chat.py)
- Web-based interface using Gradio (gradio_app.py)
- Automatic image processing and optimization for model compatibility

## Requirements

- Python 3.9+
- AWS account with Bedrock access
- Node.js (for MCP tool servers)
- Required Python packages (see requirements.txt)

## Installation

1. Clone this repository:
   ```
   git clone <repository-url>
   cd mistral-on-aws/MCP/MCP_Mistral_app_demo/
   ```

2. Install required Python packages:
   ```
   pip install -r requirements.txt
   ```

3. Configure AWS credentials:
   ```
   aws configure
   ```

## Running the Application

### Terminal-based Interface

Run the terminal-based interface with:

```bash
python src/chat.py
```

### Gradio Web Interface

Run the web-based interface with:

```bash
python gradio_app.py
```

This will start a local web server and provide you with a URL (typically http://127.0.0.1:7860) to access the application in your browser. The application must be run from the project's root directory so that it can correctly import modules from the src directory.

## Usage

1. Start the application using one of the methods above
2. Type your queries and questions in the input field
3. Include image URLs or upload an image in Gradio app in your message to enable visual understanding
4. The AI assistant will respond and use available tools as needed
5. Type 'quit', 'exit', or 'q' to exit the application

### Image Support

The application can process images from URLs or direct uploads. Simply include an image URL in your message or upload an image file, and the system will:

- Automatically detect and extract the image URL or process your uploaded image file
- Process and optimize the image for the AI model
- Include the image in the query to the model
- Support multiple image formats (JPEG, PNG, GIF, WebP)

To use this feature, you can either:
- Add an image URL directly in your message
- Select and upload an image from your device
- The system will process your image regardless of the source and incorporate it into the conversation context.

## Available Tools

The application integrates with the following MCP tool servers:

- **Google Maps**: For location-based queries: https://github.com/modelcontextprotocol/servers/tree/main/src/google-maps
- **Time**: For time-related operations:https://github.com/yokingma/time-mcp
- **Memory**: For storing and retrieving information during the conversation: https://github.com/modelcontextprotocol/servers/tree/main/src/memory

## Configuration

- Tool servers are configured in the `server_configs.py` file
- AWS Bedrock settings are in the `config.py` file
- The web interface allows changing AWS region and model ID at runtime

## Implementation Details

- Uses Amazon Bedrock's Converse API for structured conversations
- Supports multimodal inputs with raw binary image data
- Implements error handling for image processing and API calls
- Automatically resizes large images for API compatibility

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- Amazon Bedrock for providing access to large language models
- Model Context Protocol (MCP) for the tool integration framework
- Gradio for the web interface components
- This project is inspired by [ample-for-bedrock-integration-with-database-mcp-server](https://github.com/aws-samples/sample-for-bedrock-integration-with-database-mcp-server)