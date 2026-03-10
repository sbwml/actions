# Maximize available disk space for build OpenWrt job

ps: uses before `actions/checkout`

## Usage

```yaml
name: Test
on: push

jobs:
  build:
    name: Test
    runs-on: ubuntu-24.04
    steps:
      - name: Free disk space
        uses: sbwml/actions@free-disk

      - name: Checkout
        uses: actions/checkout@main

      - name: Build
        run: |
          echo "Free space:"
          df -h
```
