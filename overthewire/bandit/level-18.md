# Bandit Level 18

## Objective

The password for the next level is stored in the `readme` file. However, someone modified the `.bashrc` file to automatically log the user out when connecting via SSH.

## What I Learned

### 1. Executing a command through SSH

Normally, SSH is used to open an interactive shell:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

However, SSH can also execute a command directly on the remote machine:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 <command>
```

Instead of opening an interactive shell, the specified command is executed immediately.

This was useful because the normal shell session triggered the logout command.

### 2. What is `.bashrc`?

`.bashrc` is a configuration file used by Bash.

It can contain commands and settings that are automatically executed when Bash starts in certain situations.

For example, a `.bashrc` file may contain:

```bash
alias ll='ls -la'
```

or environment settings:

```bash
export PATH="$PATH:/some/directory"
```

It can also contain regular commands.

### 4. Why did `.bashrc` cause a problem?

In this level, the `.bashrc` file had been modified to automatically log the user out.

Because of this, opening a normal interactive SSH session was not useful.

Instead of relying on the interactive shell, I executed the required command directly through SSH.

## Key Takeaway

SSH can be used for more than opening an interactive remote shell.

A useful pattern is:

```bash
ssh user@host command
```

This executes `command` on the remote system.

Understanding the difference between an interactive shell and directly executing a remote command can help when startup scripts or shell configurations interfere with a normal login session.

## Commands and Concepts

* `ssh user@host command` — execute a command remotely
* `.bashrc` — Bash configuration/startup file
* Interactive shell — a shell where the user manually enters commands
