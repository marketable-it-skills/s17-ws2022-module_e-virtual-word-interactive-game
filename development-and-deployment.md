# Development and Deployment Guide

## Development Setup

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- Text editor or IDE (VS Code, WebStorm, etc.)
- Local web server (optional but recommended)
- Basic knowledge of HTML5, CSS3, and JavaScript

### Project Structure

```
project/
├── index.html              # Main game entry point
├── css/
│   ├── styles.css          # Game styling
│   └── animations.css      # Animation definitions
├── js/
│   ├── game.js             # Main game logic
│   ├── avatar.js           # Avatar movement and controls
│   ├── scenes.js           # Scene management
│   ├── quiz.js             # Learning activities
│   └── storage.js          # LocalStorage management
├── assets/
│   ├── images/             # Game sprites and backgrounds
│   ├── sounds/             # Audio files
│   └── scenes/             # Scene-specific assets
└── media/
    └── scene-definitions/  # Scene layout specifications
```

### Development Environment

1. **Local Server Setup** (recommended):
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js
   npx serve .
   
   # Using PHP
   php -S localhost:8000
   ```

2. **File Protocol**: Direct file opening may work but can cause CORS issues with asset loading.

## Technical Requirements

### Core Technologies

- **HTML5**: Semantic markup and Canvas (if used)
- **CSS3**: Animations, transitions, responsive design
- **JavaScript ES6+**: Game logic, event handling, LocalStorage
- **Web APIs**: 
  - LocalStorage for game state persistence
  - Fullscreen API for full-screen toggle
  - PostMessage API for score reporting

### Browser Compatibility

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

### Performance Considerations

- Optimize images (WebP, PNG compression)
- Minimize JavaScript bundle size
- Use CSS transforms for smooth animations
- Implement efficient collision detection
- Debounce user input events

## Game Architecture

### Core Components

1. **Game Engine**: Main game loop and state management
2. **Scene Manager**: Handle scene loading, switching, and asset management  
3. **Avatar Controller**: Process user input and avatar movement
4. **Quiz System**: Display learning activities and handle responses
5. **Sound Manager**: Audio playback and management
6. **Storage Manager**: Game state persistence

### Event System

Implement a centralized event system for:
- Avatar movement events
- Scene transition events
- Quiz completion events
- User interaction events

## Asset Management

### Media Files Organization

Follow the provided media file structure:
- Scene assets grouped by scene folders
- Audio files in dedicated sound directory
- Follow z-index specifications from scene documents

### Loading Strategy

- Preload critical assets (avatar, UI elements)
- Lazy load scene-specific assets
- Implement loading indicators for better UX

## Deployment

### Production Build

1. **Asset Optimization**:
   ```bash
   # Compress images
   imagemin input/ --out-dir=output/
   
   # Minify JavaScript
   terser game.js -o game.min.js
   
   # Minify CSS
   cleancss -o styles.min.css styles.css
   ```

2. **File Structure**:
   ```
   XX_module_e/
   ├── index.html
   ├── assets/
   ├── css/
   ├── js/
   └── media/
   ```

### Server Configuration

#### Apache (.htaccess)
```apache
# Enable compression
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/css text/javascript application/javascript
</IfModule>

# Cache static assets
<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType image/png "access plus 1 month"
    ExpiresByType audio/mpeg "access plus 1 month"
    ExpiresByType text/css "access plus 1 week"
    ExpiresByType application/javascript "access plus 1 week"
</IfModule>
```

#### Nginx
```nginx
location ~* \.(png|jpg|jpeg|gif|ico|svg)$ {
    expires 1M;
    add_header Cache-Control "public, immutable";
}

location ~* \.(css|js)$ {
    expires 1w;
    add_header Cache-Control "public";
}
```

### Docker Deployment (Optional)

```dockerfile
FROM nginx:alpine

COPY . /usr/share/nginx/html/XX_module_e/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

## Testing

### Browser Testing

Test across different browsers and devices:
- Desktop browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Different screen resolutions and orientations

### Functionality Testing

- Avatar movement (keyboard and touch/mouse)
- Scene transitions and animations
- Quiz interactions and barrier removal
- LocalStorage persistence
- Full-screen mode toggle
- API integration and error handling

### Performance Testing

- Frame rate during animations
- Memory usage during extended play
- Asset loading times
- Responsiveness on lower-end devices

## Validation

### Code Quality

- Use ESLint for JavaScript linting
- Validate HTML with W3C validator
- Check CSS with CSS validator
- Ensure accessibility standards compliance

### Game Mechanics Validation

- Verify all quiz barriers function correctly
- Test scene switching edge cases
- Validate score calculation and API communication
- Confirm LocalStorage data persistence across sessions

## Troubleshooting

### Common Issues

1. **Assets not loading**: Check file paths and server configuration
2. **Quiz barriers not working**: Verify collision detection logic
3. **Sound not playing**: Check audio format support and user interaction requirements
4. **LocalStorage issues**: Verify browser support and quota limits
5. **Full-screen problems**: Check browser permissions and API usage

### Debug Tools

- Browser developer tools for debugging
- Console logging for game state tracking  
- Performance profiling for optimization
- Network tab for asset loading issues

## Security Considerations

- Validate all user inputs
- Sanitize data before LocalStorage
- Implement proper error handling for API calls
- Use HTTPS in production when possible

## Maintenance

- Regular browser compatibility testing
- Asset optimization updates
- Performance monitoring
- User feedback integration