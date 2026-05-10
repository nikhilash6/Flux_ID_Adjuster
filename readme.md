FLUX Identity Adjuster

The node has been created through vibe coding. The main objective is for identity consistency for FLUX.2 klein 9b models in ComfyUI.






The default values are fixed for the best result but i have only tested it for a limited samples so look for your own settings.





Parameter	Default	Description \& Visual Impact				

layout\_blocks	3-7	D-Blocks. Establishes global layout and integrates the subject into the background safely. Anchors run at 25% strength here to actively prevent multi-head (Janus) artifacts.				

identity\_blocks	8-19	S-Blocks. Synthesizes high-frequency identity, facial micro-geometry, and photorealism. Hard snapping runs at full 100% strength here.				

saliency\_scan\_blocks	6-23	The specific blocks where the script mathematically scans the canvas to dynamically isolate the face from the background during Step 1.				

photorealistic\_smoothing	TRUE	ON: Applies an FFT filter to delete high-frequency static for photorealistic skin.OFF: Transfers raw reference textures (preserves brushstrokes, film grain, or 2D art styles).				

total\_sampling\_steps	4	CRITICAL: Must match your KSampler steps! Syncs the internal curve to ensure style and geometry inject at the exact correct anatomical phases.				

boost\_fade\_curve	Ease-In	Controls how the identity injection fades out over time. Ease-In is highly recommended to protect late-stage text styling (like watercolors or lighting).				

identity\_strength	1.5	Primary multiplier for facial likeness. Higher values force a stronger resemblance but may stiffen the subject's pose.				

background\_text\_strength	0.6	Amplifies your text prompt to construct the background and apply style. Automatically muted during delicate anatomy phases to protect fingers.				

dynamic\_text\_balancing	TRUE	Automatically throttles text strength when the face is struggling to form, preventing complex text prompts from crushing the facial identity.				

target\_likeness\_metric	0.35	The raw cosine goal. 0.35 is mathematically ideal for Flux. Pushing higher forces aggressive pulling; lower allows more stylistic freedom.				

soft\_blend\_k	1	Averages the top K matches for smooth skin. Committed anchors (eyes/lips) ignore this and snap exactly to K=1 for maximum sharpness.				

face\_isolation\_strictness	1	Top % of tokens to lock as the "Face". Set to 1.0 to pull the full body/background. Lower values (e.g., 0.35) isolate just the face for hybrid generations.				

confidence\_gate	0.15	Minimum confidence required to soft-pull a token. Higher values prevent visual artifacts but might freeze the render. 0.0 disables the safety gate.				

hard\_anchor\_margin	0.06	The margin of certainty required to permanently lock a token (like a pupil). Lower means anchors lock faster; higher requires absolute certainty.				

contrast\_and\_texture\_floor	0.18	Base similarity cutoff. Increasing this boosts visual contrast and removes noise, but pushing too high creates waxy, over-smoothed skin.				

subject\_mask (Optional)	None	Connect a mask here to restrict the Saliency Radar to only consider reference tokens inside the drawn area.				







Important to match your till always remember to Match your sampling steps to the KSampler steps to ensure proper anatomy.
For photorealism keep the "photorealistic\_smoothing" turned on, and lower the  "contrast\_and\_texture\_floor" slightly around 0.18 - 0.20, which will add more natural noise.
For anything artistic keep the "photorealistic\_smoothing" turned off, use "Ease-In" curve and bump "background\_text\_strength" up slightly. for more contrast increase the "contrast\_and\_texture\_floor" slightly around 0.30+ but it will result in waxy skin.




This project uses the PolyForm Noncommercial License 1.0.0. The short version is: you are completely free to use this tool, as long as you aren't using it to make money.

✅ What you CAN do for free: * Use it for your personal art, hobbies, school projects, academic research, or charity work.

Tinker with the code, modify the node, build on top of it, and share your tweaks with the community (as long as those are also free).

❌ What you CANNOT do (without permission): * Use this node inside a paid AI generation service, a commercial cloud product, a Patreon-gated workflow, or any business where it helps generate revenue.

Looking to use this for business?
If you are a company or developer wanting to integrate this into a commercial product or paid service, we can set that up! Just open an issue on this GitHub repository or reach out via the contact info on my GitHub profile to arrange a separate commercial license.