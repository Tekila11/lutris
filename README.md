# lutris
Lutris conf for **Arch**

**Step 1:**
installing Lutris 
```bash
  sudo pacman -S wine lutris winetricks wine-mono
```

**Step 2:**
installing **wine** ge.
download protone ge latest by cloning it from [github](https://github.com/GloriousEggroll/proton-ge-custom/releases/tag/GE-Proton9-21)
and use it as a custom runner.
```bash
  git clone https://github.com/GloriousEggroll/proton-ge-custom.git
```
Extrat it to this directory : ```~/.local/share/lutris/runners/wine```.

**Install Dependencies**

Lutris requires some dependencies for optimal performance. Install the following:

```bash
sudo pacman -S wine winetricks lib32-vulkan-icd-loader lib32-nvidia-utils 
```

For **AMD** or **Intel GPUs**:

```bash
sudo pacman -S lib32-vulkan-radeon lib32-vulkan-intel
```

3. Install Game Runtimes (Optional)

For compatibility with Windows games, you may need these:

```bash
sudo pacman -S dxvk-bin vkd3d
```

**Step 3:**
Installing GPU Driver.
First, enable multilib (32-bit support).

To enable multilib repository, uncomment the [multilib] section in /etc/pacman.conf

```bash
/etc/pacman.conf
--------------------------------------------------------------------------------------
[multilib]
Include = /etc/pacman.d/mirrorlist
```

Then upgrade the system 
```bash 
sudo pacman -Syu
```
**NVIDIA:**

*Warning:* Please ensure your graphics card is supported by modern NVIDIA driver before installing. For a list of supported GPUs click here: https://www.nvidia.com/Download/driverResults.aspx/149138/en-us

Proprietary driver and support for Vulkan are required for proper functionality of games.

To install it, execute the following command:

Info: To make sure you're running proprietary NVIDIA drivers on Manjaro you should run 
```bash 
sudo mhwd -a pci nonfree 0300

sudo pacman -S --needed nvidia-dkms nvidia-utils lib32-nvidia-utils nvidia-settings vulkan-icd-loader lib32-vulkan-icd-loader
```

**AMD**

To install support for Vulkan API (will be functional only if you have a Vulkan capable GPU) and 32-bit games, execute following command:

``` bash
sudo pacman -S --needed lib32-mesa vulkan-radeon lib32-vulkan-radeon vulkan-icd-loader lib32-vulkan-icd-loader
```

**Intel**

To install support for Vulkan API (will be functional only if you have a Vulkan capable GPU) and 32-bit games, execute following command:

```bash 
sudo pacman -S --needed lib32-mesa vulkan-intel lib32-vulkan-intel vulkan-icd-loader lib32-vulkan-icd-loader
```

Note for Intel integrated graphics users: Only Skylake and newer Intel CPUs (processors) offer full Vulkan support. Broadwell, Haswell and Ivy Bridge only offer partial support, which will very likely not work with a lot of games properly. Sandy Bridge and older lack any Vulkan support whatsoever.

**Important !!**: for more information please refer to https://github.com/lutris/docs/blob/master/InstallingDrivers.md
