# Runway adapter

The [Gen-4 image-to-video guide](https://help.runwayml.com/hc/en-us/articles/39789879462419-Gen-4-Video-Prompting-Guide) recommends a strong first frame and positive motion descriptions. The image supplies appearance; prose should emphasize subject, environment and camera motion.

Avoid a negative-prompt block. Express the desired stable background positively. Use a single scene. The retrieved guide describes 5/10-second clips, as of 2026-10-25; check the active endpoint.

Use example 5 in `examples.md`. Review paper texture and head/wing continuity. A return-to-start instruction does not prove a clean loop. Trim and inspect the boundary separately.
