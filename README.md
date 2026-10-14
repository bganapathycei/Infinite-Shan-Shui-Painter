[readme.md](https://github.com/user-attachments/files/33449424/readme.md)
# Infinite Shan Shui Landscape Painter

An interactive, procedural generative art web application that acts as an autonomous landscape artist, continuously painting an infinite classical Chinese *Shan Shui* (山水) handscroll in real time using multi-bristle ink brush techniques on textured antique silk paper.

## Overview

The engine draws from left to right across the canvas. Once the painter reaches the right edge of the screen, the viewport smoothly transitions into an infinite leftward scroll while the painter continues composing new geological massifs, mountain passes, rivers, and architectural compounds indefinitely on the advancing right edge.

The aesthetic pays homage to classical Southern Song and Yuan Dynasty masters (notably Huang Gongwang's *Dwelling in the Fuchun Mountains* and the Dong-Ju tradition), translating traditional ink brushwork rules into a high-performance procedural rendering system.

## Key Features

### 1. Lead-Offset Painter's Algorithm
To ensure authentic layering and prevent background washes from occluding foreground elements, the engine advances world coordinates using a staggered back-to-front depth queue:
* **Horizon Layer (+560px lead)**: Distant soft-wash mountain ranges, sweeping clouds, and soaring cranes.
* **Primary Massifs (+380px lead)**: Towering multi-lobed peaks, internal ridge spines, and cascading hemp-fiber contours (*Pima Cun*).
* **Foothill Terraces (+200px lead)**: Rolling lower ridges, valley conifer groves, and hillside architecture.
* **Watercourses (+50px lead)**: Lake currents, horizontal waterlines, and curled spiral eddy swirls.
* **Foreground (+0px)**: Earthen shoreline spits, rounded alum-head boulders (*Fantou*), gnarled pine groves, and waterside dwellings.

### 2. Geological Mountain Massifs & *Pima Cun* (披麻皴)
* **Broad Base Aspect Ratio**: Mountain massifs feature a realistic 3:1 to 4:1 width-to-height ratio (680px–1,020px base width) with concave bell-curve skirts that flare gently into the valley floor rather than forming narrow vertical pillars.
* **3D Structural Ridge Spines**: Branching diagonal structural spines descend at 30°–50° angles from the summit, dividing the mountain into distinct sunlit and shaded facets.
* **Diagonal Hemp-Fiber Strokes**: Nested contour strokes follow the slope of each flank, terminating at staggered elevations to dissolve seamlessly into valley mist with no hard horizontal edges.
* **Summit Moss Dots (*Taidian* / 苔点)**: Organic clusters of fine vertical ink ticks and foliage dabs crowning the summit domes and ridge shoulders.

### 3. Five Distinct Architectural Styles
Architectural compounds are procedurally chosen and nestled into flat foothill terraces, river coves, and rocky spits:

| Architectural Style | Key Visual Characteristics | Typical Setting |
| :--- | :--- | :--- |
| **Two-Tiered Pavilion (飞檐楼阁)** | Sweeping upturned eaves (*feiyan*), terracotta tile wash, crimson pillars, and balustrade railings | Elevated foothill terraces |
| **Alpine Timber Chalet (高山木屋)** | Steep A-frame timber roof, log weatherboarding, stone chimney, and warm glowing windows | Mountain saddles and passes |
| **Riverside Stilt Dwelling (水榭吊脚楼)** | Cross-braced wooden pilings over water, open viewing veranda, and a moored wooden sampan boat | Riverbanks and shoreline promontories |
| **Thatched Watermill Cottage (水车茅舍)** | Rounded organic thatch roof with eyebrow dormer, fieldstone walls, and a timber waterwheel | Stream edges and valley floors |
| **Stone Watchtower Compound (古石堡关隘)** | Tapered stone bastion, crenellated battlements, arched gateway, and fluttering crimson banner | High rocky promontories |

### 4. Living Water & Curled Eddy Swirls
* **Curling Eddies**: Logarithmic spiral swirls compressed vertically for perspective, simulating natural whirlpools and turbulent river currents.
* **Foam Highlights**: Titanium white gouache dry-brush strokes along curling crests and boulder skirts.
* **Water Currents**: Long, undulating S-curved waterlines woven with faint mountain reflections.

### 5. Multi-Bristle Brush Engine
* **Pressure Envelopes**: Strokes organically swell from fine entry points to wide expressive mid-sections, tapering cleanly at the tail.
* **Dry-Brush Splitting (*Fei Bai* / 飞白)**: Fast strokes cause individual bristle filaments to skip across the textured paper tooth.
* **Wet-on-Wet Diffusion**: Wide strokes lay down an underlying low-opacity wash halo that feathers into the paper fibers.

### 6. Infinite Double-Buffered Chunk System
* Canvas data is partitioned into dynamic 1024px offscreen chunks.
* Avoids repetitive canvas copy/blit degradation, preventing pixel drift and blurring over extended runtimes.
* Runs at a steady 60 FPS on Retina and standard displays with automatic DPI scaling.

## Project Structure

```
├── authentic_painter_landscape.html  # Complete, self-contained web application
└── README.md                         # Project documentation and architectural overview
```

## Getting Started

### Prerequisites
A modern web browser supporting HTML5 Canvas (Google Chrome, Mozilla Firefox, Apple Safari, or Microsoft Edge). No external dependencies, CDNs, package managers, or local web servers are required.

### Installation & Launch
1. Clone or download the repository to your local machine:
   ```bash
   git clone https://github.com/your-username/infinite-shan-shui-painter.git
   cd infinite-shan-shui-painter
   ```
2. Open `authentic_painter_landscape.html` directly in your browser:
   * **macOS / Linux**: Double-click the file, or open via terminal:
     ```bash
     open authentic_painter_landscape.html   # macOS
     xdg-open authentic_painter_landscape.html # Linux
     ```
   * **Windows**: Double-click `authentic_painter_landscape.html` in File Explorer.

## Interactive Controls

The floating control HUD at the bottom of the screen provides real-time controls:
* **Pause / Resume**: Toggles the autonomous painter between active sketching and inspection pause.
* **Fresh Canvas**: Clears all active chunks, generates a fresh aged-silk paper background, and restarts the drawing from the left edge.
* **Paint Speed (0.5x – 4.0x)**: Adjusts the horizontal drafting speed of the artist.
* **Pigment Richness (0.6x – 1.5x)**: Dynamically scales ink opacity and gouache saturation across all active and newly drawn strokes.

## Color Palette Reference

All pigments are defined as RGB vectors modulated by opacity and paper absorption:

| Pigment Name | Representation | Visual Role |
| :--- | :--- | :--- |
| **Sumi Lampblack** | `rgba(26, 22, 18, α)` | Calligraphic outlines, tree trunks, and deep crevice folds |
| **Walnut / Umber** | `rgba(62, 54, 45, α)` | Hemp-fiber contour lines (*Pima Cun*) and building frames |
| **Raw Sienna / Ochre** | `rgba(162, 120, 72, α)` | Mountain flank under-washes, sandbanks, and thatch roofs |
| **Venetian Red** | `rgba(152, 74, 50, α)` | Temple pavilions, banners, and autumn foliage dabs |
| **Indigo / Slate Blue** | `rgba(86, 98, 106, α)` | Distant horizon mountain washes and shadowed crevices |
| **Celadon / Jade** | `rgba(76, 100, 78, α)` | Pine needle clouds, riverside willows, and valley moss |
| **Titanium White** | `rgba(250, 245, 235, α)` | Drifting clouds, water foam crests, and sunlit rock highlights |
| **Gold Leaf** | `rgba(212, 165, 76, α)` | Interior window illumination and pagoda roof finials |

## License

No License. Anyone can use it.
