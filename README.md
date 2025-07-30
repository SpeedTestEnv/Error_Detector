# Error Detector v1.1

A sophisticated error detection and automation system for monitoring software applications and automatically handling error dialogs using both template matching and OCR-based keyword detection.

##  Features

### Core Functionality
- **Dual Detection Methods**: Combines template matching and OCR-based keyword detection
- **Real-time Monitoring**: Continuously monitors screen for error patterns
- **Automated Recovery**: Automatically clicks recovery buttons when errors are detected
- **Error Frequency Tracking**: Tracks error occurrences with configurable limits
- **Screenshot Capture**: Saves screenshots of detected errors for analysis
- **Multi-language Support**: OCR supports German and English text detection

### Advanced Features
- **DPI Scaling Support**: Automatically adjusts for different screen resolutions
- **Configurable Keywords**: User-defined error and automation keywords
- **Minimalist GUI**: Clean, non-intrusive interface for monitoring
- **Loop prevention**: Re-occuring errors within a time frame will cause the detection to stop 
- **CLI Mode**: Command-line interface for automation scenarios
- **Logging System**: Comprehensive logging for debugging and monitoring
- **Error Pattern Management**: Customizable error pattern templates

##  Requirements

### System Requirements
- Windows 10/11 (64-bit)
- 4GB RAM minimum
- 100MB free disk space
- .NET Framework 4.7.2 or later

### Dependencies
The application includes all necessary dependencies bundled within the executable:
- **OpenCV**: Computer vision and image processing
- **Tesseract OCR**: Text recognition engine (bundled)
- **PyAutoGUI**: Screen capture and automation
- **Pillow**: Image processing
- **NumPy**: Numerical computing
- **mss**: Fast screen capture

##  Installation

### Option 1: Download Pre-built Executable
1. Download the latest release from the [Releases](https://github.com/SpeedTestEnv/Error_Detector/releases) page
2. Extract the ZIP file to your desired location
3. Run `main.exe` directly

### Option 2: Build from Source
```bash
# Clone the repository
git clone https://github.com/your-repo/error-detector.git
cd error-detector

# Install Python dependencies
pip install -r requirements.txt

# Build executable
pyinstaller main.spec
```

##  Quick Start

### First Run
1. **Launch the Application**: Run `main.exe`
2. **Initial Setup**: The application will create default configuration files
3. **Configure Keywords**: Set your error and automation keywords in the GUI
4. **Start Detection**: Click "Start Detection" to begin monitoring

### Basic Usage
```bash
# Run with GUI (default)
main.exe

# Run in CLI mode
main.exe --cli

# Test detection
main.exe --test-all

# Show system status
main.exe --status
```

##  Configuration

### Settings File Location
Configuration files are stored in:
- **Executable Mode**: `./config/` (relative to executable)
- **Script Mode**: `./config/` (relative to script)

### Key Configuration Files
- `settings.json`: Main application settings
- `error_patterns.json`: Template-based error patterns
- `keyword_settings.json`: OCR keyword definitions

### Default Settings
```json
{
  "detection": {
    "poll_interval": 1.0,
    "max_errors_per_window": 5,
    "time_window_minutes": 10,
    "enable_gui": true,
    "screenshot_on_detection": true
  },
  "keywords": {
    "error_keywords": ["Error", "Timeout: Kein Ergebnis von Tester!"],
    "automation_keywords": ["Wiederholen", "Next UUT"],
    "case_sensitive": false
  }
}
```

##  Advanced Configuration

### Custom Error Keywords
Add your own error keywords through the GUI or edit `keyword_settings.json`:
```json
{
  "error_keywords": ["Your Error Text", "Another Error Message"],
  "automation_keywords": ["Retry", "Continue", "OK"]
}
```

### Template Pattern Configuration
Create custom template patterns in `error_patterns.json`:
```json
{
  "patterns": [
    {
      "name": "custom_error",
      "template_path": "templates/custom_error.png",
      "click_offset": [0, 30],
      "confidence_threshold": 0.8,
      "description": "Custom error dialog"
    }
  ]
}
```

##  Monitoring and Logs

### Log Files
- `error_detector.log`: Main application log
- `error_counters.json`: Error frequency tracking data

### Screenshots
Detected errors are saved to:
- `config/screenshots/` directory
- Timestamped filenames for easy identification

### Statistics
The application tracks:
- Error detection frequency
- Recovery attempt success rates
- Detection confidence scores
- System performance metrics

##  Troubleshooting

#### Logs for tracking and solving issues
1. **Logs**: Check `error_detector.log` for error details

#### Detection Not Working
1. **Screen Resolution**: Verify DPI scaling settings
2. **Keywords**: Check keyword spelling and case sensitivity
3. **Templates**: Ensure template images match current screen layout
4. **Confidence**: Adjust confidence thresholds in settings

#### OCR Issues
1. **Tesseract**: Verify `tesseract.exe` is in the `tesseract/` folder
2. **Language Files**: Check `tessdata/` directory for language files
3. **Text Quality**: Ensure screen text is clear and readable

### Debug Mode
Run with debug logging:
```bash
main.exe --log-level DEBUG
```

##  Security and Privacy

### Registry Impact
**The application does NOT make any registry changes when executed on a new PC.** It operates entirely in user space and stores all data in local configuration files.

### Data Storage
- **Local Only**: All data stored locally, no network transmission
- **No Registry**: No Windows registry modifications
- **Configurable**: All settings in JSON files
- **Portable**: Can run from any directory without installation

### Privacy Features
- No telemetry or data collection
- No network communication
- All screenshots stored locally
- Configurable logging levels

##  Architecture

### Core Components
```
Error Detector v1.1
├── main.py                 # Application entry point
├── detector.py            # Error detection engine
├── keyword_manager.py     # OCR and keyword management
├── automation.py          # Mouse automation
├── counter.py             # Error frequency tracking
├── gui.py                 # Minimalist GUI
└── config.py              # Configuration management
```

### Detection Flow
1. **Screen Capture**: Continuous screen monitoring
2. **Template Matching**: Image-based pattern detection
3. **OCR Processing**: Text recognition using Tesseract
4. **Keyword Matching**: Text-based error detection
5. **Automation**: Automatic click recovery
6. **Logging**: Comprehensive event logging

##  Performance

### Optimization Features
- **Efficient Screen Capture**: Uses `mss` for fast screen capture
- **Smart Polling**: Configurable detection intervals
- **Memory Management**: Automatic cleanup of old screenshots
- **Threading**: Non-blocking detection loop

### Resource Usage
- **CPU**: Low usage during idle, spikes during detection
- **Memory**: ~50-100MB typical usage
- **Disk**: Screenshots and logs (configurable cleanup)
- **Network**: No network usage


### Code Style
- Follow PEP 8 guidelines
- Use type hints
- Add docstrings for all functions
- Include unit tests for new features

##  License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

##  Credits

- **OpenCV**: Computer vision library
- **Tesseract**: OCR engine
- **PyAutoGUI**: Automation library
- **PyInstaller**: Executable bundling

---

**Version**: 1.1  
**Author**: Wen-Qiang Liao  
**Last Updated**: 2025-01-23 
