# Pydantic Env Settings

Wrapper around [BaseSettings](https://docs.pydantic.dev/usage/settings/).

Sets the usage of the .env file as default.

Modifies the error description while parsing .env file:
- marks it is a settings validation error
- renames the field names by adding the env_prefix and uppercaseing it
- gives hint about .env file

## Installation

Using pip:

```
pip install pydantic-env-settings
```

## Usage

```python
class MySettings(EnvSettings):
    filename: str
    verbose: bool

    class Config:
        env_prefix = 'MY_'

settings = MySettings()

print(settings.filename)
print(settings.verbose)
```

Then your .env file should contain:

```ini
MY_FILENAME = /tmp/tempfile.bin
MY_VERBOSE = true
```