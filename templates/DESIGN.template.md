# Design Language & Constraints (DESIGN.md)

## 1. Vision & Brand: [e.g., "Industrial Technical"]
**Product Name:** [Name]
**Tagline:** [Tagline]
**Tone:** [e.g., Mechanical, technical, monochromatic, precise]
**Philosophy:** [e.g., Industrial warmth. The interface is a piece of hardware. Structure is the ornament.]

## 2. Visual Language

### 2.1 Color Palette
- **Background:** [Hex]
- **Surface:** [Hex]
- **Borders:** [Hex]
- **Primary Text:** [Hex]
- **Secondary Text:** [Hex]
- **Status Indicators:**
  - **Success:** [Hex]
  - **Warning:** [Hex]

### 2.2 Typography
- **Display:** [Font Family]
- **Body:** [Font Family]
- **Metadata:** [Font Family]

### 2.3 Visual Hierarchy
- **Primary:** The core data.
- **Secondary:** Supporting context.
- **Tertiary:** Metadata/Systems.

## 3. UI Components & Patterns
- [Describe the aesthetic of modules/cards]
- [Describe input patterns]

## 4. Mobile Interaction Model
- **Bottom-Heavy UI:** Primary actions in the bottom 1/3 "thumb zone".
- **Tactile Mandates:** [e.g., Mechanical honesty. Haptics mandatory.]

## 5. Implementation Standard
- [e.g., Use shadcn/ui primitives stripped to their typographic essence]
- **Zero-Latency Mandate:** UI must be interactive within 100ms.
- **Performance Yield:** Chunked processing for all local data operations.
