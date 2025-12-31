# AR Experience - Catalogue

An interactive Augmented Reality (AR) experience that displays video content when specific image targets are detected. Built with A-Frame and MindAR for image-based AR tracking.

## Overview

This project creates an immersive AR catalog experience where users can point their device's camera at specific images (targets) to trigger video playback. The application supports multiple image targets, each associated with a unique video asset.

## Features

- **Image-Based AR Tracking**: Uses MindAR for robust image target recognition
- **Multiple Video Targets**: Supports 12 image targets with associated video content
- **Mobile-Optimized**: Responsive design optimized for mobile devices
- **Memory Management**: Automatic cleanup and optimization to prevent memory leaks
- **Error Recovery**: Robust error handling and video playback recovery
- **Loading Screen**: Custom loading screen with progress indicators
- **Interactive Playback**: Play button interface for user-controlled video playback

## Technologies Used

- **A-Frame** (v1.3.0): Web framework for building VR/AR experiences
- **MindAR** (v1.2.0): JavaScript library for image-based AR tracking
- **Three.js**: 3D graphics library (via A-Frame)
- **WebGL**: For rendering 3D graphics and video textures

## Project Structure

```
CatalogueOrestKhamula-main/
├── index.html              # Main HTML file with AR scene
├── targets.mind            # MindAR image target file (binary)
├── assets/                 # Media assets directory
│   ├── mainbackground.png  # Loading screen background
│   ├── asset.mp4          # Video for target 0
│   ├── asset2.mp4         # Video for target 1
│   ├── asset3.mp4         # Video for target 2
│   ├── asset4.mp4         # Video for target 3
│   ├── asset5.mp4         # Video for target 4
│   ├── asset6.mp4         # Video for target 5
│   ├── asset7.mp4         # Video for target 6
│   ├── asset8.mp4         # Video for target 7
│   ├── asset9.mp4         # Video for target 8
│   ├── asset10.mp4        # Video for target 9
│   └── asset12.mp4        # Video for target 11
└── README.md              # This file
```

## Setup & Installation

### Prerequisites

- A modern web browser with WebGL support
- A web server (required for AR functionality - cannot run from `file://` protocol)
- Camera access permissions on your device

### Running the Project

1. **Clone or download the project** to your local machine

2. **Start a local web server** (required for AR to work):
   
   Using Python 3:
   ```bash
   python3 -m http.server 8000
   ```
   
   Using Python 2:
   ```bash
   python -m SimpleHTTPServer 8000
   ```
   
   Using Node.js (http-server):
   ```bash
   npx http-server -p 8000
   ```

3. **Open in browser**:
   - Navigate to `http://localhost:8000` in your browser
   - Grant camera permissions when prompted
   - Point your camera at the image targets to trigger AR content

### Mobile Deployment

For mobile devices:

1. Deploy the project to a web server (GitHub Pages, Netlify, Vercel, etc.)
2. Access the URL from your mobile device
3. Ensure HTTPS is enabled (required for camera access on most browsers)
4. Add to home screen for a more app-like experience

## Usage

1. **Grant Camera Permission**: When you first load the page, allow camera access
2. **Wait for Loading**: The AR system will initialize (loading screen will appear)
3. **Point at Target**: Point your device's camera at one of the image targets
4. **Play Video**: When a target is detected, a play button will appear - tap it to start video playback
5. **Switch Targets**: Point at different targets to switch between different videos

## Image Targets

The project uses 12 image targets (indices 0-11) defined in `targets.mind`:
- Targets 0-9: Each associated with a video (asset.mp4 through asset10.mp4)
- Target 10: No video associated
- Target 11: Associated with asset12.mp4

## Technical Details

### AR Configuration

- **Filter Settings**: 
  - `filterMinCF: 0.0001` - Minimum confidence filter
  - `filterBeta: 0.001` - Beta filter value
- **Camera**: Uses rear-facing camera (`facingMode: 'environment'`)
- **Resolution**: Optimized for 1280x720

### Video Material

Custom shader material with:
- Edge fading effect for smooth video edges
- Global opacity of 0.8
- Transparent background support

### Memory Management

The application includes automatic memory management:
- Light cleanup every 2 minutes
- Full cleanup every 10 minutes
- Memory monitoring and automatic cleanup when memory usage exceeds 80%
- Cleanup on page visibility changes and unload events

### Browser Compatibility

- **Chrome/Edge**: Full support
- **Safari**: Full support (iOS 11.3+)
- **Firefox**: Full support
- **Opera**: Full support

## Customization

### Adding New Targets

1. Add your image target to the MindAR target file using [MindAR Creator](https://hiukim.github.io/mind-ar-js-doc/tools/compile/)
2. Add a new video asset to the `assets/` directory
3. Add the video element in the `<a-assets>` section
4. Add a new `<a-entity>` with `mindar-image-target` and corresponding video plane

### Modifying Video Properties

Edit the `<a-plane>` attributes in the HTML:
- `width` and `height`: Adjust video size
- `position`: Adjust video position relative to target
- `rotation`: Adjust video rotation

### Changing Loading Screen

Replace `assets/mainbackground.png` with your custom background image.

## Troubleshooting

### Camera Not Working
- Ensure you're using HTTPS (required for camera access)
- Check browser permissions for camera access
- Try a different browser

### Videos Not Playing
- Check that video files are in the correct format (MP4 recommended)
- Ensure videos have proper CORS headers if hosted on a different domain
- Check browser console for error messages

### AR Not Detecting Targets
- Ensure good lighting conditions
- Hold device steady
- Make sure the target image is clear and in focus
- Check that `targets.mind` file is accessible

### Performance Issues
- Close other browser tabs
- Ensure device has sufficient memory
- Check that videos are optimized (appropriate resolution and bitrate)

## License

This project appears to be a custom AR catalog experience. Please check with the project owner for specific licensing information.

## Credits

- **A-Frame**: https://aframe.io/
- **MindAR**: https://github.com/hiukim/mind-ar-js

## Notes

- The application requires a web server to run (cannot use `file://` protocol)
- HTTPS is recommended for production deployment
- Camera permissions are required for AR functionality
- Video playback may require user interaction (tap to play) on some browsers

