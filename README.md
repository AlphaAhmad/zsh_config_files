# ⚡ My Zsh Setup (Starship + Autosuggestions + Fastfetch)

A minimal, fast Zsh configuration featuring:

- 🚀 [Starship](https://starship.rs/) prompt — custom theme with OS icon, colored directory, git branch/status, and command duration
- 💡 [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) — fish-like history/completion suggestions
- 🖥️ [Fastfetch](https://github.com/fastfetch-cli/fastfetch) — system info banner on shell launch
- 🕘 Shared, persistent shell history

---

## 📁 Repo Contents

| File | Purpose |
|---|---|
| `.zshrc` | Main Zsh config (history, plugins, prompt init) |
| `starship.toml` | Starship prompt theme/config |

---

## 1. Install Zsh

**Fedora**
```bash
sudo dnf install zsh -y
```

**Arch Linux**
```bash
sudo pacman -S zsh
```

**Debian / Ubuntu**
```bash
sudo apt update && sudo apt install zsh -y
```

Set Zsh as your default shell:
```bash
chsh -s $(which zsh)
```
Log out and back in (or restart your terminal) for the change to take effect.

---

## 2. Install Fastfetch

**Fedora**
```bash
sudo dnf install fastfetch -y
```

**Arch Linux**
```bash
sudo pacman -S fastfetch
```

**Debian / Ubuntu**
```bash
sudo add-apt-repository ppa:zhangsongcui3371/fastfetch -y
sudo apt update && sudo apt install fastfetch -y
```
> Fastfetch isn't in the default Debian/Ubuntu repos on older releases — the PPA above covers those. On newer Ubuntu (24.04+) it may be available directly via `apt install fastfetch`.

---

## 3. Install a Nerd Font (required for icons)

The Starship theme uses glyphs (like  and 󰣇) that only render correctly with a [Nerd Font](https://www.nerdfonts.com/).

```bash
mkdir -p ~/.local/share/fonts && cd ~/.local/share/fonts
curl -fLo "JetBrainsMono.zip" https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
unzip JetBrainsMono.zip
fc-cache -fv
```

Then set your terminal emulator's font to **"JetBrainsMono Nerd Font"** (or any Nerd Font of your choice).

---

## 4. Install Starship

Works the same across all distros (official install script):
```bash
curl -sS https://starship.rs/install.sh | sh
```

Or via package manager:

**Arch Linux**
```bash
sudo pacman -S starship
```

**Fedora**
```bash
sudo dnf install starship -y
```

**Debian / Ubuntu**
No official apt package — use the install script above.

---

## 5. Install zsh-autosuggestions

Clone it into the path expected by `.zshrc`:
```bash
mkdir -p ~/.zsh
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
```

---

## 6. Clone This Repo & Link the Configs

```bash
git clone https://github.com/<your-username>/<your-repo>.git ~/dotfiles
```

**Link `.zshrc`:**
```bash
mv ~/.zshrc ~/.zshrc.bak   # backup any existing config
ln -s ~/dotfiles/.zshrc ~/.zshrc
```

**Link `starship.toml`:**
```bash
mkdir -p ~/.config/starship
ln -s ~/dotfiles/starship.toml ~/.config/starship/starship.toml
```

> Using symlinks (`ln -s`) instead of copying means future edits in `~/dotfiles` are picked up automatically — handy since this repo is your source of truth.

---

## 7. Reload Your Shell

```bash
source ~/.zshrc
```

Or just close and reopen your terminal.

---

## ✅ Verify Everything Works

- Fastfetch banner should print on new shell launch
- Typing a previously-run command should show a greyed-out autosuggestion
- Prompt should show your OS icon, username, directory, and git status (if in a repo)

---

## 🔧 Customization

Edit `starship.toml` to tweak colors, symbols, or add new modules (e.g. `$nodejs`, `$python`, `$battery`). See the [Starship config docs](https://starship.rs/config/) for the full module reference.
