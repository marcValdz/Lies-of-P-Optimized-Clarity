# A Graphics Overhaul Mod for [Lies of P](https://store.steampowered.com/app/1627720/Lies_of_P/)
This mod changes how the each Graphic Detail Settings work. I highly recommend tuning the settings to your liking instead of using the Graphics Presets (except for maxing or lowering the settings all at once).

# WindowsScalability.ini Tweaks
The following modifications affect the in-game graphics options.
## Visibility (New Optimal: High)
This setting scales the view distance (LOD) of the game. Vanilla's **Best** setting trades good performance for very obvious pop-in (e.g. Practice Area Wall, Geppetto’s Carriage).

This mod modifies the **High** and **Best** settings to provide seamless LOD transitions at the cost of performance.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.StaticMeshLODDistanceScale`|1.5|1.0 (1.2)|0.1 (1)|0.1 (1)|This setting fixes the Practice Area Wall pop-in and other areas like it.|
|`r.HLOD.DistanceScale`|0.9|1.0 (0.9)|2.0 (0.9)|8.0 (1)|This setting fixes Geppetto’s Carriage pop-in. The new maximum setting improves geometry detail of objects from afar (e.g. bridges).|
|`r.ViewDistanceScale`|1 (0.9)|1.0 (0.9)|2.0 (1.0)|4.0 (1)|After more testing, lowering this setting below 1.0 doesn’t provide much performance gain to justify the decrease in draw distance.|
|`r.SkeletalMeshLODBias`|1 (1)|0 (1)|-1 (0)|-1 (0)|Higher values cause NPC LOD pop-in (e.g., practice area puppets).|

## Anti-aliasing Quality (New Optimal: Subjective)
Originally, no matter what setting this is set to, TAA is used. Now this setting allows people to turn off AA completely or use FXAA instead.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.PostProcessAAQuality`|0 (3)|2 (3)|4|6 (5)|0: NoAA, 2: FXAA, 4: TAA, 6: TAA with Sharpening|
|`r.Tonemapper.Sharpen`|0.9|1.0 (0.9)|2.0 (0.9)|8.0 (1)|**High** is for native operation, while **Best** is paired with FSR (0% Sharpness Slider) or DLSS (100% Sharpness Slider).|

## Post-processing Quality (New Optimal: Subjective)
The game natively provides a way to disable motion blur, but other effects like Bloom and DOF don't have their own toggles. This mod allows disabling of those effects as well.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.MotionBlurQuality`|0 (1)|2 (3)|3 (3)|4|Adjusts the quality of motion blur. Lower values disable or reduce the effect, while higher values enhance it.|
|`r.DepthOfFieldQuality`|0 (1)|1 (1)|3 (2)|4 (2)||
|`r.BloomQuality`|0 (5)|2 (5)|4 (5)|5|Higher settings add a “flare” to light sources (e.g., candles in lanterns). These flares have a tendency to flicker, especially with DLSS enabled.|

## Shadow Quality (New Optimal: Medium)
I debated if I should’ve given the option to completely disable shadows, but I opted to not do that as the game’s foliage looks utterly horrendous and downright broken without it. Instead, the lowest setting still retains shadows, but at a much lower resolution.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.ShadowQuality`|2 (3)|3 (3)|4 (5)|5 (5)|Adjusts shadow filtering quality, ranging from low to high filtering. The lowest setting has no filtering at all.|
|`r.Shadow.CSM.MaxCascades`|2 (1)|2 (1)|2 (2)|2 (2)|Ensures consistent shadows by setting all presets to 2, preventing blurry and pixelated shadows.|
|`r.Shadow.MaxCSMResolution`|1024 (512)|2048 (1024)|4096 (1440)|8192 (1650)|Resolutions now scale linearly, significantly improving shadow quality. Higher resolutions like `8192` are very resource-intensive.|
|`r.Shadow.RadiusThreshold`|0.01 (0.05)|0.01 (0.03)|0.01 (0.02)|0.01 (0.01)|Shadows smaller than this value get culled. Setting all presets to 0.01 prevents noticeable pop-in without a significant performance hit.|
|`r.Shadow.DistanceScale`|1 (0.3)|1 (0.7)|1 (0.85)|2 (1.0)|Removes obvious cutoff distances for shadows by increasing the distance scale.|
|`r.ContactShadows`|0 (1)|0 (1)|0 (1)|1 (1)|Disables distracting, pixelated shadows in motion for Low, Medium, and High. Enabled on **Best** for screenshot purposes.|

## Texture Quality (Unchanged, depends on your GPU’s VRAM)

## Effect Quality (New Optimal: Medium)
Another setting where I debated on, specifically in the implementation of Screen Space Global Illumination (SSGI). In the end, I've relegated SSGI only to **Best** as it is the most expensive raster effect (sometimes more than RT surprisingly).

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.SSGI.Quality`|0 (0)|0 (0)|0 (2)|4 (3)|Enabled on **Best** for screenshot purposes.|

## Vegetation Quality (Unchanged)

## Shading Quality (GTAO)
Performance testing showed that there's no performance/visual difference in changing this setting, so I decided to implement GTAO on this setting's **Best** option.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.AmbientOcclusion.Method`|0 (-)|0 (-)|0 (-)|1 (-)|GTAO's presentation makes some areas of the game extremely dark. It is also quite expensive to the point where sometimes RTAO might be the better choice when optimizing for Fidelity.|

## Reflection Quality (New Optimal: High)
SSR is the most interesting setting here since the developers likely optimized their materials around r.SSR.Quality = 2. Anything higher fails to correctly display reflections, not to mention is more expensive. Just turn on RT reflections instead.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.SSR.Quality`|1 (1)|1 (2)|2 (2)|2 (4)|**Low** and **Medium** SSR captures less objects within the reflections. Performance testing shows no FPS difference, however.|
|`r.SSR.HalfResSceneColor`|1 (1)|0 (1)|1 (1)|0 (0)|**Low** and **High** cuts the SSR resolution in half which makes it blurrier and less stable (flickering) in motion. It theoretically increases FPS, but once again, performance testing doesn't show any difference, aside from it being uglier.|
|`r.SSR.MaxRoughness`|0.7 (-)|0.8 (-)|0.9 (-)|1 (-)|Higher values allow more materials to have a reflective surface. This however increases specular aliasing which is quite distracting in motion. It can be hidden by TAA of course, but now you're sacrificing image quality as a whole for a shinier surface, congrats.|

## Volumetric Fog Quality (New Optimal: High, Low turns off Volumetric Fog)
In my opinion, the default volumetric fog looks very pixelated and unstable in motion, though admittedly, it is fast in terms of FPS. Scenes where you can notice the low volumetric resolution are few and far between, but when the scene is there, it is very jarring.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.VolumetricFog`|0 (1)|1 (1)|1 (1)|1 (1)|Disabling volumetric fog does increase performance, but drastically changes the game's presentation.|
|`r.VolumetricFog.GridPixelSize`|16 (24)|8 (18)|6 (16)|4 (12)|Controls the pixelation of the fog. Lower values reduce pixelation but are more performance-heavy.|
|`r.VolumetricFog.GridSizeZ`|16 (24)|32|64|128 (80)|Determines the "intensity" of the fog. A higher value leads to more intensity but can create more pixelation if not paired with lower GridPixelSize.|

## Ambient Occlusion Quality (New Optimal: Medium)
AO is now unclamped from the post-process volume. Additionally, if Shading Quality is set to **Best**, this setting controls how GTAO looks and performs.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.AmbientOcclusionMaxQuality`|0 (30)|33 (40)|66 (50)|100 (60)||
|`r.AmbientOcclusionLevels`|0 (-1)|1 (-1)|2 (-1)|3 (-1)||
|`r.AmbientOcclusionRadiusScale`|0 (0.4)|0.33 (0.6)|0.66 (0.8)|1|Higher values increase the "thickness" of the AO around objects.|
|`r.GTAO.SpatialFilter`|0 (-)|0 (-)|0 (-)|0 (-)|GTAO by itself already makes the game darker. A value of 1 makes the game extremely dark to the point of unplayability.|
|`r.GTAO.UseNormals`|(-)|1 (-)|1 (-)|1 (-)|Without this setting, GTAO looks more "polygonal." A value of 1 allows GTAO to recognize *normals*, which smooths out the AO.|
|`r.GTAO.Downsample`|(-)|1 (-)|1 (-)|0 (-)|Halves the resolution of GTAO allowing it to run much better, at the cost of instability (jitter) and blockyness (pixelation).|
|`r.GTAO.NumAngles`|(-)|5 (-)|5 (-)|5 (-)|A value of 5 seems to be the best balance of visuals:FPS ratio. This effectively controls the *resolution* of GTAO. Higher values can quickly tank performance.|
|`r.GTAO.ThicknessBlend`|(-)|1.0 (-)|0.2 (-)|0.1 (-)|Similar to `r.AmbientOcclusionRadiusScale`, it controls how "thick" the AO is around objects. The *Medium* setting omits a lot of the AO from smaller objects.|
|`r.GTAO.FalloffEnd`|(-)|0 (-)|10 (-)|20 (-)|Controls the distance at which objects will exhibit more AO.|

## Anisotropy Filter Quality (New Optimal: Best)
Lastly, AF only goes up to 8x, likely due to this game also being ported to other platforms besides PC. But on PC, we want 16x, and this mod allows that.

|Setting|----Low----|--Medium--|----High----|----Best----||
|--|--|--|--|--|--|
|`r.MaxAnisotropy`|0 (0)|4 (4)|8 (8)|16 (16)||
|`r.VT.MaxAnisotropy`|0 (4)|4 (8)|8 (16)|16 (16)||

# WindowsEngine.ini Tweaks
These settings have a higher priority than scalable settings. Most of these settings are set by constructor at runtime.

## AA Tweaks courtesy of TheHybred

|Setting|Value||
|--|--|--|
|`r.TemporalAAPauseCorrect`|1 (0)|Holds onto render targets longer, preventing reuse, but consumes more memory.|
|`r.TemporalAACatmullRom`|1 (0)|Uses the CatmullRom filter instead of Gaussian.|
|`r.TemporalAA.R11G11B10History`|1 (0)|TAA Optimization. Don't really know what it does.|
|`r.TemporalAA.HistoryScreenPercentage`|200 (100)|Increases motion clarity at native or higher resolutions, but flickers light sources with bloom. Quite performance-heavy.|
|`r.TemporalAACurrentFrameWeight`|0 (0.04)|Higher values increase clarity at the cost of more noticeable jitter and specular aliasing. Overwritten by r.TemporalAA.Algorithm=1.|
|`r.TemporalAASamples`|4 (8)|Lower values reduce jitter but also lower geometry antialiasing quality. Increase if visual errors occur when using r.TemporalAA.Algorithm=1.|
|`r.NGX.DLSS.Preset`|3 (-)|Only Presets 3 and 6 don’t have ghosting in Lies Of P.|
|`r.NGX.LogLevel`|0 (1)|Disables DLSS logging.|

## Other Settings

|Setting|Value||
|--|--|--|
|`r.MipMapLODBias`|-1 (0)|Values less than 0 sharpen textures and foliage, but reintroduce some specular aliasing into the scene. Cost some FPS.|
|`r.MotionBlur.TargetFPS`|0 (-1)|Targets the current FPS with a rolling average, reducing character edge ghosting caused by motion blur.|
|`r.Shadow.CSMDepthBias`|7 (10)|Lower values make shadows start closer to their sources but can cause a moire effect on the ground, especially noticeable on character feet at low CascadeShadowMap resolutions.|
|`r.SSGI.Enable`|1 (0)|The most expensive setting as it simulates *Global Illumination*. It provides extra bounce lighting to objects, and is more accurate at grounding objects than SSAO, but is still inferior to RTAO since it's a ScreenSpace effect: the moment the light source disappears, the bounce lighting also disappears.|
|`r.SSR.Temporal`|1 (0)|Only applies when TAA is on. It makes SSR less grainy and distracting at the cost of lower quality in motion.|

## RT Settings

|Setting|Value||
|--|--|--|
|`r.Reflections.Denoiser`|0 (2)|Completely disables the denoising pass for RT Reflections, saving some FPS.|
|`r.RayTracing.Reflections.ExperimentalDeferred`|1 (0)|Makes RT Reflections look correct, and is surprisingly more performant that the default setting.|
|`r.RayTracing.Reflections.ExperimentalDeferred.Glossy`|0 (1)|Completely disables the jitter when standing still.|
|`r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve`|0 (1)|Disables another denoising step.|
|`r.RayTracing.Reflections.MaxRoughness`|0.3 (-1)|Higher values will allow more materials to be traces at the cost of a noisier presentation. A value of `0.3` is a direct match to `r.SSR.MaxRoughness=0.7`.|
|`r.RayTracing.Reflections.ReflectionCaptures`|0 (0)|Enables reflections within reflections, EXTREMELY expensive. Disabled after denixprince's testing.|
|`r.RayTracing.Shadows.Lights.Directional`|0 (1)|Disables RT Sun Shadows to fix the moire pattern on the ground of Black Sands location.|
|`r.RayTracing.AmbientOcclusion.EnableMaterials`|1 (0)|Fixes the blocky AO near foliage textures. Also reduces AO around characters, especially on the hair.|
|`r.RayTracing.AmbientOcclusion.SamplesPerPixel`|1 (-1)|Higher settings theoretically improves AO quality, but I don't see any quality difference. Performance quickly tanks at values greater than 1.|

# Raytracing!
Currently, the mod allows the usage of raytracing, but ONLY FOR STEAM. For some reason or another, the Gamepass build doesn't respect these settings. I provided my GameUserSettings.ini file within [EnableRT.zip](https://www.nexusmods.com/liesofp/mods/128?tab=files) with the following RT effects toggled on:

|Setting|Description|
|--|--|
|`r.RayTracing.Shadows=True`|RT shadows are much higher in terms of resolution, and it correctly simulates penumbra shadows, but foliage shadows unfortunately don’t animate; very expensive both in terms of FPS and VRAM. Character models weren’t really built with this tech in mind. For example: Sophia’s eyes look very dark which makes her look bizarre from afar, and creepy up close. Geppetto and the Lady Antonia are similarly darkened, especially on their hair.|
|`r.RayTracing.AmbientOcclusion=True`|RTAO is more accurate than SSGI, GTAO and/or AMD CACAO combined. It isn't as expensive as RT Shadows but still uses quite a bit more VRAM.|
|~~`r.RayTracing.SkyLight=True`~~|Game crashes when toggled on.|
|~~`r.RayTracing.GlobalIllumination=False`~~|Game runs like ASS when toggled on, plus there's no visual differences.|
|~~`r.RayTracing.Translucency=False`~~|Breaks Niagara effects (e.g. flying butterflies around Stargazers).|
|`r.RayTracing.Reflections=True`|Most expensive RT setting, but also the most noticeable especially in certain scenes.|

To disable any effect, just set it back to False within GameUserSettings.ini. Check [PCGamingWiki](https://www.pcgamingwiki.com/wiki/Lies_of_P]PCGamingWiki)﻿﻿ for the config file location.
