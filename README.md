# astryx-extra

Additional Astryx components composed with published Core. Independent of the Astryx monorepo; no monorepo build or install scripts are needed.

## Installation

```sh
bun add astryx-extra@github:Zizico2/astryx-extra#<commit>
```

Keep published `@astryxdesign/core` **0.7.13**, React 19.3 and StyleX 0.19 installed. Only import the extra components from this package; existing components and Astryx CSS continue to come from Core.

This package ships TypeScript source. Transpile `astryx-extra` through the consumer’s StyleX integration (for Next.js, add it to `transpilePackages`).

## Single choice

```tsx
import {SelectableCardGroup, SelectableCardGroupItem} from 'astryx-extra/SelectableCardGroup';

<SelectableCardGroup label="Forecast day" value={day} onChange={setDay}>
  <SelectableCardGroupItem value="today" label="Today">Today</SelectableCardGroupItem>
  <SelectableCardGroupItem value="tomorrow" label="Tomorrow">Tomorrow</SelectableCardGroupItem>
</SelectableCardGroup>
```

The group is controlled. A single choice (default) uses native radios: one radio tab stop, arrow-key selection, and no deselection on repeated activation. Use `selectionMode="multiple"` with a string array for checkboxes. Items accept existing SelectableCard layout, appearance and disabled props, plus a unique `value`. Groups support `isLabelHidden`, `description`, `htmlName`, `orientation` and Field container styling props. Context passes through wrappers such as Carousel.

## Compatibility and validation

This implementation uses Core’s existing internal card input bridge so it can reuse the actual published SelectableCard without duplicating its visuals or input handling. That bridge is outside Core’s public compatibility promise; the peer dependency is deliberately pinned. Verify compatibility before upgrading Core.

Run `bun install --frozen-lockfile --ignore-scripts` and `bun run typecheck`. Real-browser selection, keyboard, tab, card activation and responsive integration checks run in the consuming [ipma-weather MR #4](https://github.com/Zizico2/ipma-weather/pull/4).

## Attribution

Adapted from MIT-licensed [Astryx](https://github.com/meta/astryx), including its Lab SelectableCardGroup and the Core implementation in [the fork](https://github.com/Zizico2/astryx/pull/1). Original copyright and license are preserved. This is an independent project.
