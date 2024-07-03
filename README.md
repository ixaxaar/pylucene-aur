# PyLucene AUR

This repository provides the necessary files to build and install PyLucene on Arch Linux and related distros.

## Install

```bash
yay -S pylucene
```

or

```bash
pacaur -S pylucene
```

## Install from repo

1. Clone the repository:
   ```bash
   git clone https://github.com/ixaxaar/pylucene-aur
   cd pylucene-aur
   ```

2. Build and install the package using `makepkg`:
   ```bash
   makepkg -si
   ```

## Usage

After installation, you can use PyLucene in your Python projects as follows:
```python
import lucene
```

## Troubleshooting

For any issues encountered during the installation or usage of PyLucene, refer to the official [PyLucene documentation](https://lucene.apache.org/pylucene/).

