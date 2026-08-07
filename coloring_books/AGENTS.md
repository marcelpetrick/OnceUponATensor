# Coloring Book Workflow

This directory contains printable children's coloring-book sets. When the user supplies a topic, complete the set autonomously unless a missing requirement would make the result unsafe or unusable.

## Defaults

- Create five distinct coloring pages for each requested topic.
- Use the image-generation skill and its built-in image tool, with one generation call per page.
- Infer a sensible target age from the request or topic when no age is supplied. Use simpler, larger shapes for younger children and progressively richer scenes for older children.
- Use portrait A4 unless landscape clearly suits the topic better. Keep one orientation throughout a set.
- Deliver every page as a PNG and also deliver one combined PDF for the set.
- Put each set in a clearly named, lowercase `snake_case` directory.
- Use numbered, descriptive filenames such as `01-forest-path.png`.

## Artwork Requirements

- Pure black outlines on a pure white background; children must be able to color all major areas.
- No color, gray, shading, gradients, hatching, halftones, textures, borders, captions, or watermarks.
- Prefer smooth, closed outlines, generous print-safe margins, clear silhouettes, and large colorable regions.
- Allow solid black only where visually necessary, such as small pupils.
- Make all five compositions meaningfully different while keeping subject treatment and line weight consistent.
- Keep every important subject fully on the page. Avoid cropped faces, limbs, wings, wheels, tails, or other defining features.

## Print Preparation

1. Generate and visually inspect all five pages before finalizing them.
2. Normalize portrait pages to exactly 2480 x 3508 pixels or landscape pages to exactly 3508 x 2480 pixels.
3. Store 300 DPI resolution metadata.
4. Convert final PNGs to bilevel black and white, preserving clean outlines. ImageMagick with grayscale plus a carefully checked threshold is acceptable.
5. Verify every PNG's pixel dimensions and confirm it contains exactly two colors.
6. Combine the ordered PNGs into a single five-page A4 PDF using a lossless tool such as `img2pdf`.
7. Verify the PDF with `pdfinfo`: five pages and A4 page size.

## Quality Review

- Review a contact sheet and at least one full-resolution page from each set.
- Regenerate any page that is illegible, repetitive, visibly cropped, too dense for the intended age, or inconsistent with the requested subject.
- Remove temporary review files before committing.

## Git Handoff

- Add only the files created for the requested coloring-book work; preserve unrelated user changes.
- Commit the PNGs, combined PDF, and any requested workflow documentation together in one local commit.
- If the user asks to amend the current local commit, amend it rather than creating another commit.
- Report the output directory, PDF path, print specifications, validation result, and commit hash.
