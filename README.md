# tententgc's Dotfiles

These are my personal dotfiles, the configuration files that customize my shell, editor, and overall command-line environment. By keeping them in a Git repository, I can easily set up a new machine and keep my settings synchronized everywhere.

This setup is inspired by Holman's dotfiles and is organized by topic to keep things clean and modular.

-----

## Installation

Setting up these dotfiles on a new machine is simple.

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/tententgc/dotfiles.git ~/.dotfiles
    ```

2.  **Run the bootstrap script:**

    ```bash
    cd ~/.dotfiles
    script/bootstrap
    ```

The bootstrap script will create symbolic links (symlinks) for any configuration files into your home directory, making them active.

-----

## How It Works

The repository is structured around different "topics" (e.g., `git`, `zsh`, `vim`). This approach has a few key conventions:

  * **`bin/`**: Any executable file in the `bin/` directory will be added to your `$PATH`, making it available as a command in your shell.

  * **`topic/*.zsh`**: Any file ending in `.zsh` will be automatically loaded into your Zsh environment. This is perfect for setting aliases, functions, and environment variables.

  * **`topic/*.symlink`**: Any file ending in `.symlink` will be symbolically linked to your home directory (`~/`). For example, `zsh/zshrc.symlink` will be linked as `~/.zshrc`. This is the core mechanism that activates your configurations.

  * **`topic/install.sh`**: Any file named `install.sh` within a topic folder can be used to install dependencies for that topic (e.g., installing a package with Homebrew). These are run when you execute `script/install`.

-----

## Customization

Feel free to fork this repository and customize it to your heart's content.

#### Adding a New Topic

To add your own configurations for a new tool, just create a new directory and add the relevant files.

For example, to add a configuration for `tmux`:

1.  Create a `tmux` directory: `mkdir tmux`
2.  Add your configuration file and name it with the `.symlink` extension: `touch tmux/tmux.conf.symlink`
3.  Add your settings to `tmux/tmux.conf.symlink`.
4.  Run `script/bootstrap` again, and it will automatically create a symlink at `~/.tmux.conf`.

#### Local Settings

You can create a `~/.localrc` file for any private or machine-specific settings that you don't want to commit to the repository. This file will be automatically loaded if it exists, allowing you to override default settings or add sensitive environment variables.

For example, your `~/.localrc` might contain:

```bash
# ~/.localrc
export GITHUB_TOKEN="your_secret_token"
```

-----

