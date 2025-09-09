# Deployment Guide - GitHub Setup

This guide will help you deploy your Jeremy Williams VP Portfolio to GitHub and make it publicly accessible.

## 📋 Prerequisites

- GitHub account
- Git installed on your computer
- Your portfolio files ready

## 🚀 Step-by-Step GitHub Deployment

### Step 1: Create GitHub Repository

1. **Go to GitHub.com** and sign in
2. **Click the "+" icon** in the top right corner
3. **Select "New repository"**
4. **Repository settings**:
   - **Name**: `jeremy-williams-portfolio` (or your preferred name)
   - **Description**: "Professional portfolio website for VP Software Development"
   - **Visibility**: Public (for GitHub Pages to work with free account)
   - **Initialize**: Check "Add a README file"
   - **License**: Choose MIT License

### Step 2: Clone Repository Locally

```bash
# Replace 'yourusername' with your GitHub username
git clone https://github.com/yourusername/jeremy-williams-portfolio.git
cd jeremy-williams-portfolio
```

### Step 3: Set Up Project Structure

Create this folder structure in your cloned repository:

```
jeremy-williams-portfolio/
├── index.html              # Your website file
├── README.md               # Project documentation
├── assets/
│   └── images/
│       ├── ProPhoto1.png   # Your professional photo 1
│       ├── ProPhoto2.png   # Your professional photo 2
│       └── AIPhoto.png     # Your AI-generated photo
└── docs/
    └── DEPLOYMENT.md       # This file
```

### Step 4: Add Your Files

1. **Copy the website HTML**:
   - Save the complete website code as `index.html`
   - Place it in the root directory

2. **Add your photos**:
   ```bash
   mkdir -p assets/images
   # Copy your photos to assets/images/
   # Ensure they're named: ProPhoto1.png, ProPhoto2.png, AIPhoto.png
   ```

3. **Update file paths** in `index.html`:
   ```javascript
   // Update the photo loading function to use correct paths
   const possibleNames = [
       `assets/images/${baseName}.png`, 
       `assets/images/${baseName}.jpg`, 
       `assets/images/${baseName}.jpeg`,
       // ... other variations
   ];
   ```

### Step 5: Commit and Push

```bash
# Add all files
git add .

# Commit with a meaningful message
git commit -m "Initial portfolio website with professional photos"

# Push to GitHub
git push origin main
```

### Step 6: Enable GitHub Pages

1. **Go to your repository** on GitHub.com
2. **Click "Settings"** tab
3. **Scroll down to "Pages"** in the left sidebar
4. **Source**: Select "Deploy from a branch"
5. **Branch**: Select "main" and "/ (root)"
6. **Click "Save"**

Your website will be available at:
`https://yourusername.github.io/jeremy-williams-portfolio`

## 🔧 File Path Fixes for GitHub Pages

Since GitHub Pages serves files differently, update your JavaScript photo loading:

```javascript
// In your index.html, update the loadPhoto function:
async function loadPhoto(baseName, containerId, loadingId) {
    const possibleNames = [
        `assets/images/${baseName}.png`,
        `assets/images/${baseName}.jpg`, 
        `assets/images/${baseName}.jpeg`,
        `assets/images/${baseName.toLowerCase()}.png`,
        `assets/images/${baseName.toLowerCase()}.jpg`,
        // ... other variations with assets/images/ prefix
    ];
    
    // Rest of the function remains the same
}
```

## 📂 Alternative: Direct File Embedding

If the dynamic loading doesn't work on GitHub Pages, you can embed images directly:

```html
<!-- Replace the photo containers with direct img tags -->
<div id="pro-photo1-container" class="w-full h-full rounded-xl overflow-hidden">
    <img src="assets/images/ProPhoto1.png" alt="Professional Photo 1" class="w-full h-full object-cover">
</div>

<div id="pro-photo2-container" class="w-full h-full rounded-xl overflow-hidden">
    <img src="assets/images/ProPhoto2.png" alt="Professional Photo 2" class="w-full h-full object-cover">
</div>

<div id="ai-photo-container" class="w-full h-full">
    <img src="assets/images/AIPhoto.png" alt="AI Generated Portrait" class="w-full h-full object-cover">
</div>
```

## 🌐 Custom Domain (Optional)

To use a custom domain like `jeremywilliams.dev`:

1. **Buy a domain** from a registrar (GoDaddy, Namecheap, etc.)
2. **In GitHub Pages settings**:
   - Add your custom domain
   - Enable "Enforce HTTPS"
3. **Configure DNS** at your registrar:
   ```
   Type: CNAME
   Host: www
   Value: yourusername.github.io
   
   Type: A
   Host: @
   Values: 
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

## 🔄 Making Updates

To update your website:

```bash
# Make changes to your files
# Then commit and push
git add .
git commit -m "Update portfolio content"
git push origin main
```

GitHub Pages will automatically rebuild and deploy your changes.

## 🐛 Troubleshooting

### Photos Not Loading
1. **Check file paths**: Ensure photos are in `assets/images/`
2. **Check file names**: Must match exactly (case-sensitive)
3. **Check file formats**: Use .png, .jpg, or .jpeg
4. **Browser console**: Check for error messages (F12)

### Website Not Deploying
1. **Check GitHub Pages settings**: Ensure source is set correctly
2. **Wait time**: Can take 5-10 minutes for first deployment
3. **Repository visibility**: Must be public for free GitHub Pages

### Custom Domain Issues
1. **DNS propagation**: Can take up to 24 hours
2. **HTTPS certificate**: May take time to generate
3. **CNAME file**: GitHub should create this automatically

## ✅ Success Checklist

- [ ] Repository created on GitHub
- [ ] Files uploaded and committed
- [ ] GitHub Pages enabled
- [ ] Website accessible at GitHub Pages URL
- [ ] Photos loading correctly
- [ ] All sections displaying properly
- [ ] Mobile responsive working
- [ ] Custom domain configured (if applicable)

## 📞 Support

If you encounter issues:
1. Check GitHub Pages documentation
2. Verify file paths and names
3. Test locally first
4. Check browser console for errors
5. GitHub Community Forums for help

Your professional portfolio will be live and accessible to potential employers, clients, and colleagues!
