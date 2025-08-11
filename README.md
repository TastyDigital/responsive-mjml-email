# Kaizen Responsive Email Templates

This repository contains responsive email templates for the Kaizen Ticketing system, built using MJML (Mailjet Markup Language) with Razor syntax integration for .NET backend.

## Variable Naming Convention

Email templates use Razor variables that are derived from Bootstrap SCSS variables. The convention is to convert kebab-case SCSS variables to camelCase Razor variables.

### Variable Mapping

| Bootstrap SCSS Variable         | Razor Variable       | @Skin Variable               | Description                                  | Example Value                |
|---------------------------------|----------------------|------------------------------|----------------------------------------------|------------------------------|
| `$primary`                      | `primary`            | `@Skin.PrimaryColourHex`     | Main club/brand color                        | `#113D72`                    |
| `$secondary`                    | `secondary`          | `@Skin.SecondaryColourHex`   | Button highlight/accent color                | `#B90A25`                    |
| `$body-color`                   | `bodyColor`          | `@Skin.TextColourHex`        | Main text color                              | `#091A2E`                    |
| `$body-bg`                      | `bodyBg`             | `@Skin.BackgroundColourHex`  | Background color                             | `#E7E7E7`                    |
| `$border-radius`                | `borderRadius`       | `@Skin.BorderRadius`         | Global border radius                         | `16px`                       |
| `$font-weight-base`             | `fontWeightBase`     | `@Skin.BaseFontWeight`       | Base font weight                             | `400`                        |
| `$headings-font-weight`         | `headingsFontWeight` | `@Skin.HeadingsFontWeight`   | Headings font weight                         | `700`                        |
| `$btn-font-weight`              | `btnFontWeight`      | `@Skin.ButtonFontWeight`     | Button font weight                           | `500`                        |
| `$light-border-subtle`          | `lightBorderSubtle`  | TBD                          | Soft grey for subtle backgrounds and borders | `#e9ecef`                    |
| `$dark-border-subtle`           | `darkBorderSubtle`   | TBD                          | Dark grey for borders                        | `#adb5bd`                    |
| `$font-family-base`             | `fontFamilyBase`     | TBD                          | Web safe font family                         | `Mohave, Arial, sans-serif"` |
| N/A (Derived from fonts import) | `googleFontName`     | `@Skin.FontFamilySansSerif`  | Google font family                           | `Mohave`                     |
| N/A (Channel-specific base URL) | `channelBaseUrl`     | TBD                          | Base URL for channel links                   | `https://example.com`        |
| N/A (uses `color-contrast()`)   | `primaryContrast`    | TBD                          | Contrast color for primary                   | Auto-generated               |


### Special Variables

- **`googleFontName`**: Extracted from the font family for Google Fonts integration
- **`channelBaseUrl`**: Channel-specific base URL for links
- **`primaryContrast`**: This variable doesn't have a direct SCSS equivalent. It's generated using Bootstrap 5's `color-contrast()` function to ensure text is readable against the primary color background.


## File Organization

Templates are organized in the `src/` folder with a clear naming convention:

```
src/
├── account-activation.mjml         # Pure MJML template (for development)
├── account-activation.razor.mjml   # Razor-enhanced template (from backend)
├── password-reset.mjml            # Pure MJML template
├── password-reset.razor.mjml      # Razor-enhanced template
└── images/                        # Shared image assets
```

### Naming Convention
- **Pure MJML**: `template-name.mjml`
- **Razor-enhanced**: `template-name.razor.mjml`

This convention makes it immediately clear which files contain Razor syntax and which are pure MJML.

## Development Workflow

1. **Create Template**: Develop new templates in `src/` as pure MJML (e.g., `template-name.mjml`)
2. **Test Locally**: Use `npm run dev` to preview the template
3. **Backend Integration**: Copy template to Kaizen backend, add Razor syntax
4. **Save Enhanced Version**: Save the Razor-enhanced version with `.razor.mjml` suffix (e.g., `template-name.razor.mjml`)
5. **Variable Updates**: When Bootstrap SCSS variables change, update the Razor variables following the naming convention

## Commands

- `npm run dev` - Start development server with live reload
- `npm run build` - Build all MJML files to HTML
- `npm run watch` - Watch for changes and auto-compile
- `npm run serve` - Serve built files with browser-sync

## Notes

- All images should have @2x versions for retina displays
- Use template strings like `%=notification_greeting=%` for localization
- Preserve Razor syntax when updating templates from the backend
- Bootstrap 5.3.7 is available for CSS utility alignment