# Ansible Collection - mriamah.uv_python

Manage Python versions and installations using the C(uv) Python package manager.

![Galaxy](https://img.shields.io/badge/ansible--galaxy-0.1.0-blue)
![Build](https://img.shields.io/badge/build-passing-brightgreen)

## Requirements

- Ansible 2.12 or higher
- C(uv) installed and available on PATH
- C(uv) version ≥ 0.8.0

## Installation

Install via Ansible Galaxy:

```bash
ansible-galaxy collection install mriamah.uv_python
```

## Collection Contents

This collection provides tools to manage Python versions using the C(uv) Python package manager.

### Modules
- **`uv_python`**
  - Installs, uninstalls, and upgrades Python versions.
  - Supports three states:
    - `present` – ensures a specific Python version is installed
    - `absent` – removes specified Python version
    - `latest` – installs the latest patch version for a minor release
  - Returns facts for further playbook usage:
    - `python_versions` (list) - list of versions changed.
    - `python_paths` (list) - List of installation paths of Python versions changed.

### Roles
- *(none included in this release)*

### Plugins
- *(none included in this release)*

### Notes
- Designed for Ansible 2.12+ and uv ≥ 0.8.0
- All module operations are idempotent and support `check_mode`.

## Example Usage

```yaml
- name: Install Python 3.12.3
  uv_python:
    version: 3.12.3
    state: present
```

```yaml
- name: Remove Python 3.12
  uv_python:
    version: 3.12
    state: absent
```

```yaml
- name: Install latest patch for 3.12
  uv_python:
    version: 3.12
    state: latest
```

## License

GPL-2.0-or-later

## References

- [UV documentation – Python versions](https://docs.astral.sh/uv/concepts/python-versions/)
- [UV CLI reference](https://docs.astral.sh/uv/reference/cli/#uv-python)
