# GODZILLA Minus One — Forge 1.20.1 first-pass port

Generated from `G1_1.21_support_.mcaddon` (Bedrock behavior + resource packs).

## Included
- Forge 1.20.1 / Java 17 project scaffold.
- GeckoLib entity renderer and converted geometry resource files.
- Original PNG textures and available sound assets copied into the mod resources.
- Spawn eggs for Godzilla Minus One, Godzillasaurus, Anti-Gojira Tank, AI Tank, Shinden Plane, underwater mine, tank bullet, parachute, and nuke entity.
- Original Bedrock behavior/scripts/recipes/particle definitions kept in `conversion_reference/` for porting.

## Important limitations
This is a **first-pass port project**, not a tested/finished equivalent of the Bedrock add-on. The Bedrock models use Bedrock geometry and some animation expressions that may require adjustments for GeckoLib. Behavior-pack JSON and `@minecraft/server` JavaScript cannot run in Forge, so AI, vehicle controls, the plane camera/gun, nuke effects, custom particles, and many attacks still need native Java implementations. Several entities are currently generic mobs with placeholder AI. The copied sounds/particles are reference assets; their event definitions are not all wired to Forge.

## Build
Install JDK 17 and import this folder into IntelliJ IDEA as a Gradle project. Let Gradle resolve dependencies and run `build`. Dependencies: Minecraft Forge 1.20.1 (47.2.0), GeckoLib Forge 1.20.1 (4.4.9).

## Testing checklist
1. Build successfully with Gradle.
2. Launch client with Forge + GeckoLib installed.
3. Test each spawn egg in a new creative world.
4. Check model scale/orientation and textures. Some very large Bedrock bone hierarchies may need pivots/rotation conversions.
5. Port behavior one feature at a time, then add recipes, sounds, projectiles, particles, and vehicle controls.

## Conversion notes
See `conversion_reference/bedrock/` for the original behavior definitions, scripts, recipes and particles. Original asset authorship remains credited to Monster122.

## Build on GitHub Actions

This repository includes `.github/workflows/build.yml`. Upload/push this project to a GitHub repository, open **Actions**, select **Build Forge 1.20.1 mod**, and choose **Run workflow** (or push to `main`/`master`). If the build succeeds, open that workflow run and download the `g1-forge-1.20.1-mod` artifact. The artifact contains the built JAR from `build/libs/`.

**Important:** the workflow builds the current first-pass project; a successful build does not mean all Bedrock gameplay mechanics have been ported or tested in-game. The build has not been run in this environment because Gradle is not installed and outbound network access is unavailable here.
