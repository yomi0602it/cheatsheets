# Linux / Bash Cheatsheet

## Navigation

```bash
pwd                        # Print working directory
ls                         # List files
ls -la                     # List all files with details
cd <dir>                   # Change directory
cd ..                      # Go up one level
cd ~                       # Go to home directory
cd -                       # Go to previous directory
```

## File Operations

```bash
touch <file>               # Create an empty file / update timestamp
mkdir <dir>                # Create a directory
mkdir -p a/b/c             # Create nested directories
cp <src> <dest>            # Copy a file
cp -r <src> <dest>         # Copy a directory recursively
mv <src> <dest>            # Move or rename a file
rm <file>                  # Remove a file
rm -rf <dir>               # Remove a directory recursively (use with caution!)
ln -s <target> <link>      # Create a symbolic link
```

## Viewing & Editing Files

```bash
cat <file>                 # Print file contents
less <file>                # Page through a file
head -n 20 <file>          # First 20 lines
tail -n 20 <file>          # Last 20 lines
tail -f <file>             # Follow a file in real-time
nano <file>                # Open file in nano editor
vim <file>                 # Open file in vim editor
```

## Searching

```bash
grep "pattern" <file>                # Search for pattern in file
grep -r "pattern" <dir>              # Recursive search
grep -i "pattern" <file>             # Case-insensitive search
grep -n "pattern" <file>             # Show line numbers
grep -v "pattern" <file>             # Invert match
find <dir> -name "*.txt"             # Find files by name
find <dir> -type f -mtime -7        # Files modified in the last 7 days
find <dir> -size +100M               # Files larger than 100MB
locate <filename>                    # Find file using database (fast)
```

## Permissions

```bash
chmod 755 <file>           # Set rwxr-xr-x permissions
chmod +x <file>            # Make a file executable
chmod -R 644 <dir>         # Apply permissions recursively
chown user:group <file>    # Change file owner and group
chown -R user:group <dir>  # Change ownership recursively
ls -l                      # View permissions
```

## Process Management

```bash
ps aux                     # List all running processes
ps aux | grep <name>       # Find a process by name
top                        # Interactive process viewer
htop                       # Better interactive process viewer
kill <PID>                 # Kill a process by PID
kill -9 <PID>              # Force kill a process
pkill <name>               # Kill processes by name
bg                         # Resume a job in the background
fg                         # Bring a background job to foreground
jobs                       # List background jobs
nohup <command> &          # Run command immune to hangups
```

## Networking

```bash
ping <host>                # Test connectivity
curl <url>                 # Fetch a URL
curl -O <url>              # Download a file
wget <url>                 # Download a file
ssh user@host              # SSH into a remote host
ssh -i key.pem user@host   # SSH with a key file
scp <file> user@host:<path>  # Copy file to remote host
rsync -avz <src> user@host:<dest>  # Sync files to remote
netstat -tulpn             # Show open ports
ss -tulpn                  # Modern netstat alternative
ifconfig                   # Show network interfaces (older)
ip addr                    # Show network interfaces (modern)
```

## Disk & System

```bash
df -h                      # Disk space usage (human-readable)
du -sh <dir>               # Directory size
du -sh *                   # Size of each item in current directory
free -h                    # Memory usage
uname -a                   # System information
uptime                     # System uptime and load
who                        # Who is logged in
id                         # Current user and group IDs
hostname                   # Show hostname
date                       # Show current date and time
```

## Archives & Compression

```bash
tar -czf archive.tar.gz <dir>          # Create gzip archive
tar -xzf archive.tar.gz                # Extract gzip archive
tar -cjf archive.tar.bz2 <dir>        # Create bzip2 archive
tar -xjf archive.tar.bz2               # Extract bzip2 archive
tar -tf archive.tar.gz                 # List contents of archive
zip -r archive.zip <dir>              # Create zip archive
unzip archive.zip                      # Extract zip archive
```

## Pipes & Redirection

```bash
command > file             # Redirect stdout to file (overwrite)
command >> file            # Redirect stdout to file (append)
command 2> file            # Redirect stderr to file
command &> file            # Redirect both stdout and stderr
command < file             # Redirect file to stdin
cmd1 | cmd2                # Pipe stdout of cmd1 to stdin of cmd2
cmd1 && cmd2               # Run cmd2 only if cmd1 succeeds
cmd1 || cmd2               # Run cmd2 only if cmd1 fails
cmd1 ; cmd2                # Run both commands sequentially
```

## Shell & Environment

```bash
echo $HOME                 # Print an environment variable
export VAR=value           # Set an environment variable
env                        # List all environment variables
alias ll='ls -la'          # Create a command alias
source ~/.bashrc           # Reload shell configuration
history                    # Show command history
!!                         # Repeat last command
!<n>                       # Repeat command number n
Ctrl+R                     # Search command history
Ctrl+C                     # Interrupt current command
Ctrl+Z                     # Suspend current process
```

## Package Management

```bash
# Debian/Ubuntu (apt)
apt update                 # Update package index
apt upgrade                # Upgrade installed packages
apt install <pkg>          # Install a package
apt remove <pkg>           # Remove a package
apt search <pkg>           # Search for a package

# Red Hat/CentOS (dnf/yum)
dnf update                 # Update packages
dnf install <pkg>          # Install a package
dnf remove <pkg>           # Remove a package

# macOS (brew)
brew update                # Update Homebrew
brew install <pkg>         # Install a package
brew uninstall <pkg>       # Uninstall a package
brew list                  # List installed packages
```
