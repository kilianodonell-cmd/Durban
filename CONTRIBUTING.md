# Contributing to Durban Housing Suitability Analysis

Thank you for your interest in contributing! This project follows **open science principles** to ensure transparency, reproducibility, and community collaboration.

## Ways to Contribute

### 1. **Report Issues**
- Found a bug? Data processing error? Documentation typo?
- Open an issue with:
  - Clear description of the problem
  - Steps to reproduce (if applicable)
  - Your environment (Colab vs. local, Python version, OS)
  - Error messages or screenshots

### 2. **Improve Documentation**
- Typo fixes, clarity improvements
- Additional examples or use cases
- Data source citations and links
- Troubleshooting guides

### 3. **Add or Improve Factors**
- Propose new factors for the analysis
- Suggest better data sources
- Improve scoring thresholds or buffer distances
- Test new factor combinations

### 4. **Code Contributions**
- Performance improvements
- New visualization options
- Better error handling
- Refactoring for readability

### 5. **Testing**
- Test on different environments (Windows, Mac, Linux)
- Test in both Colab and local modes
- Report compatibility issues

### 6. **Case Studies**
- Apply the analysis to new geographic areas
- Document results and lessons learned
- Share adaptations for different contexts

## Contribution Workflow

1. **Fork the repository** (or clone if you have push access)
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes**
   - Follow code style guidelines (see below)
   - Update documentation as needed
   - Test your changes in both Colab and locally
4. **Commit with clear messages**
   ```bash
   git commit -m "Add: brief description of changes"
   git commit -m "Fix: clear description of fix"
   git commit -m "Docs: update README with new section"
   ```
5. **Push to your branch**
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Open a Pull Request**
   - Describe what you changed and why
   - Mention any issues it resolves
   - Include test results (Colab and local)

## Code Guidelines

### Python Style
- Follow **PEP 8** conventions
- Use meaningful variable names (`suitability_raster` not `sr`)
- Add comments for complex logic
- Keep functions focused and documented

### Notebooks
- Add markdown headers with `========` or `────` dividers
- Comment each major section
- Include docstrings for helper functions
- Clean outputs before committing (Cell → Clear All Outputs)

### Reproducibility
- All parameters in `config.json` or Cell 2
- No hardcoded paths or magic numbers
- Clear logging/print statements for debugging
- Document assumptions about input data

### Testing
- Test new code in both **Google Colab** and **local environments**
- Verify with sample or test data
- Check for errors with missing data files
- Document any environment-specific issues

## Documentation Standards

- **README.md**: Project overview, quick start, troubleshooting
- **SETUP.md**: Installation and setup instructions
- **config.json**: All configurable parameters in valid JSON
- **Cell docstrings**: What each cell does and its inputs/outputs
- **Comments**: Why something is done, not just what

### Adding Data Sources

When documenting a new data source, include:
```markdown
| Layer | Source | License | URL | Notes |
|-------|--------|---------|-----|-------|
| My Layer | Provider Name | CC-BY 4.0 | https://... | Pre-processed, 1-5 scores |
```

## Commit Message Convention

```
Type: Brief description

- Bullet point details
- Another detail

Resolves #123 (if applicable)
```

**Types:**
- `Add:` — New feature, factor, or capability
- `Fix:` — Bug fix or correction
- `Docs:` — Documentation improvements
- `Refactor:` — Code reorganization (no functional change)
- `Test:` — Testing improvements
- `Perf:` — Performance improvements
- `CI:` — Build or CI/CD changes

## Questions or Discussions?

- **How-to questions**: Open an issue tagged "question"
- **General discussion**: Use Discussions (if enabled) or GitHub Issues
- **Methodology questions**: Tag with "methodology" for expert review
- **Data source issues**: Tag with "data" for data specialist input

## Licensing

By contributing, you agree that your contributions are licensed under the same license as this project (see LICENSE file). We welcome contributions under open licenses only.

## Behavior Standards

This project adheres to open science values:
- **Transparent**: Methods, assumptions, and limitations are explicit
- **Reproducible**: Others can replicate your work exactly
- **Documented**: Every decision and assumption is recorded
- **Collaborative**: Respect all contributors and users
- **Respectful**: No discrimination, harassment, or hostility

## Attribution

Contributors will be acknowledged in:
- Project README
- Release notes
- Contributor list (if maintained)

Make sure your Git username reflects how you'd like to be credited.

## Questions?

- Email: [maintainer email]
- Open an issue with the "help wanted" tag
- Check existing issues/discussions for answers

---

**Thank you for contributing to open science! 🎓📊**
