# Reclaimed: an overgrown ruins tour

Reclaimed is the editable showcase at `/VineGenerator/Example/Maps/VineGeneratorAuthoringShowcase`. Its nine camera stations introduce the same growth, foliage and art-direction features available on your own vines. The courtyard combines weathered masonry, detailed ground surfaces and understory planting; the modeled-species examples use the reusable photographic foliage materials included with their presets.

The Windows player build targets DirectX 12 and Shader Model 6. Other platforms and graphics configurations have not been validated for this demo.

## Open the tour in Unreal Editor

1. Enable **Vine Generator** and restart if prompted. Enable **Show Plugin Content** in the Content Browser settings.
2. Open **VineGeneratorAuthoringShowcase** under **VineGenerator > Example > Maps**.
3. Press **Play**, using Selected Viewport or New Editor Window. The map already selects **Vine Generator Demo GameMode**; no project input mappings are needed.
4. Press **Tab** to visit the next station, or click its navigation buttons. Use **Home** to recover the station's original camera view after exploring.

Use **F1** for the menu during Play In Editor: Unreal may reserve Escape for stopping play. The menu's Quit action directs you to the editor's Stop button. In a packaged demo, Escape opens the menu and Quit exits the application.

When preparing this tour in your own project, select a vine or spawner and open **Performance > Runtime Setup**. Click **Enable Full Lightmap Precaching**, restart the editor, and use **Check Runtime Setup** to inspect the active policy. This saves a project-wide setting that prepares additional material pipelines before runtime vines appear; it can increase initial preparation work and does not alter lighting. For a read-only configuration, check out `Config/DefaultEngine.ini` or use **Copy Setting** and add `r.PSOPrecache.LightMapPolicyMode=0` under its existing `[/Script/Engine.RendererSettings]` section. Profile a packaged first-use tour on the target hardware; the setup check is not a performance test. See [runtime setup](https://funbydefault.github.io/vine-generator-docs/DOCUMENTATION.html#runtime-and-performance) for the complete configuration snippet.

## The nine stations

| Station | What to try |
| --- | --- |
| 1. Reclaimed | Explore the courtyard and inspect its climbing and hanging plants. |
| 2. Living growth | Regrow the specimen with the same seed, then compare a new variation. |
| 3. Directed by the artist | Toggle the assigned spline and attractor guides to compare their influence. |
| 4. Room to breathe | Toggle the window's exclusion box and compare how the stems occupy the opening. |
| 5. Shape the silhouette | Toggle a saved pruning cut and its untrimmed result. |
| 6. Five species. Four seasons. | Compare Ivy, Heart Leaf, Lance Leaf, Monstera and Virginia Creeper; cycle their seasonal colors. |
| 7. Bring your own foliage | Inspect prepared custom leaf geometry and materials, including seasonal tint. |
| 8. Movement in the ruins | Toggle prepared free-span motion and apply an impulse to the unsupported stems. |
| 9. Ready for production | Inspect a saved Static Mesh population batch with three LODs. |

Actions affect only the specimens assigned to the current station. The overview and production stations are for observation. At the foliage stations, changing season preserves the species, seed, leaf size and spacing. Wait for growth and mesh work to finish before another action; the HUD reports when a specimen is busy or a control cannot run.

## Keyboard and mouse

| Control | Action |
| --- | --- |
| WASD | Move the inspection camera |
| Q / E | Move down / up |
| Hold right mouse button | Look around; release it to use the HUD pointer |
| Left Shift | Move faster |
| Tab / Shift+Tab | Next / previous station |
| 1–9 | Go directly to a station |
| Home | Reset the current station's view |
| H | Hide or show the HUD |
| Escape / F1 | Open or close the menu |
| R / N | Regrow with the same seed / select a new seed and regrow |
| G / X / P | Toggle guides / exclusions / pruning at the relevant station |
| C | Cycle seasonal colors at a foliage station |
| V / F | Toggle free-span dynamics / apply an impulse at the dynamics station |

The HUD also has clickable navigation and action buttons. The camera flies freely through the scene without collision.

## Gamepad

Button names below use Xbox-style labels. The HUD switches prompts when you use a controller. Physical controller testing remains pending.

| Control | Action |
| --- | --- |
| Left / right stick | Move / look |
| LT / RT | Move down / up |
| Left stick click | Move faster |
| LB / RB | Previous / next station |
| Y | Reset the current view |
| A / X | Regrow / choose a new seed |
| D-pad Up | Run the station's feature action |
| D-pad Right | Apply a dynamics impulse |
| D-pad Down / Left | Regrow / choose a new seed |
| Start or B | Open or close the menu |
| View | Hide or show the HUD |

In the menu, use D-pad Up/Down to select **Resume exploring**, **Return to station view** or **Leave demo**, press A to activate, or B to resume.

## Windows touchscreen

Tap once to reveal the larger touch controls. This first tap only changes the layout; it does not move the camera or activate a button. Physical touchscreen acceptance remains pending. These mappings describe touchscreen input in the Windows demo.

| Control | Action |
| --- | --- |
| Drag and hold on the left half, outside HUD buttons and the field-notes panel | Move relative to the camera; release to stop |
| Drag on the right half, outside HUD controls | Look around; use both thumbs to move and look together |
| Hold: Rise / Hold: Lower | Move up / down while held |
| Fast: Off / Fast: On | Toggle three-times flight speed |
| < / > in the field notes | Previous / next station |
| Reset view | Restore the current station's camera |
| Regrow / New seed | Regrow the same variation / choose a new seed and regrow |
| The station's feature button | Toggle guides, exclusions, pruning or motion, or cycle the seasonal palette at the relevant station |
| Push at the dynamics station | Apply an impulse to the active hanging stems |
| Hide UI | Hide the controls; tap anywhere to restore them |
| Menu | Pause and show Resume exploring, Return to station view and Leave demo |

Tap buttons by releasing inside the same button. Sliding off cancels the action, even if you slide back before lifting your finger. Sliding off **Hold: Rise** or **Hold: Lower** stops the height movement. Field-note text does not steer the camera. The overview and production stations show navigation controls without live plant actions.

Opening the menu, resetting or changing stations, hiding the HUD, losing focus or switching to mouse/keyboard/gamepad input clears held touch controls and Fast mode. Restoring a hidden HUD consumes the first tap, so the controls return without moving the camera or triggering an action. Play In Editor keeps the same Quit behavior described above.

## Continue authoring

Play-session changes are temporary. Stop play to edit the saved actors, guides and pruning markers, then save your level to retain editor changes. **Home** and the menu's **Return to station view** restore only the camera; restart the play session to return all specimens to their saved state. Choosing a new seed clears existing pruning rules.

The production display was built with the Spawner Volume's real editor batching workflow. It retains editable source vines and three LODs with Nanite disabled. To inspect the LODs, open its `SM_ProductionBatch_` asset under **VineGenerator > Example > Reclaimed > Fidelity > Meshes**. In the editor, select the Spawner Volume and use **Restore Individual Vines** to work on its retained sources. Duplicate the example map before changing the supplied composition.

The runtime tour demonstrates growth, seasonal changes and motion. Its moving unsupported stems intentionally remain bare. Creating Static Mesh assets, generating LODs, preparing custom leaf assets and restoring population sources are editor operations. Static Mesh batches do not grow or simulate free spans. See [the main guide](https://funbydefault.github.io/vine-generator-docs/DOCUMENTATION.html#export-a-finished-vine) for export, LOD and Nanite setup, and [custom leaf preparation](https://funbydefault.github.io/vine-generator-docs/DOCUMENTATION.html#use-your-own-leaf-mesh) to use your own art.
