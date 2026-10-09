---
id: first-mask
title: Make your first mask
sidebar_position: 2
---

# Make your first mask

**After reading this page, you will know** the full flow from choosing a model, making a mask, and outputting it to plugging it into a shader.

## Four steps

1. In the Hierarchy, select the model and press **Use current selection**.
2. In the right panel, choose the material and the mask to edit. You can search by name or shader property.
3. Press **Paint** and paint on the model in Scene view. You can also use **Image · Gradient · Bridge · MatCap Gloss**.
4. Check the result with **Applied result**, then output the mask from **Save and apply**.

White is 1 and black is 0. The effect of each value depends on the shader feature it is connected to.

<!-- SCREENSHOT: Painting in Scene view with the open mask list on the right -->

## Window layout

| Area | Contents |
|---|---|
| Wide window | Canvas and tools on the left; material selection, layer list and open masks on the right |
| Narrow window | Material selection, open masks and the canvas, stacked from top to bottom |
| Open masks | Switch the mask you are working on, and expand a material group to open another mask |
| Show empty slots | On by default, so disabled effects and empty masks are easy to find |
| Guided | Focuses on the selected mask's effect settings and Scene view work |
| Expert | Detailed control over layers, mesh, output and tools |
| Recent | Find saved files in the Project window or open their folders |

Switching modes keeps your work.

## Change the view

Choose one of **Mask only · Applied result · Original**.

- **Mask only** and **Applied result** start Scene editing.
- **Original** ends Scene editing. Mask work is kept while you are in Original view.
- When you explicitly open a mask from **Applied result**, a related effect that was off is turned on and the applied result is shown. Looking at or searching the list alone does not change any effect.
- The preview of a mask with nothing painted yet is black (black is 0), with one line: "Nothing painted yet."

## Edit several masks

You can move between the masks on one material and paint on each. If you paint a shadow mask, edit an outline mask and come back, each mask keeps its drawing and layers. Packed masks that use the R/G/B/A channels keep separate work for each channel. If you change the channel in the Inspector, your painted work moves to the new channel with it. If the new channel already has work, Mask Maker asks **Move** / **Just follow**. Nothing is deleted. → [Channels and packing](/concepts/channels-and-packing#channel-change)

## Output and plug into a shader

1. Open **Save and apply → Mask Output**.
2. Set the output size and the **Outline (px)** value.
3. Save. A grayscale mask is imported with sRGB turned off. If the material uses lilToon, Poiyomi, MingToon, or NiloToon, it is connected to the selected material property. Other shaders get a PNG that you plug in yourself.

The default file name separates the material, the mask property and the selected channel. Check the save path before overwriting a file. An editable layer document is saved next to the output.

For shader slot names and inspector paths, see → [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)

## Which method should you start with?

| What you want | Method |
|---|---|
| Draw the area yourself | [Paint](/tabs/paint) |
| Use a picture you already have as a mask | [Image](/tabs/image) |
| An effect that gets weaker or stronger with position | [Gradient](/tabs/gradient) |
| An effect on only a few strands of hair | [Bridge](/tabs/bridge-mask) |
| The position of gloss and highlights | [MatCap Gloss](/tabs/matcap-gloss) |
| Combine several methods into one mask | [Layers and mask output](/concepts/layer-stack) |
| Pack several masks into one texture | [Mask Combiner](/tabs/combiner) (Expert tools) |

## Next

→ [What is a mask texture](/concepts/what-is-a-mask) · [sRGB and import settings](/concepts/srgb-and-import-settings)
