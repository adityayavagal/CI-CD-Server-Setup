# Installing Mono MSBuild Latest Linux

### Add latest mono repository to your system

```bash
sudo apt install gnupg ca-certificates
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb https://download.mono-project.com/repo/ubuntu stable-bionic main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
```

### Install Mono
```bash
sudo apt install mono-devel
```

## Install Nuget Package Manager (Optional)

```bash
sudo apt install nuget
nuget update -self
```

**References**
- [Mono-Project](https://www.mono-project.com/docs/)
- [Nuget Tutorial](https://docs.microsoft.com/en-us/nuget/tools/nuget-exe-cli-reference)
