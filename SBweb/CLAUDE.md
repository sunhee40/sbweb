# Website Update Workflow

A user provides a reference image (screenshot), some CSS classes or style notes, and an existing folder in VS Code that contains various HTML, CSS and JS files used to build an existing website.

The goal is to update the existing website using the CSS style provided by the user and match the style of the reference image. Instead of updating the existing CSS and style, Claude should copy the old files including HTML, CSS and others into a new folder and update them.

## Steps

1. Apply the style code provided by the user to the existing HTML. The output HTML files should be generated in the current folder. Apply the style to individual sections of HTML as well.

2. **Compare** your screenshot against the reference image. Check for mismatches in:
   - Spacing and padding (measure in px)
   - Font sizes, weights, and line heights
   - Color (exact hex values)
   - Alignment and positioning
   - Border radii, shadows, and effects
   - Responsive behavior
   - Image/icon sizing and replacement

3. **Fix** every mismatch found — edit the HTML/Tailwind code.

4. **Re-screenshot** and compare again.

5. **Repeat** steps 2–4 until the result is within 2–3px of the reference everywhere.

Do not stop after one pass. Always do at least 2 comparison rounds. Only stop when the user says so or when no visible differences remain.

## Technical Defaults

- Use Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Maintain the folder structure in the current folder exactly the same as the folder where the old files are
- Use placeholder images from `https://placehold.co/` when source images aren't provided
- Mobile-first responsive design

## Rules

- Match the reference exactly — do not "improve" the design
- If the user provides CSS classes or style tokens, use them verbatim
- Keep code clean but don't over-abstract — inline Tailwind classes are fine
- When comparing screenshots, be specific about what's wrong (e.g., "heading is 32px but reference shows ~24px", "gap between cards is 16px but should be 24px")
