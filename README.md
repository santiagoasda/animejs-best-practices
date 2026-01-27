# anime.js Best Practices

A comprehensive skill/reference guide for implementing animations with [anime.js v4](https://animejs.com/) - the lightweight JavaScript animation engine created by [Julian Garnier](https://github.com/juliangarnier).

## What is this?

This repository contains best practices, patterns, and comprehensive API documentation for anime.js v4. It's designed to be used as a **skill** for AI coding assistants (Claude Code, Cursor, etc.) but also serves as a standalone reference for developers.

## Quick Start

```bash
npm install animejs
```

```javascript
import { waapi, stagger } from 'animejs';

// Hardware-accelerated animation (recommended for most use cases)
waapi.animate('.element', {
  translateX: 200,
  opacity: [0, 1],
  delay: stagger(100),
  duration: 800,
  ease: 'outExpo'
});
```

## Repository Structure

```
animejs-best-practices/
├── SKILL.md                 # Main skill file with core patterns
├── agents/                  # AI agent definitions
├── examples/                # Working code examples
│   ├── basic-animation.js
│   ├── timeline-sequence.js
│   ├── react-integration.jsx
│   └── scroll-reveal.js
└── references/
    ├── docs/                # Official anime.js v4 API documentation
    │   ├── getting-started/
    │   ├── animation/
    │   ├── timeline/
    │   ├── animatable/
    │   ├── draggable/
    │   ├── layout/
    │   ├── scope/
    │   ├── events/
    │   ├── svg/
    │   ├── text/
    │   ├── utilities/
    │   ├── easings/
    │   ├── web-animation-api/
    │   └── engine/
    └── [best practice guides]
```

## Key Concepts

### WAAPI-First Approach

Always prefer `waapi.animate()` over `animate()` unless you need JS engine features:

| Use `waapi.animate()` | Use `animate()` |
|-----------------------|-----------------|
| CSS transforms/opacity | 500+ targets |
| Bundle size matters (3KB vs 10KB) | JS objects, Canvas, WebGL |
| Need hardware acceleration | Complex timeline orchestration |
| Simple entrance animations | SVG path morphing |

### Critical: Milliseconds, Not Seconds!

```javascript
// WRONG - animation barely visible (2ms)
waapi.animate('.el', { opacity: 1, duration: 2 });

// CORRECT - 2 second animation
waapi.animate('.el', { opacity: 1, duration: 2000 });
```

## Documentation Coverage

This repository includes complete documentation for all anime.js v4 features:

- **Core**: Timer, Animation, Timeline
- **Interactive**: Animatable, Draggable
- **Layout**: FLIP animations, enter/exit states
- **Events**: ScrollObserver, thresholds, sync modes
- **SVG**: morphTo, createDrawable, createMotionPath
- **Text**: splitText for character/word/line animations
- **Utilities**: stagger, helpers ($, get, set, random, math functions)
- **Easings**: Built-in eases, cubic-bezier, spring physics
- **WAAPI**: Hardware-accelerated Web Animations API wrapper
- **Engine**: Global configuration, time units, FPS

## Using as an AI Skill

### Claude Code

Add this repository as a skill in your Claude Code configuration to get anime.js best practices automatically applied to your animation code.

### Other AI Assistants

Reference the `SKILL.md` file in your system prompt or context to enable anime.js expertise.

## Attribution

- **anime.js** is created by [Julian Garnier](https://github.com/juliangarnier)
- Official website: [animejs.com](https://animejs.com/)
- Official repository: [github.com/juliangarnier/anime](https://github.com/juliangarnier/anime)
- Documentation source: [animejs.com/documentation](https://animejs.com/documentation)

## License

This skill/reference guide is released under the [MIT License](LICENSE).

**Note**: anime.js itself is licensed under the MIT License. See the [anime.js repository](https://github.com/juliangarnier/anime) for its license terms.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests to improve the documentation, add examples, or fix errors.
