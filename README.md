# Maximize available disk space for build OpenWrt job

This will uninstall most of the development packages pre-installed on the system and create a volume group using the `/mnt` and `/` spaces.

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
        with:
          root-reserve-gb: 4
          swap-size-gb: 4

      - name: Checkout
        uses: actions/checkout@main

      - name: Build
        run: |
          echo "Free space:"
          df -h
```

## Inputs

```yaml
  root-reserve-gb:
    description: 'Space to be left free on the root filesystem, in GB.'
    required: false
    default: '2'
  swap-size-gb:
    description: 'Swap space to create, in GB.'
    required: false
    default: '12'
```
