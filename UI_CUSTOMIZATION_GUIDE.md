# UI Customization Guide

## What's Been Implemented

### ✅ Completed Features
1. **UI Element Hiding**: CSS overlays hide buttons, leaderboard, and login
2. **Click Blocking**: Prevents clicks from reaching Unity UI elements
3. **Color Filter**: Transforms green to light pastel pink
4. **Credits Redirect**: 50/50 chance to open your URLs
5. **Message Interception**: Blocks Unity messages for unwanted features

## Adjusting Overlay Positions

If UI elements appear in different positions, edit the CSS in `index.html`:

```css
/* Example: Adjust feedback button position */
.overlay-feedback {
    bottom: 10px;    /* Distance from bottom */
    left: 10px;      /* Distance from left */
    width: 120px;    /* Overlay width */
    height: 40px;    /* Overlay height */
}
```

### Common UI Element Positions
- **Feedback Button**: Usually bottom-left (10px from bottom, 10px from left)
- **Download Button**: Usually bottom-left, next to feedback (10px from bottom, 140px from left)
- **More Games/Y8 Logo**: Usually bottom-right (10px from bottom, 10px from right)
- **Leaderboard**: Usually top-right or top-center (10px from top, 10px from right)
- **Login**: Usually top-right, near leaderboard (10px from top, 170px from right)

## Adjusting Color Filter

The color filter uses CSS to transform green to pink. To adjust:

```css
.pink-filter {
    filter: hue-rotate(300deg) saturate(0.6) brightness(1.3) contrast(0.9);
}
```

- `hue-rotate(300deg)`: Shifts colors (300° = green → pink)
- `saturate(0.6)`: Reduces color intensity (0.6 = 60% saturation)
- `brightness(1.3)`: Makes colors brighter (1.3 = 130%)
- `contrast(0.9)`: Adjusts contrast (0.9 = 90%)

**Note**: This affects the entire canvas. For precise color changes, you need the Unity source.

## Adjusting Click Blocking

Click blocking coordinates are in the `onRuntimeInitialized` function:

```javascript
// Block clicks in UI areas
if (x < 300 && y > height - 60) {
    // Bottom-left area (feedback, download)
}
if (x > width - 220 && y > height - 70) {
    // Bottom-right area (more games)
}
if (x > width - 280 && y < 60) {
    // Top-right area (leaderboard, login)
}
```

Adjust these coordinates based on where UI elements appear on your screen.

## Testing

1. Open the game in your browser
2. Check if UI elements are hidden
3. Try clicking where buttons were - they should be blocked
4. Check if colors look pinkish (may need filter adjustment)
5. Click credits button - should open your URLs

## For Complete Removal

To completely remove UI elements (not just hide them), you need:

1. **Unity Source Project** (`.unity` files)
2. **Unity Editor** (free from unity.com)
3. Open the scene and delete UI GameObjects
4. Rebuild WebGL version

## Troubleshooting

### UI elements still visible?
- Increase overlay size or adjust position
- Check browser console for errors
- Try different z-index values

### Colors not pink enough?
- Increase `hue-rotate` value (try 320deg or 340deg)
- Adjust `saturate` value (higher = more colorful)
- Adjust `brightness` value

### Clicks still work on buttons?
- Increase overlay size
- Adjust click blocking coordinates
- Check if overlays have `pointer-events: auto`

### Game performance issues?
- Color filters can impact performance
- Try reducing filter complexity
- Consider removing filter if not critical

