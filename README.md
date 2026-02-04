# Elemental Interfaces

A 3D interactive periodic table that transforms between different spatial layouts. Click between table, sphere, helix, and grid views to see all 118 elements reorganize themselves in real time.

## What it does

The project takes the familiar periodic table and lets you explore it as a spatial object. Each element is a card that knows its position in multiple coordinate systems. Switch layouts and watch the cards animate smoothly between arrangements, preserving their chemical data while completely changing how you navigate through them.

Individual elements expand on click to show detailed properties like atomic mass, density, and melting points. The whole scene responds to mouse movement with subtle parallax rotation.

## Technical approach

The core mechanic uses CSS3D transforms rather than WebGL. Each element card lives in 3D space with perspective calculations borrowed from three.js examples but implemented purely in CSS. This keeps the DOM interactive while still achieving smooth spatial transitions.

Layout transformations use anime.js v4 for the animation engine. The sphere layout distributes elements using spherical coordinates, the helix wraps them around a cylinder with vertical spacing, and the grid stacks them in cubic layers. Switching between these recalculates all positions and animates with staggered delays.

The color coding follows standard periodic table categories (noble gases, alkali metals, transition metals, etc). All element data is stored in a flat array with stride indexing for performance.

## Running it

Clone the repo and open `index.html` in a browser. The project uses ES modules from a CDN so no build step required.

```bash
git clone https://github.com/yourusername/elemental-interfaces.git
cd elemental-interfaces
# open index.html in your browser
```

For development with live reload you can use any static server:

```bash
python -m http.server 8000
# or
npx serve
```

## File structure

- `index.html` - DOM structure and element template
- `src/javascript/sketch.js` - Animation logic and layout calculations  
- `src/styles/style.css` - 3D transforms and visual styling
- Element data is hardcoded in the JS with all chemical properties

## Credits

3D transform calculations adapted from the three.js CSS3D periodic table demo. Color scheme and interaction patterns developed independently.

## License

MIT