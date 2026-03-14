# linux-dev-envs

A Linux container environment repository for everyday development, including:
- C++ development images and sample projects
- PyTorch/Python development images and sample scripts

The goal is to reuse a consistent dev environment across machines and reduce setup overhead.

## Directory Structure

```text
linux-dev-envs/
├─ Dockerfiles/
│  ├─ cpp-dev/
│  │  └─ Dockerfile
│  └─ pytorch-dev/
│     └─ Dockerfile
├─ CppCodes/
│  └─ test/
│     ├─ CMakeLists.txt
│     ├─ Makefile
│     └─ src/
│        └─ test.cpp
└─ PythonCodes/
   └─ test/
      └─ test.py
```

## Environment Overview

### 1) C++ Development Image

Path: `Dockerfiles/cpp-dev/Dockerfile`

Based on `keepalivewww/cpp-dev:latest`, with common tools installed:
- `git` `curl` `wget` `vim` `htop`
- `build-essential` `ca-certificates`

Default working directory: `/root/Codes`

### 2) PyTorch Development Image

Path: `Dockerfiles/pytorch-dev/Dockerfile`

Based on `keepalivewww/pytorch-dev:latest`, including:
- The same base toolchain as the C++ image
- Common Python packages: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `jupyter`, `transformers`, etc.

Default working directory: `/root/Codes`

## Quick Start

The following commands are intended for Linux/macOS terminals (on Windows, use WSL or PowerShell + Docker).

### Build Images

```bash
# Build C++ development image
docker build -t local/cpp-dev:latest -f Dockerfiles/cpp-dev/Dockerfile .

# Build PyTorch development image
docker build -t local/pytorch-dev:latest -f Dockerfiles/pytorch-dev/Dockerfile .
```

### Use with Dev Container

This repository already includes a devcontainer setup, so you can open it directly in your vscode and use:
- `Reopen in Container`
- `Rebuild Container`
etc

## Sample Projects

### C++ Sample (`CppCodes/test`)

```bash
cd CppCodes/test
make build
make run
```

Expected output:

```text
hello
```

Notes:
- `make debug`: Build in Debug mode
- `make clear`: Remove the `bin` directory

### Python Sample (`PythonCodes/test`)

```bash
cd PythonCodes/test
python test.py
```

This prints the `torch` version available in the current environment.

## Use Cases

- Quickly bootstrap a consistent Linux development environment
- Practice and validate a C++ build workflow (CMake + Make)
- Quickly verify Python/PyTorch dependencies
