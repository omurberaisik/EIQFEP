EIQFEP ---

Field	Value
Project name	EIQFEP — Every Image Quality For Every PC
Summary (≤ 250 chars)	A from-scratch Iris shader pack with 5 quality levels: volumetric clouds, colored block light, ray-traced GI/lights (Ultra), a custom Nether and End, and a Style switch (Natural / vivid BSL-like / Dark Mode) with a full Fine Tune menu. Early alpha — feedback wanted.
Category	Shaders (Customization)
Mod loader / requires	Iris Shaders (Fabric/NeoForge, with Sodium). Not OptiFine-tested.
Game versions	The pack targets Minecraft Java 26.x (26.3). Tick only the versions you can name; I could not test in-game.
Release type for the file	Alpha
License	Apache License version 2.0
Links	https://github.com/omurberaisik/EIQFEP
Screenshots	None for now (planned for a later version, e.g. 0.1.0).

Tags: shaders, iris, realistic, vanilla-friendly, volumetric-clouds, colored-lighting, ray-tracing, nether, end.


EIQFEP — Every Image Quality For Every PC
⚠️ Early alpha — please read

EIQFEP has not been tested on a real computer yet. Everything so far was verified in a software OpenGL (Mesa llvmpipe) simulation that imitates how Iris runs a shader pack. That catches many bugs (every one of the 195 shader programs compiles, and the options were swept for NaN/black screens), but it is not the same as a real GPU + driver + Iris + Minecraft. Things that behave differently on real hardware — performance, driver quirks, exact brightness, Iris-specific behaviour — are still unknown.

Your feedback is the most important part of this release. If you try it, please tell me what works, what looks wrong and what runs badly. See "How to give feedback" below.

What is it?

EIQFEP is a shader pack for Iris, written completely from scratch (no code from any other shader pack). The idea: one pack, five quality levels, so the same pack can run on a weak laptop or a strong gaming PC. Change the level in the first line of the shader menu — everything else is the same pack.

Quality levels
Level	Name	Highlights
1	Performance	1024 shadows, FXAA, cheap sky/clouds, no AO
2	Low	Colored shadows, 4-sample SSAO, procedural normals, clouds
3	Medium	Soft PCSS shadows, contact shadows, GTAO, TAA, volumetric light, SSR, bloom, colored block light (LPV)
4	High	More samples, sharpening, longer SSR / volumetrics, larger light volume, ray tracing on
5	Ultra	4096 shadows, 24-tap soft shadows, 40-step SSR, 24-step light shafts, largest light volume, ray-traced GI / lights / reflections
Main features

Sky & weather

Physically inspired atmosphere (sunrise/sunset, twilight, sun halo), large adjustable sun, moon, stars, aurora, shooting stars
Volumetric clouds + high cirrus layer, cloud shadows, light shafts (god rays)
Rain, thunder flashes, wet surfaces with puddles and ripples, snow sparkle, biome fog (desert dust, humid air), morning mist

Lighting

Soft shadows (PCSS) with colored shadows through stained glass
GTAO ambient occlusion, contact shadows
Colored block light (LPV): glowing blocks light their surroundings in their own color (soul torch = blue, redstone = red, amethyst = purple, lava, glowstone…). Handheld lights too. Visual only — does not change the real game light level.
Ray tracing (Level 4–5): voxel ray-traced global illumination, light selection with colored shadow rays ("MegaLight"-style), ray-traced reflections where screen-space reflections miss. Needs OpenGL 4.3+; automatically falls back to vanilla block light on older GPUs/macOS.

Water & materials

Animated waves, reflections, refraction, absorption, caustics, foam
Automatic surface detail for textures without a normal map; labPBR support

Nether & End

Nether rewritten: real ambient light, biome-aware colors and fog, glowing lava sea, heat haze, embers
The Eye: a black hole in the Nether/End sky with an accretion disk and lensing; in the End it is the key light of the dimension
End nebula, aurora, void motes, volumetric fog

Image & color

6 tonemappers: EIQ, ACES, Filmic, Neutral, AgX, AgX Punchy
Auto exposure, bloom, vibrance, saturation, contrast, color temperature, vignette
Optional (off by default): motion blur, depth of field, lens flare, rain drops, film grain, chromatic aberration
HDR output when the "Shaders + HDR" mod is installed and HDR is on
Experimental Distant Horizons support
New in 0.0.2 / 0.0.2.1
Style switch: EIQ (natural) · BSL-like (vivid, warm sun + blue shadows) · Dark Mode (moody, dark nights and caves, high contrast)
Fine Tune menu — make it look the way you like: ambient light, sunlight strength, shadow tone (warm ↔ cool), sky saturation/brightness, cloud brightness, fog density, cave darkness, water turbidity, night brightness, exposure, contrast, saturation, vibrance, color temperature, bloom, vignette, tonemap. Sliders stack on top of the chosen style.
Adaptive Quality (Performance screen): lowers shadow filtering, AO, ray-traced GI and generated normals with distance to save GPU time. Turn it off for full quality at every range.
Nights are dimmer in the default look (still adjustable).
Many bug fixes: blindness effect now darkens the sky, several NaN/divide-by-zero guards, full option sweep.
Installation
Install Iris (with Sodium) for your Minecraft version.
Put the downloaded .zip into your shaderpacks folder — do not unzip it.
Important (Minecraft 26.2+): if your game has the Graphics API setting, set it to OpenGL (Options → Video Settings). Iris does not work with the native Vulkan renderer.
In-game: Options → Video Settings → Shader Packs → choose EIQFEP.
Pick a Quality Level (first entry), then a Style. Not sure? Start at Level 2–3 and go up while the game stays smooth.
Requirements
Minecraft Java Edition with Iris (Sodium)
A GPU/driver with OpenGL 3.3+ for Levels 1–2; OpenGL 4.3+ (compute shaders, image load/store) for Levels 3–5 (colored light, ray tracing)
Ray tracing (Levels 4–5) is heavy — expect it to need a fairly strong GPU. I do not have real performance numbers yet.
Known limitations
Not tested on real hardware yet (see the warning at the top). Performance numbers do not exist yet; tell me yours!
The BSL-like and Dark Mode looks were tuned in a small synthetic test world, not in real biomes — use Fine Tune to match your taste, and tell me what looks off.
The torch in your hand lights the surroundings but the held model itself does not glow yet.
Distant Horizons support, the Nether biome colors and the End/Nether eye lighting are experimental.
macOS / old GPUs: colored light and ray tracing fall back to vanilla block light.
The menu is available in English and Turkish.
How to give feedback

This is an alpha — every report helps, including "it just works fine". Please include:

PC: GPU model + driver version, OS, CPU (laptop or desktop)
Game: Minecraft version, Iris version, Sodium version, other mods that affect rendering (Distant Horizons, HDR mod, etc.)
Pack settings: Quality Level, Style, and anything you changed
What happened: a screenshot or short clip if you can, and when it happens (time of day, weather, dimension, underwater…)
FPS: roughly what you got, and on which level / render distance
If the pack fails to load: the error text (Iris shows it in chat / latest.log)

Especially valuable right now:

Does it load at all on your GPU (NVIDIA / AMD / Intel / Apple)?
Performance per quality level, with and without Adaptive Quality
Anything that looks too dark, too bright, flickering, noisy or glitchy (especially nights, caves, water, Nether, End)
Whether the BSL-like and Dark Mode styles look good in your world

Thank you for testing — this pack will get better with your help!







Note: As this shader is still under development, it may contain residual elements.
