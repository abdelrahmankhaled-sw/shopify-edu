# Shopify Educational Theme

A customized Shopify theme based on Horizon with RTL support, enhanced banners, and automated deployment.

## Features

- ✅ **RTL Support**: Full right-to-left language support for Arabic
- ✅ **Homepage Banner**: Customizable announcement banners
- ✅ **CI/CD Pipeline**: Automated deployment with GitHub Actions
- ✅ **Content Protection**: Prevents overriding admin-configured content
- ✅ **Responsive Design**: Mobile-first approach
- ✅ **Modern UI**: Clean and professional design

## Setup Instructions

### Prerequisites

- Node.js 18.20+ or 20.10+
- Git 2.28.0+
- Shopify CLI
- Access to a Shopify development store

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone git@github.com:abdelrahmankhaled-sw/shopify-edu.git
   cd shopify-edu
   ```

2. **Install Shopify CLI**
   ```bash
   npm install -g @shopify/cli @shopify/theme
   ```

3. **Connect to your Shopify store**
   ```bash
   shopify theme dev --store your-store.myshopify.com
   ```

4. **Start local development**
   ```bash
   shopify theme dev
   ```

### GitHub Actions Setup

To enable automated deployment, add these secrets to your GitHub repository:

1. Go to your GitHub repository → Settings → Secrets and variables → Actions
2. Add the following secrets:

   - `SHOPIFY_STORE`: Your store name (without .myshopify.com)
   - `SHOPIFY_PASSWORD`: Your theme access password
   - `SHOPIFY_CLI_THEME_TOKEN`: Your Shopify CLI theme token

### Getting Shopify Credentials

1. **Store Name**: Found in your Shopify admin URL
2. **Theme Password**: 
   - Go to Shopify Admin → Online Store → Themes
   - Click "Actions" → "Edit code" on your theme
   - The password will be in the URL or you can generate a new one
3. **CLI Theme Token**:
   ```bash
   shopify auth login
   shopify theme token
   ```

## RTL Support

The theme automatically detects Arabic language (`ar`) and applies RTL styling:

- Text direction changes to right-to-left
- Layout elements are mirrored appropriately
- Arabic fonts are loaded
- Navigation and UI elements are adjusted

### Testing RTL

1. Change your store's language to Arabic in the admin
2. Or temporarily modify the locale in `layout/theme.liquid`
3. View the site to see RTL layout in action

## Homepage Banner

The theme includes a customizable announcement banner:

- **Location**: Top of the homepage
- **Customizable**: Colors, text, buttons, and behavior
- **Responsive**: Adapts to mobile devices
- **Dismissible**: Optional close button

### Customizing the Banner

Edit `templates/index.json` or use the Shopify theme editor:

```json
{
  "type": "announcement-banner",
  "settings": {
    "message": "Your announcement message",
    "button_text": "Shop Now",
    "button_link": "shopify://collections/all",
    "background_color": "#2563eb",
    "text_color": "#ffffff"
  }
}
```

## CI/CD Pipeline

The automated deployment pipeline:

### On Pull Requests:
- Runs theme validation and linting
- Deploys to development theme
- Comments on PR with preview link

### On Main Branch Push:
- Deploys to live theme
- Creates backup of current theme
- Protects admin-configured content
- Creates GitHub release

### Content Protection

The pipeline is configured to:
- Preserve admin-configured settings
- Backup themes before deployment
- Deploy code and content separately
- Avoid overriding customer data

## File Structure

```
├── assets/           # CSS, JS, and image files
│   ├── base.css     # Main stylesheet
│   └── rtl.css      # RTL-specific styles
├── blocks/          # Reusable theme blocks
├── config/          # Theme configuration
├── layout/          # Theme layout files
│   └── theme.liquid # Main layout template
├── locales/         # Translation files
│   ├── en.default.json
│   └── ar.json      # Arabic translations
├── sections/        # Theme sections
│   ├── header.liquid
│   └── announcement-banner.liquid
├── snippets/        # Reusable code snippets
├── templates/       # Page templates
│   └── index.json   # Homepage configuration
└── .github/
    └── workflows/   # GitHub Actions
```

## Development Workflow

1. **Create feature branch**
   ```bash
   git checkout -b feature/your-feature
   ```

2. **Make changes and test locally**
   ```bash
   shopify theme dev
   ```

3. **Commit and push**
   ```bash
   git add .
   git commit -m "Your commit message"
   git push origin feature/your-feature
   ```

4. **Create Pull Request**
   - GitHub Actions will deploy to development
   - Review changes in the preview environment

5. **Merge to main**
   - Automatic deployment to live theme
   - Release created automatically

## Troubleshooting

### Common Issues

1. **Authentication errors**: Ensure your Shopify credentials are correct
2. **Theme conflicts**: Check for conflicting themes in your store
3. **Build failures**: Review GitHub Actions logs for details

### Getting Help

- Check the [Shopify CLI documentation](https://shopify.dev/themes/tools/cli)
- Review [GitHub Actions logs](https://github.com/abdelrahmankhaled-sw/shopify-edu/actions)
- Contact the development team

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This theme is based on Shopify's Horizon theme and is customized for educational purposes.

---

**Store URL**: https://sw-edu-abdelrahman-khaled.myshopify.com

**Repository**: https://github.com/abdelrahmankhaled-sw/shopify-edu
