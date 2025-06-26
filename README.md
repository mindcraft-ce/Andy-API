# Andy API Local Client

This directory contains all the components needed to run the local-side of the Andy API, allowing you to join the compute pool and contribute your hardware resources.

## 🚀 Quick Start

### Option 1: Web Interface (Recommended)
```bash
./start.sh web
```
Access the web interface at: http://localhost:5000

### Option 2: Enhanced CLI Client
```bash
./start.sh enhanced
```
Advanced command-line client with VRAM monitoring and enhanced system tracking.

### Option 3: Simple CLI Client
```bash
./start.sh cli
```
Basic command-line client for simple pool joining.

## 📁 Files Overview

### Core Applications
- **`app.py`** - Flask web application providing a user-friendly interface
- **`enhanced_andy_client.py`** - Advanced CLI client with comprehensive system monitoring
- **`andy_host_client.py`** - Basic CLI client for simple pool joining
- **`launch.py`** - Unified launcher script for all client modes

### Configuration & Setup
- **`requirements.txt`** - Python dependencies
- **`start.sh`** - Main startup script with mode selection
- **`templates/`** - Web interface templates

### Templates (Web Interface)
- **`local_dashboard.html`** - Main dashboard view
- **`local_metrics.html`** - Performance metrics and monitoring
- **`local_models.html`** - Model management interface
- **`local_settings.html`** - Configuration settings

## 🛠️ Installation

### Prerequisites
- Python 3.8+
- Ollama (for model hosting)
- NVIDIA GPU (optional, for VRAM monitoring)

### Setup
1. **Install Dependencies**:
   ```bash
   pip3 install -r requirements.txt
   ```

2. **Install Ollama** (if not already installed):
   - Visit: https://ollama.ai
   - Download and install for your platform
   - Pull some models: `ollama pull llama2`

3. **Start the Client**:
   ```bash
   ./start.sh web  # For web interface
   # or
   ./start.sh enhanced  # For enhanced CLI
   ```

## 🎮 Usage Modes

### Web Interface Mode
- **Port**: 5000 (default)
- **Features**: 
  - Visual dashboard
  - Model management
  - Performance monitoring
  - Easy configuration
- **Best For**: Most users, beginners, visual interface preference

### Enhanced CLI Mode
- **Features**:
  - VRAM tracking
  - Advanced system monitoring
  - Real-time performance metrics
  - Automatic model discovery
- **Best For**: Advanced users, servers, automated deployments

### Simple CLI Mode
- **Features**:
  - Basic pool joining
  - Simple configuration
  - Lightweight operation
- **Best For**: Minimal setups, testing, basic usage

## ⚙️ Configuration

### Environment Variables
```bash
export ANDY_API_URL="https://mindcraft.riqvip.dev"      # Andy API server
export OLLAMA_URL="http://localhost:11434"       # Local Ollama instance
export FLASK_PORT="5000"                         # Web interface port
```

### Command Line Options
```bash
# Web mode
python3 launch.py --mode web --port 5000

# Enhanced CLI mode  
python3 launch.py --mode enhanced --server https://mindcraft.riqvip.dev --ollama http://localhost:11434

# Simple CLI mode
python3 launch.py --mode cli --server https://mindcraft.riqvip.dev --ollama http://localhost:11434
```

## 📊 Features

### System Monitoring
- **CPU Usage**: Real-time CPU utilization tracking
- **RAM Usage**: Memory consumption monitoring
- **VRAM Tracking**: GPU memory usage (NVIDIA GPUs)
- **Model Performance**: Request/response metrics

### Model Management
- **Auto-Discovery**: Automatically detect Ollama models
- **Model Classification**: Categorize by type (text, vision, etc.)
- **Performance Testing**: Built-in model testing
- **Resource Tracking**: Per-model resource usage

### Pool Integration
- **Automatic Registration**: Join Andy API compute pool
- **Health Monitoring**: Regular health pings
- **Load Balancing**: Intelligent request distribution
- **Fallback Handling**: Graceful error recovery

## 🔧 Troubleshooting

### Common Issues

1. **Ollama Not Found**:
   ```bash
   # Check if Ollama is running
   curl http://localhost:11434/api/tags
   
   # Start Ollama if needed
   ollama serve
   ```

2. **Port Already in Use**:
   ```bash
   # Use different port
   python3 launch.py --mode web --port 5001
   ```

3. **VRAM Monitoring Issues**:
   ```bash
   # Install GPU monitoring libraries
   pip3 install pynvml GPUtil
   ```

4. **Connection Issues**:
   - Check firewall settings
   - Verify Andy API server is running
   - Ensure network connectivity

### Logs & Debugging
- Web interface logs: Check console output
- CLI client logs: Displayed in terminal
- Error details: Check Python traceback

## 🔗 Integration

### With Andy API Server
The local client connects to the main Andy API server (default: https://mindcraft.riqvip.dev) to:
- Register as a compute host
- Receive inference requests
- Report performance metrics
- Participate in load balancing

### With Ollama
The client interfaces with your local Ollama instance to:
- Discover available models
- Serve inference requests
- Monitor model performance
- Manage model resources

## 📈 Performance Optimization

### Hardware Recommendations
- **CPU**: Multi-core processor for concurrent requests
- **RAM**: 16GB+ for larger models
- **GPU**: NVIDIA GPU with 8GB+ VRAM (optional but recommended)
- **Storage**: SSD for model loading performance
- **Network**: Stable internet connection with good bandwidth

### Configuration Tips
- Adjust `max_clients` based on your hardware
- Monitor VRAM usage to avoid OOM errors
- Use appropriate model quantization
- Configure reasonable context lengths

## 🤝 Contributing

This local client is part of the larger Mindcraft-CE Andy API ecosystem. To contribute:

1. Fork the main repository
2. Make your changes in the `local_client/` directory
3. Test thoroughly with different modes
4. Submit a pull request

## 📄 License

Part of the Mindcraft-CE project - see main repository for license details.
