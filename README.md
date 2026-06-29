# 🔐 Password Generator

**A powerful, secure, and user-friendly password generator built entirely with HTML, CSS, and JavaScript**

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/akash6595/password-generator/blob/main/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/akash6595/password-generator)](https://github.com/Akash6595/password-generator/issues)
[![GitHub stars](https://img.shields.io/github/stars/akash6595/password-generator?style=social)](https://github.com/akash6595/password-generator/stargazers)

---

## 🚀 Overview

Tired of weak passwords that compromise your security? **Random Password Generator** is a simple yet powerful tool that creates strong, unique passwords with just a few clicks. Perfect for developers, security-conscious users, and anyone who needs reliable authentication.

### Key Features:
✅ **Customizable length** - Generate passwords from 8 to 100+ characters
✅ **Multiple character sets** - Choose from uppercase, lowercase, numbers, and special characters
✅ **Copy to clipboard** - Instantly copy generated passwords
✅ **No dependencies** - Works entirely in the browser
✅ **Responsive design** - Works on any device
✅ **Open source** - Free to use and modify

### Who This Is For:
- Developers creating secure applications
- Security professionals managing multiple accounts
- Regular users who want stronger passwords
- Anyone who needs temporary passwords for services

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Character Selection** | Choose from uppercase, lowercase, numbers, and special characters |
| **Password Length** | Adjustable from 8 to 100+ characters |
| **Instant Generation** | Generate new passwords with a single click |
| **Clipboard Copy** | One-click copy to clipboard functionality |
| **Dark/Light Mode** | Automatic theme detection |
| **No Installation** | Works directly in your browser |
| **Progressive Enhancement** | Works even if JavaScript is disabled |

---

## 🛠️ Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Build Tools**: None (pure frontend)
- **Hosting**: Any static hosting service (GitHub Pages, Netlify, Vercel, etc.)
- **Browser Support**: Chrome, Firefox, Safari, Edge (latest versions)

**System Requirements**:
- Modern web browser
- Internet connection (for online version)
- No additional software required

---

## 📦 Installation

### Quick Start (Single File Version)

1. **Download the files**:
   ```bash
   git clone https://github.com/akash6595/password-generator.git
   ```

2. **Open index.html** in any modern web browser

3. **Start generating passwords immediately!**

### Alternative Installation Methods

#### As a GitHub Pages Site
```bash
# Clone the repository
git clone https://github.com//password-generator.git

# Navigate to the project directory
cd random-password-generator

# Install gh-pages package (if not already installed)
npm install gh-pages --save-dev

# Add these to your package.json if you have one:
"homepage": "https://akash6595.github.io/password-generator",
"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist"
}

# Build and deploy
npm run build
npm run deploy
```
---

## 🎯 Usage

### Basic Usage

Here's a complete, working example of how to use the password generator:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Password Generator</h1>

        <div class="controls">
            <label for="length">Password Length:</label>
            <input type="range" id="length" min="8" max="100" value="12">

            <div class="character-options">
                <label><input type="checkbox" checked> Uppercase</label>
                <label><input type="checkbox" checked> Lowercase</label>
                <label><input type="checkbox" checked> Numbers</label>
                <label><input type="checkbox" checked> Special Characters</label>
            </div>
        </div>

        <button id="generate">Generate Password</button>
        <button id="copy">Copy</button>

        <div class="password-display">
            <input type="text" id="password" readonly>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
```

### Advanced Usage

To enhance the password generator with additional features:

```javascript
// Enhanced script.js example with additional functionality
document.addEventListener('DOMContentLoaded', function() {
    const passwordInput = document.getElementById('password');
    const generateBtn = document.getElementById('generate');
    const copyBtn = document.getElementById('copy');
    const lengthSlider = document.getElementById('length');
    const characterOptions = document.querySelectorAll('.character-options input');

    // Character sets
    const uppercaseChars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    const lowercaseChars = 'abcdefghijklmnopqrstuvwxyz';
    const numberChars = '0123456789';
    const specialChars = '!@#$%^&*()_+-=[]{}|;:,.<>?';

    // Generate password function
    function generatePassword() {
        let chars = '';
        const length = parseInt(lengthSlider.value);

        // Build character set based on selected options
        characterOptions.forEach(option => {
            if (option.checked) {
                if (option.nextElementSibling.textContent === 'Uppercase') {
                    chars += uppercaseChars;
                } else if (option.nextElementSibling.textContent === 'Lowercase') {
                    chars += lowercaseChars;
                } else if (option.nextElementSibling.textContent === 'Numbers') {
                    chars += numberChars;
                } else if (option.nextElementSibling.textContent === 'Special Characters') {
                    chars += specialChars;
                }
            }
        });

        // Generate password
        let password = '';
        for (let i = 0; i < length; i++) {
            const randomIndex = Math.floor(Math.random() * chars.length);
            password += chars.charAt(randomIndex);
        }

        passwordInput.value = password;
    }

    // Event listeners
    generateBtn.addEventListener('click', generatePassword);
    copyBtn.addEventListener('click', function() {
        if (passwordInput.value) {
            passwordInput.select();
            document.execCommand('copy');
            copyBtn.textContent = 'Copied!';
            setTimeout(() => {
                copyBtn.textContent = 'Copy';
            }, 2000);
        }
    });

    lengthSlider.addEventListener('input', generatePassword);
    characterOptions.forEach(option => {
        option.addEventListener('change', generatePassword);
    });

    // Generate initial password
    generatePassword();
});
```

### CSS Styling Example

```css
/* style.css example with responsive design */
:root {
    --primary-color: #4a6fa5;
    --secondary-color: #166088;
    --light-color: #f8f9fa;
    --dark-color: #343a40;
    --success-color: #28a745;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--light-color);
    color: var(--dark-color);
    margin: 0;
    padding: 20px;
    transition: background-color 0.3s, color 0.3s;
}

.container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1 {
    color: var(--primary-color);
    text-align: center;
    margin-bottom: 20px;
}

.controls {
    display: flex;
    flex-direction: column;
    gap: 15px;
    margin-bottom: 20px;
}

.controls label {
    font-weight: 600;
    margin-bottom: 5px;
}

input[type="range"] {
    width: 100%;
}

.character-options {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 10px;
}

.character-options label {
    display: flex;
    align-items: center;
    gap: 5px;
    font-size: 0.9em;
}

button {
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1em;
    transition: background-color 0.3s;
}

#generate {
    background-color: var(--primary-color);
    color: white;
    width: 100%;
    margin-bottom: 10px;
}

#generate:hover {
    background-color: var(--secondary-color);
}

#copy {
    background-color: var(--success-color);
    color: white;
    width: 100%;
}

#copy:hover {
    background-color: #218838;
}

.password-display {
    margin-top: 20px;
}

.password-display input {
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 1em;
    text-align: center;
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
    body {
        background-color: var(--dark-color);
        color: var(--light-color);
    }

    .container {
        background-color: #343a40;
        border: 1px solid #495057;
    }

    #generate {
        background-color: var(--secondary-color);
    }

    #generate:hover {
        background-color: #0f4c75;
    }

    #copy {
        background-color: #218838;
    }

    #copy:hover {
        background-color: #1b7e32;
    }
}

/* Responsive adjustments */
@media (max-width: 600px) {
    .character-options {
        flex-direction: column;
        align-items: flex-start;
    }
}
```

---

## 📁 Project Structure

```
password-generator/
├── .gitignore          # Git ignore file
├── index.html          # Main HTML file
├── script.js           # JavaScript functionality
├── style.css           # CSS styling
├── README.md           # Project documentation
└── (Optional) assets/  # For any additional assets
```

---

## 🔧 Configuration

### Customization Options

1. **Character Sets**: Modify the character strings in `script.js` to include/exclude specific characters
2. **Password Length**: Adjust the range in the HTML range input
3. **Colors**: Change the CSS variables in `style.css` for theming
4. **UI Elements**: Modify the HTML structure to change layout and appearance

### Environment Variables

For potential future enhancements (like analytics), you could add:

```javascript
// In script.js
const ANALYTICS_ENABLED = process.env.ANALYTICS_ENABLED === 'true';
```

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### How to Contribute

1. **Fork the repository**
2. **Create your feature branch**: `git checkout -b feature/your-feature`
3. **Commit your changes**: `git commit -m 'Add some feature'`
4. **Push to the branch**: `git push origin feature/your-feature`
5. **Open a Pull Request**

### Development Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/akash6595/password-generator.git
   ```

2. Open the `index.html` file in your preferred code editor

3. Make your changes to the corresponding files:
   - HTML structure: `index.html`
   - Styling: `style.css`
   - JavaScript functionality: `script.js`

4. Test your changes in multiple browsers

### Code Style Guidelines

- **HTML**: Use semantic elements, proper indentation (2 spaces)
- **CSS**: Use CSS variables for theming, follow BEM methodology where appropriate
- **JavaScript**: Use ES6+ features, consistent indentation (2 spaces), meaningful variable names
- **Accessibility**: Ensure all interactive elements have proper labels and ARIA attributes

### Pull Request Process

1. Ensure your code follows the style guidelines
2. Write clear, concise commit messages
3. Test your changes thoroughly
4. Document any new features or changes in the README
5. Submit your pull request with a clear description

---

---

## 👥 Authors & Contributors

**Current Maintainers**:
- [Your Name](https://github.com/akash6595) - Initial work and ongoing maintenance

**Special Thanks**:
- All contributors who have helped improve this project
- The open-source community for inspiration and resources

---

## 🐛 Issues & Support

### How to Report Issues

If you encounter any problems or have suggestions for improvement:

1. Search the [existing issues](https://github.com/akash6595/password-generator/issues) to see if your issue has already been reported
2. If not, [open a new issue](https://github.com/akash6595/password-generator/issues/new) with:
   - A clear title describing the problem
   - A detailed description of what went wrong
   - Steps to reproduce the issue
   - Any relevant screenshots or error messages
   - Your environment (browser, OS, etc.)

### Where to Get Help

- **GitHub Discussions**: For general questions and feature requests
- **Twitter**: [@yourhandle](https://twitter.com/yourhandle) for quick updates
- **Email**: [danavchaudhary@gmail.com](mailto:danavchaudhary@gmail.com)

## 🗺️ Roadmap

### Planned Features

| Feature | Description | Status |
|---------|-------------|--------|
| **Password Strength Meter** | Visual indicator of password strength | ⏳ Planning |
| **Password Manager Integration** | Export to popular password managers | 🚧 In Progress |
| **Multi-device Sync** | Sync generated passwords across devices | 💡 Idea |
| **Biometric Authentication** | Use fingerprint/face ID for secure access | 💡 Idea |
| **Local Storage** | Save frequently used passwords | 💡 Idea |
| **Dark Mode Toggle** | Manual dark/light mode selection | ✅ Implemented (via prefers-color-scheme) |

### Known Issues

| Issue | Description | Priority |
|-------|-------------|----------|
| **Mobile UI** | Some layout issues on very small screens | Medium |
| **Copy Button** | Copy button doesn't work in some browsers | Low |
| **Accessibility** | Need to improve ARIA labels and keyboard navigation | High |

### Future Improvements

1. Add more character sets (e.g., symbols from different languages)
2. Implement password complexity analysis
3. Add a "generate password for me" button that fills a form field
4. Create a desktop application version
5. Add unit tests for the JavaScript functionality

---

## 🎉 Get Involved!

We'd love to see what you create with this password generator! Here are some ideas to get started:

1. **Create a custom version** for your company or project
2. **Integrate with your app** as a secure password generation component
3. **Translate the interface** into other languages
4. **Add new features** and submit a pull request
5. **Share your use case** in the discussions section

Every contribution helps make this tool more useful for everyone. Let's build something amazing together!

---

## 📢 Join the Community

Stay updated with the latest developments:

- [GitHub Repository](https://github.com/akash6595/password-generator)

Together, we can make password management easier and more secure for everyone!

---
```
