# Remote Access: A (Non)Comprehensive Guide

## Installing VSCode
VSCode is a commonly used IDE, and apparently the de facto editor used for this course. VSCode can be downloaded from the [official website](https://code.visualstudio.com/), and is available for Windows and most \*nix systems. The download page should look something like this:
![VSCode Homepage](images/remote_access/vscode_site.png)

The installation process is about as straightforward as it gets. You run the installer as you would with any executable. The exact installation process depends on your system, but as of 01/30/2023, the Windows x86_64 installer should first present a license agreement, then prompt for a destination location, a start menu alias, and then various installation settings. You can customize any of these as you see fit (except the license agreement, which must be accepted), but the defaults are honestly fine. Finalize the installation and you're good to go.

In short: Just keep clicking next until VSCode installs. If you're feeling especially quirky and want to embrace Web3, GitHub has an online VSCode editor available [here](https://github.dev). It's probably easier to just follow this tutorial and install it locally, however.

Images of each prompt are attached below:

![License Agreement](images/remote_access/license.png)
![Destination Location](images/remote_access/destination.png)
![Start Menu Alias](images/remote_access/start.png)
![Installation Settings](images/remote_access/installation.png)
![Confirmation Page](images/remote_access/confirmation.png)

## Remotely Connecting
VSCode should have options to remotely connect to servers. There's an included terminal that you can use, and if memory serves correctly, there are also extensions you can download to make your job easier. Since, again, I don't actually use this IDE, I can't offer guidance on how to do it.

Instead, I'll detail the remote access process for Linux. I'm using a Debian-based system (Ubuntu 20.04 Focal Fossa), but this process should be universal across any Linux system. And most \*nix systems, now that I think about it.

Almost every distro should come with `ssh` shipped, but it should be widely obtainable from online sources if not. Use the appropriate package manager (`apt` for for Debian-based systems) and install as needed. If your sources are compromised or the `ssh` package is otherwise not available, OpenSSH provides binaries on their [website](https://www.openssh.com/).

For CSE15L, we'll be using the SSH gateway (?) found at `ieng6.ucsd.edu`. Specify your corresponding user account and append the hostname, separating the two with and `@`. It should look something like this:

```
ssh cs15lwi23zz@ieng6.ucsd.edu
```

Enter the password when prompted, and you should be connected to the system. Successful access should look like the following:
![SSH Success](images/remote_access/ssh_success.png)

## Trying Some Commands
Now that we have remote accesss, let's run some basic diagnostic commands. First, we'll figure out what interpreter we're running. Run `echo  $0` and note the result. It looks like the configuration for CSE15L defaults to `bash`.

![Verifying the current interpreter](images/remote_access/interpreter_result.png)

We can also look at what user we're running commands as and get an idea of where we are and what that filesystem looks like. The following table has a few recommended commands:

|    Command    |                Behavior                   |
| ------------- | --------------------------------------    |
|   `whoami`    | Displays the name of the current user     |
|    `pwd`      | Displays the current working directory    |
|     `ls`      | Lists the files in the supplied directory |

![Looking around](images/remote_access/looking_around.png)

We can also look at various other bits of interesting system information, like currently used resources (via `top`) or available disk space (via `df`), but that's a bit out of scope for a remote access tutorial.

Good times were had by all.