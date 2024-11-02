# Python Code Explainer 🚀

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--3.5-lightgrey)](https://openai.com/)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Stars](https://img.shields.io/github/stars/bsujalnaik/PythonCodeExplainer?style=social)](https://github.com/bsujalnaik/PythonCodeExplainer/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/bsujalnaik/PythonCodeExplainer)](https://github.com/bsujalnaik/PythonCodeExplainer/issues)
[![GitHub forks](https://img.shields.io/github/forks/bsujalnaik/PythonCodeExplainer)](https://github.com/bsujalnaik/PythonCodeExplainer/network)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/bsujalnaik/PythonCodeExplainer)](https://github.com/bsujalnaik/PythonCodeExplainer/pulls)
[![GitHub last commit](https://img.shields.io/github/last-commit/bsujalnaik/PythonCodeExplainer)](https://github.com/bsujalnaik/PythonCodeExplainer/commits/main)

## 📖 Table of Contents
- [Overview](#overview)
- [Features](#-features)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Usage](#-usage)
- [Configuration](#️-configuration)
- [Contributing](#-contributing)
- [Documentation](#-documentation)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)
- [Contact](#-contact)

## Overview

Python Code Explainer is an innovative tool that leverages OpenAI's GPT to provide detailed, human-readable explanations of Python code snippets. It's designed to help developers, students, and code reviewers quickly understand complex Python code through intelligent analysis and clear explanations.

## 🌟 Features

- 🔍 **Detailed Code Analysis**
  - Line-by-line code explanation
  - Syntax highlighting and interpretation
  - Context-aware explanations
  - Time and space complexity analysis

- 🎯 **Smart Parsing**
  - Automatic code structure detection
  - Intelligent context understanding
  - Support for multiple coding styles
  - Recognition of common patterns and algorithms

- 🚀 **Performance**
  - Fast processing and response times
  - Efficient API usage
  - Caching for repeated queries
  - Batch processing capabilities

- 💡 **Educational Tools**
  - Learning-focused explanations
  - Best practices highlighting
  - Code improvement suggestions
  - Alternative implementation examples

- 🔒 **Security**
  - Secure API key handling
  - Rate limiting protection
  - Input validation
  - Safe error handling

## 📋 Prerequisites

Before installation, ensure you have:

- Python 3.8 or higher
- pip package manager
- OpenAI API key
- 64-bit operating system
- Minimum 4GB RAM

Required Python packages:
```plaintext
openai>=1.0.0
python-dotenv>=0.19.0
rich>=10.0.0
requests>=2.26.0
typing-extensions>=4.0.0
```

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/bsujalnaik/PythonCodeExplainer.git
   cd PythonCodeExplainer
   ```

2. **Create and activate virtual environment (recommended)**
   ```bash
   # Windows
   python -m venv venv
   .\venv\Scripts\activate

   # Linux/MacOS
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` file:
   ```plaintext
   OPENAI_API_KEY=your_api_key_here
   MODEL_NAME=gpt-3.5-turbo
   MAX_TOKENS=500
   TEMPERATURE=0.7
   ```

## 💻 Usage

### Basic Usage

```python
from python_code_explainer import CodeExplainer

# Initialize the explainer
explainer = CodeExplainer(api_key="your_openai_api_key")

# Simple code explanation
code = """
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
"""

explanation = explainer.explain_code(code)
print(explanation)
```

### Advanced Usage

```python
# Detailed analysis with specific focus
explanation = explainer.explain_code(
    code,
    focus="time_complexity",
    detail_level="advanced",
    include_examples=True,
    suggest_improvements=True
)

# Generate documentation
docs = explainer.generate_documentation(
    code,
    style="google",
    include_examples=True
)

# Get optimization suggestions
suggestions = explainer.suggest_improvements(
    code,
    focus=["performance", "readability"]
)

# Batch processing
file_paths = ["script1.py", "script2.py"]
batch_explanations = explainer.batch_explain(file_paths)
```

### Command Line Usage

```bash
# Explain a Python file
python -m python_code_explainer explain script.py

# Generate documentation
python -m python_code_explainer document script.py --style google

# Get improvement suggestions
python -m python_code_explainer improve script.py
```

## 🛠️ Configuration

### Configuration Options

| Parameter | Description | Default | Type | Required |
|-----------|-------------|---------|------|----------|
| `api_key` | OpenAI API key | None | str | Yes |
| `model` | GPT model to use | "gpt-3.5-turbo" | str | No |
| `temperature` | Response creativity (0-1) | 0.7 | float | No |
| `max_tokens` | Maximum response length | 500 | int | No |
| `detail_level` | Explanation detail level | "intermediate" | str | No |
| `language` | Output language | "en" | str | No |
| `cache_enabled` | Enable response caching | True | bool | No |
| `timeout` | API timeout in seconds | 30 | int | No |

### Configuration File

Create `config.yaml` in the project root:

```yaml
api:
  key: your_api_key_here
  model: gpt-3.5-turbo
  temperature: 0.7
  max_tokens: 500

output:
  detail_level: intermediate
  language: en
  format: markdown

system:
  cache_enabled: true
  timeout: 30
  log_level: INFO
```

## 📚 Documentation

### Class Reference

```python
class CodeExplainer:
    """
    Main class for Python code explanation.
    
    Attributes:
        api_key (str): OpenAI API key
        model (str): GPT model name
        temperature (float): Response creativity
        max_tokens (int): Maximum response length
    
    Methods:
        explain_code(code: str, **kwargs) -> str
        generate_documentation(code: str, **kwargs) -> str
        suggest_improvements(code: str, **kwargs) -> List[str]
        batch_explain(file_paths: List[str]) -> Dict[str, str]
    """
```

### Example Response Format

```json
{
    "explanation": {
        "summary": "Function calculates factorial using recursion",
        "complexity": {
            "time": "O(n)",
            "space": "O(n)"
        },
        "line_by_line": [
            {
                "line": 1,
                "code": "def factorial(n):",
                "explanation": "Function definition with parameter n"
            }
        ]
    },
    "suggestions": [
        "Consider using iteration for better performance",
        "Add input validation for negative numbers"
    ]
}
```

## 🔧 Troubleshooting

### Common Issues

1. **API Key Issues**
   ```bash
   Error: OpenAI API key not found
   ```
   Solution: Ensure API key is properly set in .env file or environment variables.

2. **Rate Limiting**
   ```bash
   Error: Rate limit exceeded
   ```
   Solution: Implement exponential backoff or reduce request frequency.

3. **Memory Issues**
   ```bash
   MemoryError: Unable to allocate memory
   ```
   Solution: Reduce batch size or implement streaming for large files.

### Debug Mode

Enable debug mode for detailed logging:

```python
explainer = CodeExplainer(debug=True, log_level="DEBUG")
```

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **Fork the Repository**
   ```bash
   git clone https://github.com/bsujalnaik/PythonCodeExplainer.git
   cd PythonCodeExplainer
   ```

2. **Create a Feature Branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```

3. **Make Changes**
   - Write clear, documented code
   - Add tests for new features
   - Update documentation

4. **Run Tests**
   ```bash
   python -m pytest tests/
   ```

5. **Submit Pull Request**
   - Clear description of changes
   - Reference any related issues
   - Update README if needed

### Code Style

Follow these guidelines:
- Use PEP 8
- Write docstrings (Google style)
- Add type hints
- Maximum line length: 88 characters
- Use meaningful variable names

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔮 Future Plans

- [ ] Add support for more programming languages
- [ ] Implement AST-based analysis
- [ ] Add interactive mode
- [ ] Integrate with popular IDEs
- [ ] Support for code generation
- [ ] Add natural language querying
- [ ] Implement custom explanation templates
- [ ] Add support for code metrics
- [ ] Integrate with CI/CD pipelines
- [ ] Add code smell detection

## 📫 Contact

- **Author**: Sujal Naik
- **Email**: [contact@example.com](mailto:contact@example.com)
- **Project Link**: [https://github.com/bsujalnaik/PythonCodeExplainer](https://github.com/bsujalnaik/PythonCodeExplainer)
- **Blog**: [https://example.com/blog](https://example.com/blog)
- **Twitter**: [@example](https://twitter.com/example)

## ⭐ Show your support

Give a ⭐️ if this project helped you!

## 🙏 Acknowledgments

- OpenAI for providing the GPT API
- Python community for inspiration
- All contributors to this project

---
*Made with ❤️ by [Sujal Naik](https://github.com/bsujalnaik)*
