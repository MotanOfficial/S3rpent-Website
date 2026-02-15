# S3rpent Website

Modern website showcasing the S3rpent app suite, built with SvelteKit and deployed to GitHub Pages.

## 🚀 Features

- Modern, responsive design
- Showcases S3rpent Media and S3rpent Vision applications
- Automatic deployment via GitHub Actions
- Optimized for GitHub Pages

## 📦 Setup

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Run development server:**
   ```bash
   npm run dev
   ```

3. **Build for production:**
   ```bash
   npm run build
   ```

4. **Preview production build:**
   ```bash
   npm run preview
   ```

## 🌐 GitHub Pages Deployment

### Initial Setup

1. **Push your code to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/s3rpent_website.git
   git push -u origin main
   ```

2. **Enable GitHub Pages:**
   - Go to your repository on GitHub
   - Navigate to **Settings** → **Pages**
   - Under **Source**, select **GitHub Actions**
   - The workflow will automatically deploy on every push to `main` or `master`

### Automatic Deployment

The repository includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) that:
- Automatically builds the site on every push to `main`/`master`
- Deploys to GitHub Pages
- Uses the correct base path (`/s3rpent_website`)

### Manual Deployment

If you need to deploy manually:

1. Build the site:
   ```bash
   npm run build
   ```

2. The built files will be in the `build/` directory

3. Push the `build/` folder to the `gh-pages` branch (if using manual deployment)

## 🔧 Configuration

### Base Path

The base path is configured in `svelte.config.js`:
- Production: `/s3rpent_website` (matches your repository name)
- Development: `` (empty, for local development)

If your repository name is different, update the `paths.base` in `svelte.config.js`.

## 📝 Project Structure

```
s3rpent_website/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions deployment workflow
├── src/
│   ├── app.css                 # Global styles
│   ├── app.d.ts                # TypeScript definitions
│   ├── app.html                # HTML template
│   ├── lib/                    # Shared components
│   └── routes/
│       ├── +layout.svelte      # Root layout
│       └── +page.svelte        # Homepage
├── static/                     # Static assets
├── svelte.config.js            # SvelteKit configuration
└── package.json
```

## 🛠️ Technologies

- **SvelteKit** - Framework
- **TypeScript** - Type safety
- **Vite** - Build tool
- **GitHub Actions** - CI/CD

## 📄 License

[Add your license here]

---

Made with ❤️ by MotanOfficial
