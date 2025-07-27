# Contributing to E-Commerce Customer Analytics

🎉 **Thank you for your interest in contributing to this project!** 🎉

We welcome contributions from the community and are pleased to have you join us. This document provides guidelines and information about contributing to the E-Commerce Customer Analytics project.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Submitting Changes](#submitting-changes)

## 🤝 Code of Conduct

This project adheres to a Code of Conduct that we expect all contributors to follow:

- **Be respectful** and inclusive in all interactions
- **Be collaborative** and help others learn
- **Be constructive** in feedback and discussions
- **Focus on the project goals** and user needs

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- Git
- Basic understanding of data analytics and pandas
- Familiarity with matplotlib/seaborn for visualizations

### Fork and Clone

1. **Fork** the repository on GitHub
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/yourusername/ecommerce-customer-analytics.git
   cd ecommerce-customer-analytics
   ```

3. **Add upstream** remote:
   ```bash
   git remote add upstream https://github.com/originalowner/ecommerce-customer-analytics.git
   ```

## 💡 How to Contribute

### Types of Contributions

We welcome several types of contributions:

#### 🐛 **Bug Reports**
- Use the GitHub issue tracker
- Include detailed reproduction steps
- Provide system information and Python version
- Include error messages and stack traces

#### ✨ **Feature Requests**
- Describe the business value and use case
- Explain the expected behavior
- Consider implementation complexity
- Discuss with maintainers before starting work

#### 📊 **Analytics Enhancements**
- New customer segmentation methods
- Additional visualization types
- Performance optimizations
- Statistical analysis improvements

#### 📚 **Documentation**
- README improvements
- Code comments and docstrings
- Tutorial and example additions
- Methodology documentation

#### 🧪 **Testing**
- Unit tests for analytics functions
- Integration tests for data pipelines
- Performance benchmarks
- Data validation tests

## 🛠️ Development Setup

### 1. Create Virtual Environment
```bash
python -m venv ecommerce_analytics_env
source ecommerce_analytics_env/bin/activate  # On Windows: ecommerce_analytics_env\Scripts\activate
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
pip install -r requirements-dev.txt  # Development dependencies
```

### 3. Install Pre-commit Hooks (Optional)
```bash
pre-commit install
```

### 4. Verify Installation
```bash
python ecommerce_analytics.py
```

## 📏 Coding Standards

### Python Style Guide

We follow **PEP 8** with some project-specific guidelines:

#### **General Principles**
- Use meaningful variable and function names
- Keep functions focused and small (< 50 lines)
- Add docstrings for all functions and classes
- Use type hints where appropriate

#### **Analytics Code Style**
```python
def calculate_rfm_scores(transactions_df: pd.DataFrame, 
                        current_date: datetime) -> pd.DataFrame:
    """
    Calculate RFM (Recency, Frequency, Monetary) scores for customers.
    
    Args:
        transactions_df: DataFrame containing transaction data
        current_date: Reference date for recency calculation
        
    Returns:
        DataFrame with RFM scores for each customer
    """
    # Implementation here
    pass
```

#### **Data Processing Standards**
- Always validate input data
- Handle missing values explicitly
- Use descriptive column names
- Include data quality checks

#### **Visualization Standards**
- Use consistent color schemes
- Include proper titles and labels
- Add value annotations where helpful
- Export high-resolution images (300 DPI)

### File Organization

```
src/
├── analytics/
│   ├── __init__.py
│   ├── rfm_analysis.py      # RFM calculation functions
│   ├── revenue_analysis.py  # Revenue analytics
│   └── churn_analysis.py    # Churn prediction
├── visualization/
│   ├── __init__.py
│   ├── dashboard.py         # Main dashboard creation
│   └── charts.py           # Individual chart functions
└── utils/
    ├── __init__.py
    ├── data_generation.py   # Synthetic data creation
    └── helpers.py          # Utility functions
```

## 🧪 Testing Guidelines

### Running Tests
```bash
# Run all tests
pytest

# Run specific test file
pytest tests/test_analytics.py

# Run with coverage
pytest --cov=src
```

### Writing Tests

#### **Analytics Function Tests**
```python
import pytest
import pandas as pd
from src.analytics.rfm_analysis import calculate_rfm_scores

def test_rfm_calculation():
    # Create sample data
    sample_data = pd.DataFrame({
        'customer_id': ['C001', 'C002'],
        'transaction_date': ['2024-01-01', '2024-01-15'],
        'amount': [100.0, 200.0]
    })
    
    # Test function
    result = calculate_rfm_scores(sample_data, pd.Timestamp('2024-02-01'))
    
    # Assertions
    assert len(result) == 2
    assert 'recency' in result.columns
    assert result['recency'].min() >= 0
```

#### **Data Validation Tests**
```python
def test_data_quality():
    """Test that generated data meets quality standards."""
    customers_df, transactions_df = generate_sample_data(1000, 5000)
    
    # Test data integrity
    assert len(customers_df) == 1000
    assert len(transactions_df) == 5000
    assert transactions_df['amount'].min() > 0
    assert transactions_df['customer_id'].isin(customers_df['customer_id']).all()
```

## 📝 Submitting Changes

### Branch Naming Convention

- `feature/description` - New features
- `bugfix/description` - Bug fixes
- `docs/description` - Documentation updates
- `refactor/description` - Code refactoring

### Commit Message Format

```
type(scope): brief description

Detailed explanation of what changed and why.

- Include bullet points for multiple changes
- Reference issue numbers: Fixes #123
- Keep first line under 72 characters
```

**Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

### Pull Request Process

1. **Create Feature Branch**
   ```bash
   git checkout -b feature/customer-lifetime-value
   ```

2. **Make Changes**
   - Write clean, documented code
   - Add tests for new functionality
   - Update documentation as needed

3. **Test Locally**
   ```bash
   pytest
   python ecommerce_analytics.py  # Full integration test
   ```

4. **Commit Changes**
   ```bash
   git add .
   git commit -m "feat(analytics): add customer lifetime value prediction"
   ```

5. **Push to Fork**
   ```bash
   git push origin feature/customer-lifetime-value
   ```

6. **Create Pull Request**
   - Use the GitHub interface
   - Fill out the PR template
   - Link related issues
   - Request review from maintainers

### Pull Request Template

```markdown
## Description
Brief description of changes and motivation.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Performance improvement

## Testing
- [ ] Tests added/updated
- [ ] All tests pass
- [ ] Manual testing completed

## Screenshots (if applicable)
Include before/after visualizations.

## Checklist
- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No breaking changes (or documented)
```

## 🏷️ Release Process

### Version Numbering
We follow [Semantic Versioning](https://semver.org/):
- `MAJOR.MINOR.PATCH`
- `MAJOR`: Breaking changes
- `MINOR`: New features (backward compatible)
- `PATCH`: Bug fixes

### Release Checklist
1. Update version numbers
2. Update CHANGELOG.md
3. Run full test suite
4. Create release branch
5. Submit release PR
6. Tag release after merge

## 🆘 Getting Help

### Communication Channels
- **GitHub Issues**: Bug reports and feature requests
- **GitHub Discussions**: General questions and ideas
- **Email**: Direct contact with maintainers

### Documentation Resources
- [Analytics Methodology](docs/methodology.md)
- [Technical Guide](docs/technical_guide.md)
- [Visualization Guide](docs/visualization_guide.md)

## 🎯 Project Roadmap

### Upcoming Features
- Machine learning models for churn prediction
- Real-time analytics dashboard
- A/B testing framework
- Advanced cohort analysis
- Integration with popular e-commerce platforms

### Long-term Goals
- Cloud deployment options
- Multi-language support
- Enterprise features
- Community marketplace integrations

---

**Thank you for contributing to E-Commerce Customer Analytics!** 🚀

Your contributions help make this project better for everyone in the data analytics community.
