# Ansible Collection - mriamah.uv

Manage Python versions and installations using the [uv](https://github.com/astral-sh/uv) Python package manager.

![Galaxy](https://img.shields.io/badge/ansible--galaxy-0.1.10-blue)
![Build](https://img.shields.io/badge/build-passing-brightgreen)

## Requirements

- Ansible `2.12` or higher.
- `uv` installed and available on `PATH`.
- `uv` version ≥ `0.8.0`.

## Installation

Install via Ansible Galaxy:

```bash
ansible-galaxy collection install mriamah.uv
```

## Collection Contents

This collection provides tools to manage Python versions using the `uv` Python package manager.

### Modules
#### python
  - Installs, uninstalls, and upgrades Python versions.
  - Supports three states:
    - `present` – ensures a specific Python version is installed.
    - `absent` – removes specified Python version.
    - `latest` – installs the latest patch version for a minor release.
  - Returns facts for further playbook usage:
    - `python_versions` (list) - list of versions changed.
    - `python_paths` (list) - List of installation paths of Python versions changed.

### Notes
- Designed for Ansible 2.12+ and uv ≥ 0.8.0
- All module operations are idempotent and support `check_mode`.

## Example Usage

```yaml
- name: Install Python 3.12.3
  mriamah.uv.python:
    version: 3.12.3
    state: present
```

```yaml
- name: Remove Python 3.12
  mriamah.uv.python:
    version: 3.12
    state: absent
```

```yaml
- name: Install latest patch for 3.12
  mriamah.uv.python:
    version: 3.12
    state: latest
```

## License

GNU General Public License v3.0+ (see COPYING or https://www.gnu.org/licenses/gpl-3.0.txt)

## References

- [UV documentation – Python versions](https://docs.astral.sh/uv/concepts/python-versions/)
- [UV CLI reference](https://docs.astral.sh/uv/reference/cli/#uv-python)
