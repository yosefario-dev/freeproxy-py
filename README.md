# freeproxy

[![Python](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-GPL%20v3-blue.svg)](LICENSE)

HTTP proxy library for Python using CroxyProxy infrastructure.

## Installation

```bash
pip install curl-cffi
```

## Usage

```python
import freeproxy

# Simple usage
response = freeproxy.get("https://example.com")
print(response.text)

# Session-based
proxy = freeproxy.FreeProxy()
response = proxy.get("https://example.com/api")
proxy.close()

# Context manager
with freeproxy.FreeProxy() as proxy:
    response = proxy.get("https://example.com")
```

## API

### FreeProxy Class

```python
FreeProxy(timeout=30, max_retries=3)
```

**Methods:**
- `get(url, **kwargs)`
- `post(url, **kwargs)`  
- `put(url, **kwargs)`
- `delete(url, **kwargs)`
- `head(url, **kwargs)`
- `patch(url, **kwargs)`
- `get_session_info()`
- `close()`

### Convenience Functions

```python
freeproxy.get(url, **kwargs)
freeproxy.post(url, **kwargs)
freeproxy.put(url, **kwargs)
freeproxy.delete(url, **kwargs)
freeproxy.head(url, **kwargs)
freeproxy.patch(url, **kwargs)
```

## Error Handling

```python
try:
    response = freeproxy.get("https://example.com")
except freeproxy.ProxyError as e:
    print(f"Proxy error: {e}")
```

## Requirements

- Python 3.7+
- curl-cffi

## License

GNU General Public License v3.0
