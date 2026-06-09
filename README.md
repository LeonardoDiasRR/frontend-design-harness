# Frontend Design Harness — Setup Guide

This guide describes how to assemble a **frontend design harness** for AI-assisted UI/UX development, composed of animation libraries, design intelligence skills, and component MCP servers that together enable rapid, polished frontend creation.

The harness is **agent-agnostic**: every library, skill, and MCP server works with any AI coding environment — Claude Code, Codex, Cursor, OpenCode, Windsurf, Cline, Copilot, and others.

---

## Prerequisites

- An AI coding environment (CLI assistants, editor integrations, or agent-based coding tools)
- [Node.js](https://nodejs.org/) (Latest LTS recommended)
- npm or bun
- Git

---

## 1. Project Setup

### 1.1 Initialize a React + TypeScript project

```bash
# Using Vite (recommended)
npm create vite@latest my-app -- --template react-ts
cd my-app
```

### 1.2 Install core dependencies

```bash
npm install motion react react-dom
npm install -D tailwindcss @tailwindcss/vite
```

---

## 2. Animation — Motion (formerly Framer Motion)

**Type:** Animation library (React / JavaScript / Vue)  
**Repository:** https://github.com/framer/motion  
**Documentation:** https://motion.dev/docs/react-quick-start  
**Install:** `npm install motion`

Motion is a production-ready animation library for React with a hybrid engine that combines JavaScript power with native browser APIs for GPU-accelerated, 120fps animations.

### Key capabilities

| Feature | Description |
|---------|-------------|
| `motion.div` | Animate any HTML/SVG element with the `motion` component prefix |
| Gestures | Hover, tap, drag, pan — built-in gesture handlers |
| Layout animations | Animate layout changes automatically with `layout` prop |
| Scroll-linked | `useScroll`, `useInView` for scroll-triggered animations |
| Springs & tweens | Declarative spring physics or duration-based easing |
| Variants | Orchestrate child animations from parent containers |
| AnimatePresence | Animate enter/exit transitions for mount/unmount |
| LayoutGroup | Coordinate layout animations across sibling components |

### Quick start

```tsx
import { motion, AnimatePresence } from "motion/react"

function FadeIn({ children }) {
  return (
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      exit={{ opacity: 0, y: -20 }}
      transition={{ duration: 0.3 }}
    >
      {children}
    </motion.div>
  )
}
```

### Typical usage in AI workflows

Describe the animation you want and the agent uses Motion to implement it:

```
"Add a staggered fade-in animation to this list of cards"
"Create a smooth page transition between routes"
"Build a draggable modal with spring physics"
```

> Motion was previously known as **Framer Motion**. The package was renamed to `motion` in v12. The React API is imported from `"motion/react"`.

---

## 3. Design Intelligence — UI/UX Pro Max Skill

**Type:** AI Skill  
**Repository:** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill  
**Website:** https://uupm.cc  
**CLI:** `npx uipro-cli`

An AI skill that provides **design intelligence** for building professional UI/UX across multiple platforms. It contains 161 reasoning rules and 67 UI style definitions that guide the AI agent to generate polished, production-ready interfaces with strong visual hierarchy and refined user experience decisions.

### Key capabilities

| Feature | Description |
|---------|-------------|
| Design System Generator | Analyzes project requirements and generates a complete, tailored design system (v2.0 flagship) |
| Color palette generation | AI-recommended primary, secondary, CTA, background, and text colors |
| Typography pairing | Suggests font combinations (e.g., Cormorant Garamond + Montserrat) |
| Layout patterns | Hero-centric, SaaS dashboard, e-commerce, mobile-first |
| Accessibility | Automatically targets WCAG AA compliance |
| Anti-pattern avoidance | Flags neon colors, harsh animations, AI-purple gradients |

### Installation

```bash
# In Claude Code, Codex, or other skill-compatible environments:
/plugin install @nextlevelbuilder/ui-ux-pro-max-skill
```

Or reference the skill repository directly in your environment's instructions.

### Typical usage

Describe the interface you want, and the skill guides the agent through design decisions:

```
"Create a landing page for a luxury wellness spa — warm, premium feel"
"Build a SaaS dashboard with dark mode and data visualizations"
"Design a mobile-first e-commerce product page"
```

### Example output (Design System Generator)

```
TARGET: Serenity Spa - RECOMMENDED DESIGN SYSTEM

PATTERN: Hero-Centric + Social Proof
STYLE: Soft UI Evolution — soft shadows, subtle depth, calming
COLORS:
  Primary:    #E8B4B8 (Soft Pink)
  Secondary:  #A8D5BA (Sage Green)
  CTA:        #D4AF37 (Gold)
TYPOGRAPHY: Cormorant Garamond / Montserrat
AVOID: Neon colors, harsh animations, AI purple/pink gradients
```

---

## 4. Motion Design — Design Motion Principles Skill

**Type:** AI Skill  
**Repository:** https://github.com/kylezantos/design-motion-principles  
**Install:** `npx skills add kylezantos/design-motion-principles`

A motion and interaction design skill with **two modes** — **Create** (build interactive components with purposeful motion) and **Audit** (review existing animations). It provides context-aware guidance distilled from three distinct motion-design philosophies: **Emil Kowalski** (restraint & speed), **Jakub Krehel** (production polish), and **Jhey Tompkins** (creative experimentation).

The skill weights each lens by your project context instead of applying one philosophy everywhere.

### Key capabilities

| Feature | Description |
|---------|-------------|
| **Create mode** | Build interactive components with motion baked in — React, Framer Motion, CSS, or HTML |
| **Audit mode** | Review existing motion design with a motion-gap analysis and anti-AI-slop checklist |
| **3 designer lenses** | Context-aware weighting of Emil Kowalski, Jakub Krehel, and Jhey Tompkins |
| **Anti-slop checklist** | Flags AI-generated motion tells: pulsing indicators, hover-scale-on-everything, stagger-spam |
| **HTML audit report** | Self-contained HTML with auto-looping CSS demos beside each finding |
| **Motion cookbook** | Consolidated recipe library: enter/exit, easing, springs, clip-path, FLIP, scroll-driven |
| **Creation gotchas** | Self-check against common AI motion failure modes |

### Installation

```bash
npx skills add kylezantos/design-motion-principles
```

Or manually:

```bash
git clone https://github.com/kylezantos/design-motion-principles.git
cp -r design-motion-principles/skills/design-motion-principles ~/.claude/skills/
```

### Typical usage

Describe your motion needs in natural language:

```
Add a polished enter/exit animation to this modal
Build an animated toast component for this dashboard
Audit the motion design in this codebase
```

### Workflow integration

1. **Create** — Ask the agent to build a component with purposeful motion
2. The skill runs a light discovery (project context + lens weighting)
3. Generates components with the right recipes, accessibility, and performance defaults
4. **Audit** — Ask for a review and get a branded HTML report with visual demos

---

## 5. Component Generation — 21st.dev Magic MCP

**Type:** MCP Server  
**Repository:** https://github.com/21st-dev/magic-mcp  
**Website:** https://21st.dev/magic  
**Install:** `npx @21st-dev/cli@latest install <client> --api-key <key>`

21st.dev Magic MCP is an AI-powered component platform that generates beautiful, modern UI components from natural language descriptions. It acts as a **Model Context Protocol (MCP) server**, integrating directly with your IDE or coding environment.

### Key capabilities

| Feature | Description |
|---------|-------------|
| `/ui` command | Type `/ui` in your agent's chat to trigger component generation |
| Multi-IDE | Cursor, Windsurf, VS Code + Cline, Claude |
| Component library | Access to 21st.dev's growing collection of modern components |
| Real-time preview | Instantly see generated components |
| TypeScript | Full type-safe component output |
| SVGL integration | Access to professional brand assets and logos |

### Installation

```bash
# 1. Generate an API key at https://21st.dev/magic/console

# 2. Install for your IDE (one command)
npx @21st-dev/cli@latest install cursor --api-key your_key_here
# or: npx @21st-dev/cli@latest install windsurf --api-key your_key_here
# or: npx @21st-dev/cli@latest install cline --api-key your_key_here
# or: npx @21st-dev/cli@latest install claude --api-key your_key_here

# 3. Alternative: manual MCP config (cursor example)
# Add to ~/.cursor/mcp.json:
```

```json
{
  "mcpServers": {
    "@21st-dev/magic": {
      "command": "npx",
      "args": ["-y", "@21st-dev/magic@latest"],
      "env": { "API_KEY": "your_key_here" }
    }
  }
}
```

### Typical usage

```adblock
/ui create a modern navigation bar with responsive mobile menu
/ui build a pricing table with 3 tiers and hover effects
/ui design an animated hero section with gradient background
/ui add a testimonials carousel with avatars
```

### Workflow integration

1. **Describe** — Tell your agent what component you need via `/ui`
2. **Generate** — Magic MCP builds a polished, customizable component
3. **Integrate** — The component lands directly in your project
4. **Customize** — Full control over styles, logic, and behavior

---

## 6. Per-project setup checklist

```markdown
[ ] Initialize project with Vite + React + TypeScript
[ ] Install Motion (framer-motion) for animations
[ ] Install and configure Tailwind CSS v4
[ ] Add UI/UX Pro Max skill to agent environment
[ ] Add Design Motion Principles skill to agent environment
[ ] Configure 21st.dev Magic MCP server for component generation
[ ] Register design system tokens (colors, typography, spacing)
```

### Suggested stack

```markdown
[ ] @nextlevelbuilder/ui-ux-pro-max-skill — Design intelligence
[ ] kylezantos/design-motion-principles — Motion design
[ ] 21st.dev Magic MCP — Component generation
[ ] Motion — Animations and gestures
[ ] Tailwind CSS v4 — Utility-first styling
[ ] shadcn/ui or 21st.dev components — Base component library
[ ] SVGL — Brand asset library
```

---

## 7. Workflow example

```
1. You: "Create a SaaS landing page for an AI analytics startup"
2. Agent loads UI/UX Pro Max → generates design system:
   - Color palette, typography, layout pattern
3. Design Motion Principles → Motion components with purposeful animation
   - Create mode: enter/exit, scroll reveals, micro-interactions
4. 21st.dev Magic MCP → responsive nav bar, pricing table
5. Result: polished, animated, production-ready page in minutes
```

---

## 8. UI/UX Design Tips Reference

**File:** [`ui-ux-design-tips.html`](./ui-ux-design-tips.html)

A mobile-first reference HTML document compiling 6 core UI/UX principles from Katherine Gilligan's **"Building with Good UX"** series (Parts 3–10). Includes inline SVG diagrams, comparison tables, checklists, and a quick-reference cheat sheet.

### Topics Covered

| # | Topic | Key Insight |
|---|-------|-------------|
| 1 | **Loading States** | Choose loading type by expected duration — skeleton screens beat blind spinners |
| 2 | **Forms** | 6 commandments: inline feedback, show/hide password, enabled button, micro-interactions, input masks, clear error messages |
| 3 | **Empty States** | First impression matters — illustrate, give action, educate. Never leave a blank screen |
| 4 | **Partial States** | Prioritize critical content. Show what's ready while the rest loads |
| 5 | **Graceful Degradation** | Fail with elegance — offline mode, reduced functionality, friendly messages |
| 6 | **Consistency & Authenticity** | Transparency builds trust. Quality > frequency |

### How to Use

1. Open `ui-ux-design-tips.html` in any browser (mobile or desktop)
2. Browse by topic — each section is self-contained with SVG diagrams and practical checklists
3. Use the **Cheat Sheet** at the bottom for a quick reminder of all 6 principles
4. Reference during UI reviews, design discussions, or as a checklist before shipping features

### Credits

Based on the **"Building with Good UX"** series by [Katherine Gilligan](https://www.instagram.com/synsation_/) (@synsation_) — Parts 3–10, May–June 2026.

---

## 9. References

| Resource | Link |
|----------|------|
| Motion (Framer Motion) | https://github.com/framer/motion |
| Motion Documentation | https://motion.dev/docs/react-quick-start |
| UI/UX Pro Max Skill | https://github.com/nextlevelbuilder/ui-ux-pro-max-skill |
| UI/UX Pro Max Website | https://uupm.cc |
| Design Motion Principles | https://github.com/kylezantos/design-motion-principles |
| 21st.dev Magic MCP | https://github.com/21st-dev/magic-mcp |
| 21st.dev Website | https://21st.dev/magic |
| Tailwind CSS | https://tailwindcss.com |
| Vite | https://vitejs.dev |

---

## 10. Inspiration

This project was inspired by the Anthropic engineering paper:

> **Harness Design for Long-Running Applications**
> Anthropic Engineering — https://www.anthropic.com/engineering/harness-design-long-running-apps

And follows the same harness pattern established by [dev-harness](https://github.com/LeonardoDiasRR/dev-harness).

---

## 11. To Do

- [ ] **Component library integration guide** — Add step-by-step for combining 21st.dev Magic output with shadcn/ui or other component libraries
- [ ] **Animation pattern library** — Reusable Motion animation recipes (page transitions, scroll reveals, staggered lists)
- [ ] **Design system starter template** — A ready-to-fork repo with pre-configured Harness + design tokens
- [ ] **Responsive testing workflow** — Guidance on testing generated UIs across breakpoints
