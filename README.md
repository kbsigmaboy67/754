# Vercel Document.write & Iframe App

A simple Vercel application configured with permissive headers to allow `document.write()` from GitHub, Vercel, and about:blank domains, including full iframe support.

## Features

- ✅ Allows `document.write()` in iframes
- ✅ Permits embedding from GitHub, Vercel, and about:blank domains
- ✅ Full CORS support
- ✅ Permissive CSP for iframe content
- ✅ Cross-origin resource sharing enabled
- ✅ Interactive demos included

## Header Configuration

### Content Security Policy (CSP)
- **frame-ancestors**: Allows framing from 'self', GitHub domains, Vercel domains, and about:blank
- **script-src**: Allows unsafe-inline and unsafe-eval (required for document.write)
- **default-src, img-src, style-src, connect-src, frame-src**: All configured for GitHub and Vercel domains

### Cross-Origin Headers
- **X-Frame-Options**: ALLOWALL
- **Access-Control-Allow-Origin**: * (all origins)
- **Cross-Origin-Embedder-Policy**: unsafe-none
- **Cross-Origin-Opener-Policy**: unsafe-none
- **Cross-Origin-Resource-Policy**: cross-origin

## Deployment

### Deploy to Vercel

1. **Install Vercel CLI** (if not already installed):
   ```bash
   npm i -g vercel
   ```

2. **Deploy the app**:
   ```bash
   vercel
   ```

3. **Or deploy to production**:
   ```bash
   vercel --prod
   ```

### One-Click Deploy

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/yourusername/your-repo)

## Local Development

```bash
# Install Vercel CLI
npm i -g vercel

# Run locally with Vercel dev server
vercel dev
```

The app will be available at `http://localhost:3000`

## File Structure

```
.
├── index.html       # Main demo page
├── vercel.json      # Vercel configuration with headers
├── package.json     # Project metadata
└── README.md        # This file
```

## Usage Examples

### Example 1: Document.write in New Window
```javascript
const newWindow = window.open('', '_blank');
newWindow.document.write('<h1>Hello World</h1>');
newWindow.document.close();
```

### Example 2: Document.write in Iframe
```javascript
const iframe = document.createElement('iframe');
document.body.appendChild(iframe);

const doc = iframe.contentDocument;
doc.open();
doc.write('<h1>Iframe Content</h1>');
doc.close();
```

### Example 3: About:blank Iframe
```javascript
const iframe = document.createElement('iframe');
iframe.src = 'about:blank';
document.body.appendChild(iframe);

setTimeout(() => {
  iframe.contentDocument.write('<h1>About:blank content</h1>');
  iframe.contentDocument.close();
}, 100);
```

## Security Considerations

⚠️ **Warning**: This configuration is very permissive and suitable for development, testing, or specific use cases where you need maximum flexibility with iframes and document.write.

For production applications handling sensitive data, consider:
- Tightening CSP policies
- Restricting allowed domains
- Removing `unsafe-eval` and `unsafe-inline` if possible
- Implementing proper authentication and authorization

## Allowed Domains

The following domains can embed this app in iframes and use document.write:

- **GitHub**: `*.github.com`, `github.com`
- **Vercel**: `*.vercel.app`, `vercel.app`
- **About:blank**: `about:blank`

## Browser Compatibility

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Opera (latest)

## License

MIT

## Contributing

Feel free to open issues or submit pull requests for improvements!
