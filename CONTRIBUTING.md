# Contributing to Advanced Benchmark Suite

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing to the project.

## 🤝 Code of Conduct

Be respectful, inclusive, and constructive. We're all here to make performance benchmarking better.

---

## 📋 How to Contribute

### 1. Reporting Bugs

Found a bug? Please open an issue with:

- **Clear title** - What's broken?
- **Reproduction steps** - How to recreate the bug
- **Expected behavior** - What should happen?
- **Actual behavior** - What actually happens?
- **Environment** - Device, browser, OS, version
- **Screenshots/logs** - If applicable

**Example:**
```
Title: GPU Benchmark crashes on Firefox 115

Steps to Reproduce:
1. Open gpu_accelerated_benchmark.html
2. Set Matrix Size to 1024
3. Click "RUN BOTH"
4. After ~5 seconds: browser crashes

Expected: Benchmark completes normally
Actual: Firefox crashes with "Out of memory" error

Environment:
- Device: MacBook Pro 14"
- OS: macOS 13.5
- Browser: Firefox 115.0
```

### 2. Suggesting Features

Have an idea? Create an issue with:

- **Clear description** - What feature?
- **Use case** - Why is it needed?
- **Proposed solution** - How would it work?
- **Alternatives considered** - Other approaches?

**Example:**
```
Title: Add WebGPU support

Description:
WebGPU offers significant performance improvements over WebGL, 
especially for compute operations like matrix multiplication.

Use Case:
Users with WebGPU-capable devices could see 2-5x performance 
improvements in GPU benchmarks.

Proposed Solution:
Add WebGPU backend alongside existing WebGL implementation, 
with automatic fallback to WebGL.

Alternatives:
- Stick with WebGL only (limits performance ceiling)
- Require WebGPU (breaks compatibility)
```

### 3. Submitting Pull Requests

#### Before You Start

1. **Fork** the repository
2. **Clone** your fork: `git clone https://github.com/yourname/advanced-benchmark.git`
3. **Create branch**: `git checkout -b feature/your-feature-name`
4. **Install dependencies** (if any): `npm install`

#### During Development

Follow these standards:

**Code Style:**
- Use consistent indentation (2 spaces)
- Use descriptive variable names
- Add comments for complex logic
- Keep functions focused and small

**Example:**
```javascript
// ✅ Good
function calculateFPS(frameCount, elapsedSeconds) {
  // Average frames per second
  return frameCount / elapsedSeconds;
}

// ❌ Avoid
function calc(n, t) {
  return n / t;
}
```

**File Organization:**
```
- HTML files: *.html in root or relevant folder
- Guides: *.md files in respective directories
- Tests: Create tests/ folder if adding new features
- Assets: Keep images/resources organized
```

**Comments & Documentation:**
```javascript
// For functions:
/**
 * Calculates normalized FPS score (0-100)
 * @param {number} fps - Measured frames per second
 * @param {number} referenceType - Reference value
 * @returns {number} Normalized score 0-100
 */
function normalizeFPS(fps, referenceType) {
  // Implementation
}

// For complex logic:
// Ensure FPS doesn't exceed physical monitor refresh rate
const cappedFPS = Math.min(fps, screen.refreshRate);
```

#### Testing

Before submitting, test your changes:

1. **All benchmark modes** - Run each benchmark type
2. **Multiple browsers** - Chrome, Firefox, Safari
3. **Different devices** - Desktop, laptop, tablet (if possible)
4. **Edge cases** - Very low/high FPS, large matrices, etc.

**Testing Checklist:**
```
- [ ] GPU Benchmark runs without errors
- [ ] Graphics Benchmark completes all scenes
- [ ] Scoring Benchmark shows detailed breakdown
- [ ] Mobile browser responsive (if applicable)
- [ ] No console errors
- [ ] Results are reproducible
- [ ] Performance hasn't degraded
```

#### Making the Pull Request

```bash
# Commit with clear message
git add .
git commit -m "Add WebGPU support for matrix multiplication

- Implement WebGPU compute shader
- Add automatic fallback to WebGL
- Performance improvement: ~3x for large matrices
- Tested on Chrome 121, Firefox 115"

# Push to your fork
git push origin feature/your-feature-name
```

**PR Template:**

```markdown
## Description
Brief explanation of what this PR does.

## Related Issues
Closes #123

## Changes Made
- [ ] Feature 1
- [ ] Feature 2
- [ ] Documentation update

## Testing
- [ ] Tested on Chrome
- [ ] Tested on Firefox
- [ ] Tested on Safari
- [ ] All benchmarks run without errors

## Screenshots
[If applicable]

## Performance Impact
- [Describe any performance changes]

## Checklist
- [ ] Code follows style guidelines
- [ ] Documentation is updated
- [ ] No breaking changes
- [ ] Tests added/updated
```

---

## 🏗️ Development Setup

### Prerequisites

- Modern web browser (Chrome 120+, Firefox 115+, Safari 15+)
- Text editor (VS Code, Sublime, etc.)
- Git

### No build step required!

This project uses plain HTML/JavaScript/CSS with no build tools. Just edit files and test in your browser.

### Local Development

```bash
# Clone the repository
git clone https://github.com/yourusername/advanced-benchmark.git
cd advanced-benchmark

# Start a local server (Python 3)
python -m http.server 8000

# Or using Node.js http-server
npm install -g http-server
http-server

# Open http://localhost:8000 in your browser
```

---

## 📝 Documentation Guidelines

### When to update docs

- Adding a new feature
- Changing behavior
- Adding new test scenes
- Improving scoring methodology
- Fixing misleading information

### Documentation standards

**Markdown Format:**
```markdown
# Main Heading
## Subheading
### Sub-subheading

**Bold text** and *italic text*

- Bullet point
- Another point

1. Numbered item
2. Second item

[Link text](url)

`inline code`

```code block
Multiple lines
```
```

**Example Docs:**
- Keep language simple and clear
- Explain the "why" not just the "what"
- Use code examples when relevant
- Include diagrams if helpful (ASCII art OK)
- Proofread before committing

---

## 🔍 Code Review Process

All PRs require review by a maintainer:

1. **Automated checks** - Code style, tests
2. **Manual review** - Functionality, performance, documentation
3. **Feedback** - Suggestions for improvement
4. **Approval** - Merge when approved

Be patient - reviews might take a few days.

---

## 🐛 Reporting Security Issues

Do NOT open a public issue for security vulnerabilities.

Email security concerns to: [your-email@example.com]

Please include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if applicable)

We'll respond within 48 hours.

---

## 💡 Contribution Ideas

### Easy (Good for Beginners)

- [ ] Fix typos or improve wording in docs
- [ ] Add browser compatibility notes
- [ ] Improve code comments
- [ ] Add new test device results
- [ ] Create usage examples

### Medium (Some Experience)

- [ ] Add new benchmark scene
- [ ] Implement custom scoring weights
- [ ] Improve mobile responsiveness
- [ ] Add dark mode toggle
- [ ] Optimize rendering performance

### Advanced (Experienced)

- [ ] Implement WebGPU support
- [ ] Add multi-threaded benchmarking
- [ ] Create cloud results synchronization
- [ ] Implement WASM acceleration
- [ ] Add ML/AI performance metrics

---

## 🎓 Learning Resources

### Understanding the Codebase

1. **Start here**: Read README.md
2. **Graphics benchmark**: fox_benchmark_advanced.html (~450 lines)
3. **GPU acceleration**: advanced_webgl_benchmark.html (~400 lines)
4. **Scoring system**: transparent_scoring_benchmark.html (~600 lines)
5. **Guides**: Read the *.md files for deep dives

### Key Concepts

- **Three.js**: 3D graphics library
- **WebGL**: GPU API for web browsers
- **Scoring normalization**: Converting measurements to 0-100 scale
- **Performance profiling**: Measuring FPS, draw calls, memory

### Helpful Resources

- [Three.js Docs](https://threejs.org/docs/)
- [WebGL Spec](https://www.khronos.org/webgl/)
- [MDN Performance](https://developer.mozilla.org/en-US/docs/Web/Performance)
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)

---

## 📊 Commit Message Guidelines

Use clear, descriptive commit messages:

```
Format: <type>: <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `perf`: Performance improvement
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance

**Example:**
```
feat: Add WebGPU compute shader support

Implement WebGPU backend for matrix multiplication with automatic
WebGL fallback. Provides ~3x performance improvement on supported devices.

- Add WebGPU shader compilation
- Implement feature detection
- Add fallback error handling
- Update documentation

Closes #45
```

---

## ✅ Checklist for Contributors

Before submitting your PR:

- [ ] Fork and clone the repo
- [ ] Create a descriptive branch name
- [ ] Make your changes
- [ ] Test on multiple browsers
- [ ] Update documentation if needed
- [ ] Write clear commit messages
- [ ] Push to your fork
- [ ] Create PR with detailed description
- [ ] Respond to review feedback

---

## 🎉 Recognition

Contributors will be recognized in:
- [CONTRIBUTORS.md](CONTRIBUTORS.md)
- GitHub contributors page
- Release notes (for significant contributions)

Thank you for making this project better! 🚀

---

## 📞 Questions?

- Create a [GitHub Discussion](../../discussions)
- Check existing [Issues](../../issues)
- Review [Documentation](../../)

Happy contributing! 🎊
