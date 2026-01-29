# Contributing to Shield AI Landing Page

Thank you for considering contributing to this project! This document provides guidelines and instructions for contributing.

## 🚀 Quick Start

1. **Fork** this repository
2. **Clone** your fork locally
3. **Create a branch** for your feature/fix
4. **Make your changes**
5. **Test thoroughly**
6. **Submit a pull request**

## 📋 Development Setup

### Prerequisites
- Node.js 18.x or higher
- npm 9.x or higher
- Git

### Installation
```bash
git clone https://github.com/YOUR_USERNAME/shield-ai-landing.git
cd shield-ai-landing
npm install
npm run dev
```

## 🎯 How to Contribute

### Reporting Bugs
- Use GitHub Issues
- Include browser version and OS
- Provide steps to reproduce
- Include screenshots if applicable

### Suggesting Features
- Open a GitHub Issue with the "enhancement" label
- Describe the feature and use case
- Explain why it would be valuable

### Code Contributions

#### Branch Naming
- `feature/description` - New features
- `fix/description` - Bug fixes
- `docs/description` - Documentation updates
- `refactor/description` - Code refactoring

#### Commit Messages
Follow conventional commits format:
```
type(scope): description

[optional body]
[optional footer]
```

Examples:
- `feat(animations): add new shape transition effect`
- `fix(carousel): resolve scroll issue on mobile`
- `docs(readme): update deployment instructions`

## 🧪 Testing

Before submitting a PR:

1. **Test locally**
   ```bash
   npm run dev
   ```

2. **Build successfully**
   ```bash
   npm run build
   ```

3. **Type checking**
   ```bash
   npm run astro check
   ```

4. **Test on multiple browsers**
   - Chrome
   - Firefox
   - Safari
   - Mobile browsers

## 📝 Code Style

### TypeScript
- Use TypeScript for all new components
- Define proper types/interfaces
- Avoid `any` types

### React Components
- Use functional components
- Utilize hooks appropriately
- Keep components focused and small

### Styling
- Use Tailwind CSS utility classes
- Follow existing naming conventions
- Maintain responsive design

### Comments
- Add comments for complex logic
- Use JSDoc for functions
- Keep comments up-to-date

## 🔍 Pull Request Process

1. **Update documentation** if needed
2. **Test all changes** thoroughly
3. **Update README.md** with relevant changes
4. **Ensure build passes** (`npm run build`)
5. **Request review** from maintainers

### PR Template
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Refactoring

## Testing
- [ ] Tested locally
- [ ] Build successful
- [ ] Tested on mobile
- [ ] Type checking passes

## Screenshots (if applicable)
Add screenshots here
```

## 📚 Resources

- [Astro Documentation](https://docs.astro.build)
- [React Documentation](https://react.dev)
- [GSAP Documentation](https://greensock.com/docs/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)

## 📧 Questions?

Open an issue or reach out to the maintainer.

Thank you for contributing! 🎉
