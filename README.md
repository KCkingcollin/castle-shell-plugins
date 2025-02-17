# Castle Shell Plugins
The official plugins that will come with castle shell
## Installation

```
hyprpm add https://github.com/KCkingcollin/castle-shell-plugins
hyprpm enable hyprbars
```

Note: Unless they fixed it the extra repo is missing a depend for hyprpm you'll need ``hyprwayland-scaner`` to get hyprland plugins to build.
=======
> [!IMPORTANT]
> hyprland-plugins only officially supports installation via `hyprpm`.
> hyprland-plugins follows hyprland-git and requires you to be on hyprland-git
> or tagged >= v0.33.1.

# Plugin list
 - hyprbars -> adds title bars to windows
 - hyprexpo -> adds an expo-like workspace overview

# Nix

NOTE: I do not use Nix, and the Castel-shell project will not use nix, but feel free to try as ive left the files that are needed and I think I altered the corect files, however I have no idea

To use these plugins, it's recommended that you are already using the
[Hyprland flake](https://github.com/hyprwm/Hyprland).
First, add this flake to your inputs:

```nix
inputs = {
  # ...
  hyprland.url = "github:hyprwm/Hyprland";
  hyprland-plugins = {
    url = "github:hyprwm/hyprland-plugins";
    inputs.hyprland.follows = "hyprland";
  };

  # ...
};
```

The `inputs.hyprland.follows` guarantees the plugins will always be built using
your locked Hyprland version, thus you will never get version mismatches that
lead to errors.

After that's done, you can use the plugins with the Home Manager module like
this:

```nix
{inputs, pkgs, ...}: {
  wayland.windowManager.hyprland = {
    enable = true;
    # ...
    plugins = [
      inputs.hyprland-plugins.packages.${pkgs.system}.hyprbars
      # ...
    ];
  };
}
```

# Contributing

Feel free to open issues and MRs with fixes.

Be aware I'm not the originator of some of these apps, go upstream for issues with hyprbars, or expo, but if you have issues installing I'd be happy to help.
