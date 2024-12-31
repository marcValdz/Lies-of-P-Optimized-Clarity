# A Graphics Overhaul Mod for [Lies of P](https://store.steampowered.com/app/1627720/Lies_of_P/)
This mod changes how the each Graphic Detail Settings work. I highly recommend tuning the settings to your liking instead of using the Graphics Presets (except for maxing or lowering the settings all at once).

# WindowsScalability.ini Tweaks
The following modifications affect the in-game graphics options.
## Visibility (New Optimal: High)
This setting scales the view distance (LOD) of the game. Sadly, even the default Best setting doesn’t get rid of very obvious pop-in (e.g. Practice Area Wall, Geppetto’s Carriage). This mod fixes these issues by modifying these values:

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.StaticMeshLODDistanceScale</td>
            <td>Before</td>
            <td>1.5</td>
            <td>1.2</td>
            <td>1</td>
            <td>1</td>
            <td rowspan=2>This setting fixes the Practice Area Wall pop-in and other areas like it.</td>
        </tr>
        <tr>
            <td>After</td>
            <td colspan=4>0.1</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.HLOD.DistanceScale</td>
            <td>Before</td>
            <td>0.9</td>
            <td>0.9</td>
            <td>0.9</td>
            <td>1</td>
            <td rowspan=2>This setting fixes Geppetto’s Carriage pop-in. The new maximum setting improves geometry detail of objects from afar (e.g. bridges).</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0.9</td>
            <td>1.0</td>
            <td>2.0</td>
            <td>8.0</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.ViewDistanceScale</td>
            <td>Before</td>
            <td>0.9</td>
            <td>0.9</td>
            <td>1.0</td>
            <td>1.0</td>
            <td rowspan=2>After more testing, lowering this setting below 1.0 doesn’t provide much performance gain to justify the decrease in draw distance.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>1.0</td>
            <td>1.0</td>
            <td>2.0</td>
            <td>4.0</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.SkeletalMeshLODBias</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>0</td>
            <td>0</td>
            <td rowspan=2>Higher values cause NPC LOD pop-in (e.g., practice area puppets). Setting to -1 for consistency, with minimal performance impact.</td>
        </tr>
        <tr>
            <td>After</td>
            <td colspan=4>-1</td>
        </tr>
    </tbody>
</table>

## Anti-aliasing Quality (New Optimal: High)
Originally, no matter what setting this is set to, TAA is used. Now this setting allows people to turn off AA completely or use FXAA instead.

   <table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.PostProcessAAQuality</td>
            <td>Before</td>
            <td>3</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td rowspan=2>Changes the anti-aliasing quality levels: 0 = AA Off, 2 = FXAA, 4 = TAA, 6 = TAA for Upscaling.</td>
        </tr>
        <tr>
            <td>After</td>
            <td colspan=4>0, 2, 4, 6</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.Tonemapper.Sharpen</td>
            <td>Before</td>
            <td>0</td>
            <td>0</td>
            <td>0.5</td>
            <td>2</td>
            <td rowspan=2>A sharpening filter differentiates High and Best. High is for native operation, while Best is paired with FSR (0% Sharpness Slider) or DLSS (100% Sharpness Slider).</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>0</td>
            <td>0.5</td>
            <td>2</td>
        </tr>
    </tbody>
</table>

## Post-processing Quality (New Optimal: Subjective)
Now this setting acts like an accessibility option, allowing users to disable post-processing completely (no motion blur/DOF/bloom).

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.MotionBlurQuality</td>
            <td>Before</td>
            <td>1</td>
            <td>3</td>
            <td>3</td>
            <td>4</td>
            <td rowspan=2>Adjusts the quality of motion blur. Lower values disable or reduce the effect, while higher values enhance it.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.DepthOfFieldQuality</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>2</td>
            <td>2</td>
            <td rowspan=2>Controls the depth of field effect. Higher values improve visual depth quality, creating more realistic focus transitions.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>1</td>
            <td>3</td>
            <td>4</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.BloomQuality</td>
            <td>Before</td>
            <td>5</td>
            <td>5</td>
            <td>5</td>
            <td>5</td>
            <td rowspan=2>Higher settings add a “flare” to light sources (e.g., candles in lanterns). These flares may flicker, especially with DLSS enabled.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>2</td>
            <td>4</td>
            <td>5</td>
        </tr>
    </tbody>
</table>

## Shadow Quality (New Optimal: Medium)
I debated if I should’ve given the option to completely disable shadows, but I opted to not do that as the game’s foliage looks utterly horrendous and downright broken without it. Instead, the lowest setting still retains shadows, but at a much lower resolution.

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.ShadowQuality</td>
            <td>Before</td>
            <td>3</td>
            <td>3</td>
            <td>5</td>
            <td>5</td>
            <td rowspan=2>Adjusts shadow filtering quality, ranging from low to high filtering.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.Shadow.CSM.MaxCascades</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>2</td>
            <td>2</td>
            <td rowspan=2>Ensures consistent shadows by setting all presets to 2, preventing blurry and pixelated shadows.</td>
        </tr>
        <tr>
            <td>After</td>
            <td colspan=4>2</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.Shadow.MaxCSMResolution</td>
            <td>Before</td>
            <td>512</td>
            <td>1024</td>
            <td>1440</td>
            <td>1650</td>
            <td rowspan=2>Resolutions now scale linearly, significantly improving shadow quality. Higher resolutions like 8192 are resource-intensive.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>1024</td>
            <td>2048</td>
            <td>4096</td>
            <td>8192</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.Shadow.RadiusThreshold</td>
            <td>Before</td>
            <td>0.05</td>
            <td>0.03</td>
            <td>0.02</td>
            <td>0.01</td>
            <td rowspan=2>Shadows smaller than this value get culled. Setting all presets to 0.01 prevents noticeable pop-in without a significant performance hit.</td>
        </tr>
        <tr>
            <td>After</td>
            <td colspan=4>0.01</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.Shadow.DistanceScale</td>
            <td>Before</td>
            <td>0.3</td>
            <td>0.7</td>
            <td>0.85</td>
            <td>1.0</td>
            <td rowspan=2>Removes obvious cutoff distances for shadows by increasing the distance scale.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>1.0</td>
            <td>1.0</td>
            <td>1.0</td>
            <td>2.0</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.LightMaxDrawDistanceScale</td>
            <td>Before</td>
            <td>0.5</td>
            <td>0.5</td>
            <td>1</td>
            <td>1</td>
            <td rowspan=2>Prevents lights from abruptly turning off at a distance by setting all presets to 2.</td>
        </tr>
        <tr>
            <td>After</td>
            <td colspan=4>2</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.ContactShadows</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td rowspan=2>Disables distracting, pixelated shadows in motion for Low, Medium, and High. Enabled for Best for screenshot purposes.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>0</td>
            <td>0</td>
            <td>1</td>
        </tr>
    </tbody>
</table>

## Texture Quality (Unchanged, depends on your GPU’s VRAM)

## Effect Quality (New Optimal: Medium)
Another setting where I debated on, specifically in the implementation of Screen Space Global Illumination (SSGI).

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.SSGI.Quality</td>
            <td>Before</td>
            <td>0</td>
            <td>0</td>
            <td>2</td>
            <td>3</td>
            <td rowspan=2>Screen Space Global Illumination (SSGI) is enabled only on High and Best. Higher values improve quality significantly.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>0</td>
            <td>4</td>
            <td>4</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.SSGI.HalfRes</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>0</td>
            <td rowspan=2>High uses half-resolution SSGI (faster but prone to flickering). Best uses full-resolution SSGI for more stability but at a higher performance cost.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>0</td>
        </tr>
    </tbody>
</table>


## Vegetation Quality (Unchanged)
## Shading Quality (Unchanged)

## Reflection Quality (New Optimal: Low)
SSR is the most interesting setting here since the developers likely optimized their materials around r.SSR.Quality = 2. Anything higher fails to correctly display reflections, not to mention is more expensive. Just turn on RT reflections instead.

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.SSR.Quality</td>
            <td>Before</td>
            <td>1</td>
            <td>2</td>
            <td>2</td>
            <td>4</td>
            <td rowspan=2>Screen Space Reflections (SSR) quality differs for High and Best, but RT Reflections provide a better alternative at these levels.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>1</td>
            <td>2</td>
            <td>4</td>
            <td>4</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.SSR.HalfResSceneColor</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>0</td>
            <td rowspan=2>Alternates resolution quality. Medium and Best deliver the most accurate SSR, while Low and High reduce SSR detail for better performance.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>1</td>
            <td>0</td>
            <td>1</td>
            <td>0</td>
        </tr>
    </tbody>
</table>


## Volumetric Fog Quality (New Optimal: Medium, Low turns off Volumetric Fog)
IMO, the default volumetric fog looks very pixelated, though admittedly, it is fast in terms of FPS. Scenes where you can notice the low volumetric resolution are few and far between, but when the scene is there, it is very jarring.

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.VolumetricFog</td>
            <td>Before</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td rowspan=2>Volumetric fog is now optional for Low. Players can disable it completely for better performance.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.VolumetricFog.GridPixelSize</td>
            <td>Before</td>
            <td>24</td>
            <td>18</td>
            <td>16</td>
            <td>12</td>
            <td rowspan=2>Controls the pixelation of the fog. Lower values reduce pixelation but are more performance-heavy.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>16</td>
            <td>8</td>
            <td>6</td>
            <td>4</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.VolumetricFog.GridSizeZ</td>
            <td>Before</td>
            <td>24</td>
            <td>32</td>
            <td>64</td>
            <td>80</td>
            <td rowspan=2>Determines the "intensity" of the fog. A higher value leads to more intensity but can create more pixelation if not paired with lower GridPixelSize.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>16</td>
            <td>32</td>
            <td>64</td>
            <td>128</td>
        </tr>
    </tbody>
</table>

## Ambient Occlusion Quality (New Optimal: Medium)
AO is now unclamped from the post-processing setting value.

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.AmbientOcclusionMaxQuality</td>
            <td>Before</td>
            <td>30</td>
            <td>40</td>
            <td>50</td>
            <td>60</td>
            <td rowspan=2>Controls the maximum quality of ambient occlusion. Higher values improve quality but are more expensive in terms of performance.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>33</td>
            <td>66</td>
            <td>100</td>
        </tr>
        
        <tr>
            <td rowspan=2>r.AmbientOcclusionLevels</td>
            <td>Before</td>
            <td>0</td>
            <td>-1</td>
            <td>-1</td>
            <td>-1</td>
            <td rowspan=2>Defines the number of ambient occlusion levels available. Higher levels provide more detail but also more performance cost.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>1</td>
            <td>2</td>
            <td>3</td>
        </tr>
        <tr>
            <td rowspan=2>r.AmbientOcclusionRadiusScale</td>
            <td>Before</td>
            <td>0.4</td>
            <td>0.6</td>
            <td>0.8</td>
            <td>1.0</td>
            <td rowspan=2>Adjusts the radius scale for ambient occlusion. A higher value increases the radius, resulting in more pronounced occlusion.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>0.33</td>
            <td>0.66</td>
            <td>1.0</td>
        </tr>
    </tbody>
</table>



## Anisotropy Filter Quality (New Optimal: Best)

Lastly, AF only goes up to 8x, likely due to this game also being ported to other platforms besides PC. But on PC, we want 16x, and this mod allows that.

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th></th>
            <th>Low</th>
            <th>Medium</th>
            <th>High</th>
            <th>Best</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>r.MaxAnisotropy</td>
            <td>Before</td>
            <td>0</td>
            <td>2</td>
            <td>4</td>
            <td>8</td>
            <td rowspan=2>Controls the maximum level of anisotropic filtering. Higher values improve texture sharpness at oblique angles but may impact performance.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>0</td>
            <td>4</td>
            <td>8</td>
            <td>16</td>
        </tr>
        <tr>
            <td rowspan=2>r.VT.MaxAnisotropy</td>
            <td>Before</td>
            <td>4</td>
            <td>4</td>
            <td>8</td>
            <td>8</td>
            <td rowspan=2>Sets the maximum anisotropy for virtual textures. Higher values enhance texture quality at the cost of performance.</td>
        </tr>
        <tr>
            <td>After</td>
            <td>4</td>
            <td>8</td>
            <td>16</td>
            <td>16</td>
        </tr>
    </tbody>
</table>

# WindowsEngine.ini Tweaks
These settings have a higher priority than scalable settings. Most of these settings are set by constructor at runtime.

## AA Tweaks courtesy of TheHybred

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th>Default</th>
            <th>Modified</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>r.TemporalAAPauseCorrect</td>
            <td>0</td>
            <td>1</td>
            <td>Holds onto render targets longer, preventing reuse, but consumes more memory.</td>
        </tr>
        <tr>
            <td>r.TemporalAACatmullRom</td>
            <td>0</td>
            <td>1</td>
            <td>Uses the CatmullRom filter instead of Gaussian.</td>
        </tr>
        <tr>
            <td>r.TemporalAA.R11G11B10History</td>
            <td>0</td>
            <td>1</td>
            <td>TAA Optimization to improve temporal antialiasing.</td>
        </tr>
        <tr>
            <td>r.TemporalAA.HistoryScreenPercentage</td>
            <td>100</td>
            <td>200</td>
            <td>Increases motion clarity at native or higher resolutions, but flickers light sources with bloom. Quite performance-heavy.</td>
        </tr>
        <tr>
            <td>r.TemporalAACurrentFrameWeight</td>
            <td>0.04</td>
            <td>0</td>
            <td>Higher values sharpen but cause noticeable jitter. Overwritten by r.TemporalAA.Algorithm=1.</td>
        </tr>
        <tr>
            <td>r.TemporalAASamples</td>
            <td>8</td>
            <td>4</td>
            <td>Lower values reduce jitter but also lower geometry antialiasing quality. Increase if visual errors occur when r.TemporalAA.Algorithm=1.</td>
        </tr>
        <tr>
            <td>r.NGX.DLSS.Preset</td>
            <td>3</td>
            <td>0-7</td>
            <td>Only Presets 3 and 6 don’t have ghosting in Lies Of P.</td>
        </tr>
        <tr>
            <td>r.NGX.LogLevel</td>
            <td>0</td>
            <td>1</td>
            <td>Controls the logging level (0: default, 1: detailed).</td>
        </tr>
    </tbody>
</table>

## Other Settings

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th>Default</th>
            <th>Modified</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>r.MipMapLODBias</td>
            <td>0</td>
            <td>-1</td>
            <td>Values less than 0 sharpen textures and foliage, but reintroduce some specular aliasing into the scene.</td>
        </tr>
        <tr>
            <td>r.Shadow.CSMDepthBias</td>
            <td>10</td>
            <td>7</td>
            <td>Lower values cause a moire effect on the ground and make shadows start closer to their sources, especially noticeable on character feet at low CascadeShadowMap resolutions.</td>
        </tr>
        <tr>
            <td>r.SSR.Temporal</td>
            <td>0</td>
            <td>1</td>
            <td>SSR is less grainy with this on but loses some detail in motion.</td>
        </tr>
        <tr>
            <td>r.MotionBlur.TargetFPS</td>
            <td>-1</td>
            <td>0</td>
            <td>Targets the current FPS with a rolling average, reducing character edge ghosting caused by motion blur.</td>
        </tr>
        <tr>
            <td>r.SSGI.Enable</td>
            <td>0</td>
            <td>1</td>
            <td>The most expensive setting but also the most noticeable. It is more accurate for grounding objects and enabling bounce lighting, though it disappears when light sources do. It’s different from SSAO.</td>
        </tr>
    </tbody>
</table>

## RT Settings
<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th>Default</th>
            <th>Modified</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>r.Reflections.Denoiser</td>
            <td>2</td>
            <td>0</td>
            <td>When enabled, it reduces the quality of deferred RT reflections and doesn’t resolve motion graininess.</td>
        </tr>
        <tr>
            <td>r.Reflections.Denoiser.ReconstructionSamples</td>
            <td>8</td>
            <td>0</td>
            <td>Setting this to 0 likely disables the denoising step altogether.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred</td>
            <td>0</td>
            <td>1</td>
            <td>Improves the look of RT reflections and is surprisingly more performant than the default settings.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.Glossy</td>
            <td>1</td>
            <td>0</td>
            <td>Disabling this makes objects reflect more, though it looks inaccurate.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SmoothBias</td>
            <td>1</td>
            <td>0</td>
            <td>Disabling this causes reflections to look broken.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve</td>
            <td>1</td>
            <td>0</td>
            <td>Looks much better when standing still, but is very grainy in motion.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve.NumSamples</td>
            <td>32</td>
            <td>32+</td>
            <td>Higher values make RT reflections more stable at the cost of some specular detail.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve.TemporalQuality</td>
            <td>2</td>
            <td>0-2</td>
            <td>Improves stability when standing still, but causes instability in motion, with noticeable grain.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve.TemporalWeight</td>
            <td>0.95</td>
            <td>1</td>
            <td>Higher values reduce shimmering, but sacrifice some detail in the reflections.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ReflectionCaptures</td>
            <td>0</td>
            <td>1</td>
            <td>Captures more objects in reflections but is very expensive performance-wise.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Shadows.EnableTwoSidedGeometry</td>
            <td>1</td>
            <td>0</td>
            <td>Fixes shadows on the sands of the Isle of Alchemists.</td>
        </tr>
        <tr>
            <td>r.RayTracing.AmbientOcclusion.EnableMaterials</td>
            <td>0</td>
            <td>1</td>
            <td>Fixes blocky AO near foliage textures and reduces AO around characters, especially on their hair.</td>
        </tr>
    </tbody>
</table>


# Raytracing!
Currently, the mod allows the usage of raytracing, but ONLY FOR STEAM. For some reason or another, the Gamepass build doesn't respect these settings. I provided my GameUserSettings.ini file within [EnableRT.zip](https://www.nexusmods.com/liesofp/mods/128?tab=files) with the following RT effects toggled on:

<table>
    <thead>
        <tr>
            <th>Setting</th>
            <th>Default</th>
            <th>Modified</th>
            <th>Effect</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>r.Reflections.Denoiser</td>
            <td>2</td>
            <td>0</td>
            <td>When enabled, it reduces the quality of deferred RT reflections and doesn’t resolve motion graininess.</td>
        </tr>
        <tr>
            <td>r.Reflections.Denoiser.ReconstructionSamples</td>
            <td>8</td>
            <td>0</td>
            <td>Setting this to 0 likely disables the denoising step altogether.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred</td>
            <td>0</td>
            <td>1</td>
            <td>Improves the look of RT reflections and is surprisingly more performant than the default settings.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.Glossy</td>
            <td>1</td>
            <td>0</td>
            <td>Disabling this makes objects reflect more, though it looks inaccurate.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SmoothBias</td>
            <td>1</td>
            <td>0</td>
            <td>Disabling this causes reflections to look broken.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve</td>
            <td>1</td>
            <td>0</td>
            <td>Looks much better when standing still, but is very grainy in motion.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve.NumSamples</td>
            <td>32</td>
            <td>32+</td>
            <td>Higher values make RT reflections more stable at the cost of some specular detail.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve.TemporalQuality</td>
            <td>2</td>
            <td>0-2</td>
            <td>Improves stability when standing still, but causes instability in motion, with noticeable grain.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ExperimentalDeferred.SpatialResolve.TemporalWeight</td>
            <td>0.95</td>
            <td>1</td>
            <td>Higher values reduce shimmering, but sacrifice some detail in the reflections.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Reflections.ReflectionCaptures</td>
            <td>0</td>
            <td>1</td>
            <td>Captures more objects in reflections but is very expensive performance-wise.</td>
        </tr>
        <tr>
            <td>r.RayTracing.Shadows.EnableTwoSidedGeometry</td>
            <td>1</td>
            <td>0</td>
            <td>Fixes shadows on the sands of the Isle of Alchemists.</td>
        </tr>
        <tr>
            <td>r.RayTracing.AmbientOcclusion.EnableMaterials</td>
            <td>0</td>
            <td>1</td>
            <td>Fixes blocky AO near foliage textures and reduces AO around characters, especially on their hair.</td>
        </tr>
    </tbody>
</table>



To disable any effect, just set it back to False within GameUserSettings.ini. Check [PCGamingWiki](https://www.pcgamingwiki.com/wiki/Lies_of_P]PCGamingWiki)﻿﻿ for the config file location.