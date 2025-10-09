# Contributing to NCMH Mental Health Platform

Thank you for your interest in contributing to the National Center for Mental Health (NCMH) platform! This project aims to provide accessible, confidential mental health support to everyone in Saudi Arabia.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Development Guidelines](#development-guidelines)
- [Submission Process](#submission-process)
- [Translation Guidelines](#translation-guidelines)
- [Security and Privacy](#security-and-privacy)

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming, inclusive, and harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity and expression, level of experience, nationality, personal appearance, race, religion, or sexual identity and orientation.

### Expected Behavior

- Use welcoming and inclusive language
- Be respectful of differing viewpoints and experiences
- Gracefully accept constructive criticism
- Focus on what is best for the community
- Show empathy towards other community members
- Maintain confidentiality regarding sensitive mental health information

### Unacceptable Behavior

- Trolling, insulting/derogatory comments, and personal or political attacks
- Public or private harassment
- Publishing others' private information without explicit permission
- Sharing confidential mental health data
- Other conduct which could reasonably be considered inappropriate in a professional setting

## How Can I Contribute?

### Reporting Bugs

Before submitting a bug report:
- Check the existing issues to avoid duplicates
- Collect information about the bug (browser, OS, steps to reproduce)

When submitting a bug report, include:
- A clear and descriptive title
- Detailed steps to reproduce the issue
- Expected vs actual behavior
- Screenshots if applicable
- Browser console errors if relevant

**Note:** If you find a security vulnerability, please DO NOT open an issue. Email security@ncmh-platform.sa instead.

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion, include:

- A clear and descriptive title
- Detailed description of the proposed functionality
- Explanation of why this enhancement would be useful
- Possible implementation approach (if applicable)

### Your First Code Contribution

Unsure where to begin? Look for issues tagged with:
- `good-first-issue` - Simple issues for newcomers
- `help-wanted` - Issues that need assistance
- `translation` - Translation improvements needed
- `accessibility` - Accessibility enhancements

## Getting Started

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, or Edge)
- Text editor (VS Code, Sublime Text, etc.)
- Basic knowledge of HTML, CSS, and JavaScript
- Git installed on your system

### Local Setup

1. **Fork the Repository**
   ```bash
   # Click the "Fork" button on GitHub
   ```

2. **Clone Your Fork**
   ```bash
   git clone https://github.com/YOUR-USERNAME/ncmh-mental-health-platform.git
   cd ncmh-mental-health-platform
   ```

3. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

4. **Open the HTML File**
   - Simply open `index.html` in your browser
   - No build process required for basic development

5. **Make Your Changes**
   - Edit the files as needed
   - Test thoroughly in multiple browsers
   - Test both English and Arabic interfaces

## Development Guidelines

### Code Style

#### HTML
- Use semantic HTML5 elements
- Maintain proper indentation (4 spaces)
- Add ARIA labels for accessibility
- Keep structure clean and organized

#### CSS
- Use meaningful class names
- Follow existing naming conventions
- Comment complex styling rules
- Ensure RTL (Right-to-Left) compatibility for Arabic

#### JavaScript
- Use `var` for consistency with existing code
- Add comments for complex logic
- Maintain functional programming patterns
- Keep functions focused and single-purpose

### Accessibility Standards

This platform must be accessible to all users:

- Use semantic HTML elements
- Provide alt text for images
- Ensure keyboard navigation works
- Maintain sufficient color contrast (WCAG AA minimum)
- Test with screen readers
- Support browser zoom up to 200%

### Internationalization (i18n)

All user-facing text must be translatable:

```javascript
// Good
<button data-translate="continue">Continue</button>

// Bad
<button>Continue</button>
```

Add translations to both `english` and `arabic` sections of the `translations` object.

### Testing Checklist

Before submitting, test:

- [ ] All pages load correctly
- [ ] Navigation between pages works
- [ ] Forms validate properly
- [ ] Both English and Arabic interfaces work
- [ ] RTL layout displays correctly in Arabic
- [ ] Chatbot responds appropriately
- [ ] Emergency button functions properly
- [ ] Location search works
- [ ] Mobile responsive design works
- [ ] Browser console shows no errors

### Browser Support

Test your changes on:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Submission Process

### Pull Request Process

1. **Update Documentation**
   - Update README.md if adding features
   - Add comments to complex code
   - Update API.md if changing functionality

2. **Test Thoroughly**
   - Run through the testing checklist
   - Test on multiple browsers
   - Verify both language interfaces

3. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "feat: add descriptive commit message"
   ```

4. **Push to Your Fork**
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Create Pull Request**
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your fork and branch
   - Fill out the PR template completely

### Commit Message Guidelines

Follow conventional commits format:

- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation changes
- `style:` Code style changes (formatting, etc.)
- `refactor:` Code refactoring
- `test:` Adding tests
- `chore:` Maintenance tasks

Examples:
```
feat: add voice recording feature to sentiment analysis
fix: correct Arabic RTL layout on mobile devices
docs: update API documentation for chatbot responses
```

### Pull Request Template

When creating a PR, include:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Translation improvement

## Testing
- [ ] Tested on Chrome
- [ ] Tested on Firefox
- [ ] Tested on Safari
- [ ] Tested on mobile
- [ ] Tested Arabic interface
- [ ] Tested English interface

## Screenshots
(if applicable)

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have commented my code where necessary
- [ ] I have updated the documentation
- [ ] My changes generate no console errors
- [ ] I have tested both language interfaces
```

## Translation Guidelines

### Adding New Translations

1. Locate the `translations` object in the JavaScript section
2. Add your key-value pairs to both `english` and `arabic` objects
3. Use the `data-translate` attribute in HTML elements
4. Test both interfaces thoroughly

### Translation Best Practices

- Keep translations culturally appropriate
- Maintain the same tone and formality level
- Consider mental health terminology sensitivity
- Preserve formatting placeholders (like `<br>` tags)
- Have native speakers review translations

Example:
```javascript
var translations = {
    english: {
        welcome_message: 'Welcome to NCMH Platform'
    },
    arabic: {
        welcome_message: 'مرحباً بك في منصة المركز الوطني للصحة النفسية'
    }
};
```

## Security and Privacy

### Sensitive Information

- NEVER commit API keys, credentials, or secrets
- NEVER include real user data in examples
- NEVER expose internal system information

### Data Privacy

This platform handles sensitive mental health information:

- Do not log user input to console in production
- Maintain data minimization principles
- Follow GDPR and local privacy regulations
- Encrypt sensitive data in transit and at rest

### Reporting Security Issues

If you discover a security vulnerability:

1. **DO NOT** open a public issue
2. Email: security@ncmh-platform.sa
3. Include detailed information about the vulnerability
4. Allow reasonable time for response before disclosure

## Recognition

Contributors will be recognized in:
- Project README.md
- Release notes
- Annual contributor acknowledgments

## Questions?

- Open an issue with the `question` label
- Email: contribute@ncmh-platform.sa
- Join our community discussions

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (MIT License).

---

**Thank you for helping make mental health support more accessible!** 💚

*Last updated: October 2025*
