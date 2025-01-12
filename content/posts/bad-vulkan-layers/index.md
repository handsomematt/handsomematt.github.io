---
date: '2025-01-12T10:00:00Z'
title: 'Bad Vulkan Layers'
summary: 'A list of third party Vulkan layers known to cause crashes and how to disable them.'
---

Vulkan offers implicit layers as a way for third party overlays to hook into Vulkan games, these are always enabled regardless of if the third party program is running.

When we switched to [Vulkan in s&box](https://sbox.game/news/vulkan) we had a lot of users reporting crashes, almost all of them were related to out of date or simply malfunctioning layers from programs they weren't actively running or had even thought they'd uninstalled.

{{< figure src="doometernal.jpg" attr="DOOM Eternal disabling layers" width=600 align=center >}}

We explicitly blacklisted a list of layers that were consistently crashing users. There's more elegant ways to handle it like DOOM does with dialogs, but if you're fire fighting crashes these are the main culprits and how to disable them.

### Bad Layers

| Name           | Layer Name                 | Disable EnvVar                     |
|----------------|----------------------------|------------------------------------|
| Twitch Studio  | `VK_LAYER_Twitch_Overlay`  | `DISABLE_TWITCH_VULKAN_OVERLAY`    |
| Overwolf       | `VK_LAYER_OW_OVERLAY`      | `DISABLE_VULKAN_OW_OVERLAY_LAYER`  |
| Overwolf (OBS) | `VK_LAYER_OW_OBS_HOOK`     | `DISABLE_VULKAN_OW_OBS_CAPTURE`    |
| OBS            | `VK_LAYER_OBS_HOOK`        | `DISABLE_VULKAN_OBS_CAPTURE`       |
| Bandicam       | `VK_LAYER_bandicam_helper` | `VK_LAYER_bandicam_helper_DEBUG_1` |
| FPS Monitor    | `VK_LAYER_fpsmon`          | `DISABLE_FPSMON_LAYER`             |
| PlayClaw       | `VK_LAYER_playclaw`        | `DISABLE_PLAYCLAW_LAYER`           |
| ReShade        | `VK_LAYER_reshade`         | `DISABLE_VK_LAYER_reshade_1`       |
| MangoHud       | `MangoHud`                 | `DISABLE_MANGOHUD`                 |
| Riva Tuner     | `VK_LAYER_RTSS`            | `DISABLE_RTSS_LAYER`               |

### Other Layers

Other layers that are circumstantially useful to disable.

| Layer Name                       | Disable EnvVar                          | Comments                                                                                            |
|-------------------------|----------------------------------|-----------------------------------------|-----------------------------------------------------------------------------------------------------|
|  `VK_LAYER_AMD_switchable_graphics` | `DISABLE_LAYER_AMD_SWITCHABLE_GRAPHICS_1` | Recommendation from Nvidia to disable this - we want to run on the dedicated graphics device anyway |
| `VK_LAYER_VALVE_steam_overlay`     | `DISABLE_VK_LAYER_VALVE_steam_overlay_1`  | Useful for disabling Steam overlay in editor                                                        |
| `VK_LAYER_EOS_Overlay`             | `EOS_OVERLAY_DISABLE_VULKAN_WIN64`        | Useful for disabling Epic overlay in editor                                                        |
