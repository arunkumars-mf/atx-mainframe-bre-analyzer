# Development Guide

## Project Structure

```
atx-mainframe-bre-analyzer/
├── src/
│   └── atx_mainframe_bre_analyzer/
│       ├── __init__.py
│       └── server.py
├── tests/
├── examples/
├── pyproject.toml
├── README.md
└── LICENSE
```

## Environment Setup

### Prerequisites
- Python 3.8+
- ATX Business Rules Extraction output directories

### Installation
```bash
# Development installation
pip install -e .

# Or install from PyPI
pip install atx-mainframe-bre-analyzer
```

### Environment Variables
```bash
export ATX_MF_APPLICATION_LEVEL_BRE="/path/to/application/level/bre"
export ATX_MF_COMPONENT_LEVEL_BRE="/path/to/component/level/bre"
```

## Testing

### Running as MCP Server
```bash
# Test the server directly
python -m atx_mainframe_bre_analyzer.server
```

### Integration Testing
Configure in your MCP client and test the available tools:
- `list_business_functions`
- `get_business_function_details`
- `list_all_components`
- `search_components`
- `get_bre_overview`

## Building and Publishing

### Build Package
```bash
python -m build
```

### Publish to PyPI
```bash
python -m twine upload dist/*
```

## Architecture

The BRE Analyzer works with ATX Business Rules Extraction output:

1. **Application Level BRE**: Contains business function directories with entry points
2. **Component Level BRE**: Contains COBOL and JCL component analysis files
3. **MCP Integration**: Provides structured access via Model Context Protocol

## Adding New Features

1. Add new tools in `server.py`
2. Update the tool list in `handle_list_tools()`
3. Implement the handler in `handle_call_tool()`
4. Update documentation and tests
