# Contributing to Interview-Prep

Thank you for your interest in contributing to this DSA problem museum! 🎉

## How to Contribute

### Adding New Problems

1. **Choose a Category**: Select appropriate folder (DSA, LeetCode, GeeksforGeeks, or Codeforces)
2. **Use the Template**: Copy `/Templates/problem-template.md` as a starting point
3. **Follow the Format**: Ensure all sections are filled out properly
4. **Optimize Solution**: Aim for O(n) or better time complexity
5. **Multiple Languages**: Provide solutions in at least Python, JavaScript, and Java

### Problem Requirements

Each problem submission should include:

- [ ] Clear problem statement
- [ ] Source and difficulty level
- [ ] Multiple examples with explanations
- [ ] Constraints listed
- [ ] Detailed approach explanation
- [ ] Key insights highlighted
- [ ] Step-by-step algorithm
- [ ] Complexity analysis (Time & Space)
- [ ] Solutions in multiple languages (Python, JavaScript, Java minimum)
- [ ] Related problems
- [ ] Relevant tags

### Code Quality Standards

#### Time Complexity
- ✅ **Preferred**: O(1), O(log n), O(n)
- ⚠️ **Acceptable**: O(n log n) when O(n) isn't feasible
- ❌ **Avoid**: O(n²) or worse unless it's the only solution

#### Code Style
- Use meaningful variable names
- Add comments for complex logic
- Follow language-specific conventions:
  - Python: PEP 8
  - JavaScript: ESLint standards
  - Java: Oracle conventions

#### Documentation
- Explain the approach before code
- Include complexity analysis
- Document edge cases
- Provide multiple test cases

### File Naming

Use kebab-case for file names:
- ✅ `two-sum.md`
- ✅ `longest-substring-without-repeating.md`
- ❌ `TwoSum.md`
- ❌ `two_sum.md`

### Folder Structure

```
Category/
├── Difficulty/ (for LeetCode, GFG, Codeforces)
│   └── problem-name.md
└── Topic/ (for DSA)
    └── problem-name.md
```

### Pull Request Process

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/add-problem-name`)
3. Add your problem following the template
4. Ensure all sections are complete
5. Test code solutions
6. Commit with clear message (`git commit -m 'Add: Problem Name'`)
7. Push to branch (`git push origin feature/add-problem-name`)
8. Open Pull Request with description

### Commit Message Format

```
Add: [Problem Name] - [Category]
Update: [Problem Name] - [What changed]
Fix: [Problem Name] - [What was fixed]
```

### Review Checklist

Before submitting, ensure:

- [ ] Problem follows template structure
- [ ] All sections are filled out
- [ ] Code solutions are tested
- [ ] Time complexity is O(n) or explained if not
- [ ] Multiple language implementations included
- [ ] Examples are clear and correct
- [ ] Related problems are relevant
- [ ] Tags are appropriate
- [ ] README updated if needed

## Types of Contributions

### Priority Areas
1. **New Problems**: Add problems with O(n) solutions
2. **Additional Languages**: Add C++, Go, Rust implementations
3. **Better Solutions**: Improve existing solutions
4. **Documentation**: Enhance explanations and examples
5. **Bug Fixes**: Correct errors in solutions or explanations

### What to Avoid
- Problems without optimal solutions
- Duplicate problems
- Incomplete submissions
- Code without explanations
- Solutions without complexity analysis

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on code quality and learning
- Help others understand solutions
- Give credit where due

## Questions?

Feel free to:
- Open an issue for discussion
- Ask questions in pull requests
- Suggest improvements to guidelines

## Recognition

Contributors will be acknowledged in:
- README.md contributors section
- Individual problem files (if significant contribution)

---

Thank you for helping build this learning resource! 🚀
