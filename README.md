# Custom-Components

# 1. ⭐ Rating Component for Next.js (Client Component)

[![TypeScript](https://img.shields.io/badge/Language-TypeScript-blue?style=flat-square)](https://www.typescriptlang.org/) 

[![Next.js App Router](https://img.shields.io/badge/Next.js-App%20Router-black?style=flat-square)](https://nextjs.org/docs/app)

[![Accessibility](https://img.shields.io/badge/Accessibility-Yes-green?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/Accessibility)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

A fully customizable, accessible, and interactive star rating component built for **Next.js App Router** using **React** and **TypeScript**.  
Supports half-star rendering, custom icons, read-only mode, and hydration-safe dynamic gradients.

## ✨ Features

- ⭐ Full and half-star support
- 🖌️ Customizable star icons (default provided)
- 🎨 Adjustable active/inactive colors
- 🔒 Read-only mode
- ♿ Keyboard and screen reader accessible
- 🚀 Optimized with `useCallback` and `useMemo`
- 🛠️ Hydration-safe gradients with `useId`
- ✅ Built-in TypeScript types

## Installation

```bash
  # No separate package - Copy the component directly into your project
```

Place the ```Rating.tsx``` file inside your ```src/components/``` folder.
    
## ⚙️ Usage

Here’s a full working example of how to use the `Rating` component interactively:

```tsx
"use client";

import React, { useState, useCallback } from 'react';
import Rating from '@/components/Rating'; // Adjust the import path accordingly

export function RatingExample() {
  const [currentRating, setCurrentRating] = useState(3.5);

  // Memoized callback to handle rating changes
  const handleRatingChange = useCallback((newRating: number) => {
    console.log("New rating selected (whole number):", newRating);
    setCurrentRating(newRating);
  }, []);

  return (
    <div style={{ padding: '20px', fontFamily: 'sans-serif' }}>
      <h2>Interactive Rating (allows float initial)</h2>
      <Rating
        initialValue={currentRating}
        onChange={handleRatingChange}
        size={32}
        activeColor="darkorange"
      />
      <p>Selected Rating: {currentRating}</p>
    </div>
  );
}
```

## 🛠️ Props


|  Prop   |   Type   | Default |      Description      |
| ------- | -------  | ------- | --------------------- |
| `count` | `number` |   `5`   | Total number of stars |
| `initialValue` | `number` | `0` | Initial rating (supports floats like 3.5) |
| `onChange` | `(value: number) => void` | `undefined` | Callback when rating changes |
| `size` | `number` | `24` | Size of each star (pixels) |
| `activeColor` | `string` | `#ffc107` | Color of filled stars |
| `inactiveColor` | `string` | `#e4e5e9` | Color of empty stars |
| `readonly` | `boolean` | `false` | Disables interactions when true |
| `className` | `string` | `''` | Custom class name for styling |
| `customIcon` | `React.ComponentType<{...props}>` | `StarIcon` | Replace default star with a custom component |
