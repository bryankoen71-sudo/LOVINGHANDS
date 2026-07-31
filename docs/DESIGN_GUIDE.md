
# Design Instructions & Visual Guide

## Splash Design
- Background: pure black #000
- Logo card: white #fff, 380x380, padding 28, radius 40
- Outer glow: ::before inset -18px linear-gradient 135deg #E6086B->#4F46E5 blur 22px opacity 0.85
- Outer second: inset -32px blur 38px opacity 0.55 reverse animation
- Inner glow pulse: box-shadow 0 0 0 2px white, 0 0 30px pink, 0 0 60px blue -> at 50% 0 0 3px white, 0 0 45px pink 0.95, 0 0 85px blue 0.85
- Dots: 3 dots loader, dotPulse animation background #222 -> #E6086B with box-shadow pink+blue
- Brand text: 11px, spacing 4px, #666, b white

## Top Nav Rotating Glow
- Wrapper: 60px circle, padding 4px
- Before: conic-gradient from 0deg: #E6086B 0deg, #4F46E5 90deg, #E6086B 180deg, #4F46E5 270deg, #E6086B 360deg, inset -5px, rotate 2s linear infinite
- After: same but blurred 18px inset -16px reverse
- Image: 100% circle white background

## Gallery
- Wrap: aspect 16/10, radius 24, border #1A1A1A, shadow 0 24px 64px -24px black 0.6
- Images: absolute inset 0 object-fit cover opacity 0 transition 0.6s, active opacity 1
- Dots: bottom center, flex gap 6px, bg rgba(0,0,0,0.35) blur 6px, padding 6x12 radius 999, dot 6px rgba white 0.4, active 22px white

## Admin Panel
- Colors: bg #080808, cards #111 border #222 radius 16
- Pink gradient button: linear-gradient 135deg #E6086B #4F46E5
- Sidebar 220px bg #0f0f0f
