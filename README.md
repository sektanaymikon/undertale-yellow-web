# Undertale Yellow: Shades of Justice — browser compatibility repair

This is the existing Shades of Justice browser edition, not an original conversion of the unmodified Undertale Yellow release. The original in-game credits remain intact. See CREDITS.txt for the source and contributors.

## Snowdin repair

The converted molten-rock object had lost its empty collision-event registrations for the ramps and pistons. The three relevant object types now share a positive physics collision group. The rock and piston fixture coordinates also match the desktop edition, restoring the visible alignment of their contacts. No story flags, solved-puzzle flags, or puzzle bypasses are included.

The patch is limited to the OBJT fields recorded in snowdin-patch.json. The rest of game.unx is unchanged. The standalone browser runtime is unchanged.

## Validation

- Reproduced the original failure: the rock fell straight through the first ramp and disappeared.
- Tested the earlier plank/rock Snowdin puzzle without modifying it; collision and respawn worked.
- Tested the repaired piston puzzle through its normal lever and arrow-key controls, using local test instrumentation to position the player and record the trajectory.
- Both puzzle phases completed: the rock crossed the ramps and pistons, melted the ice, filled the water meter, and opened the gate. No solved-state injection was used.
- Tested the packaged download, per-part SHA-256 validation, gzip decompression, runtime boot, keyboard input, and fullscreen wrapper.

This is a targeted compatibility repair, not a complete-game playthrough certification. The upstream build logs three shader compilation errors during startup; those pre-existing shader issues are outside this patch.

## Hosting and CodeHS

The main branch contains the HTML launcher, runtime, font/license, and pinned manifest. The five assets branches hold compressed game chunks, keeping each CDN package below 50 MB. Manifest URLs pin exact commits. Uploading only the main branch to another host will still fetch its pinned external game chunks.

Use the supplied small Undertale-Yellow-CodeHS-index.txt as CodeHS index.html. It loads the launcher directly into the CodeHS page. The first game download is approximately 186 MB, hosted externally. Saves use the browser runner's existing local save storage and stay tied to the page's origin.

The bottom-right port credit remains inside the fullscreen wrapper, at 50% opacity, with pointer input disabled. Original game-author credits are preserved.
