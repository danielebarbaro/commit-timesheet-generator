# Git Timesheet Generator

📅 Automatically generate professional timesheets from your Git commit history.

## Overview

Transform your Git commits into beautifully formatted monthly timesheets. Perfect for freelancers, consultants, and teams that need to track and report development activities.

## Features

- ✅ **Automatic time tracking** from commit timestamps
- 📊 **Daily activity summaries** with time ranges
- 🏷️ **Intelligent commit categorization** (features, fixes, refactoring, etc.)
- 📈 **Monthly macro-activity reports** with commit counts
- 🎨 **Clean Markdown output** ready for clients or project managers
- 🌍 **Cross-platform** (macOS & Linux)

## Installation

### Quick Install

```bash
curl -o git-timesheet https://raw.githubusercontent.com/danielebarbaro/commit-timesheet-generator/main/git-timesheet
chmod +x git-timesheet
```

### Manual Install

1. Download `git-timesheet`
2. Make it executable: `chmod +x git-timesheet`
3. Optionally move to PATH: `sudo mv git-timesheet /usr/local/bin/`

## Usage

### Basic Usage

Navigate to your Git repository and run:

```bash
./git-timesheet
```

This generates timesheets for the current year using your Git author name.

### Custom Author and Year

```bash
./git-timesheet "Jane Doe" 2024
```

### Parameters

- **Author** (default: `git config user.name`): The commit author to track
- **Year** (default: current year): The year to generate reports for

## Output

The script creates a `timesheets/` directory with one Markdown file per month:

```
timesheets/
├── 2025-01-January.md
├── 2025-02-February.md
└── 2025-03-March.md
```

### Example Output

See [`examples/sample-output.md`](examples/sample-output.md) for a complete example.

```markdown
# Timesheet June 2025
**Developer**: Jane Doe

---

## Monday 09 June
**Time range**: 09:15 - 18:30

**Activities**:
- User authentication module
- Fix password validation bug
- Refactor login component
- Add unit tests for auth service

---

## Monthly Summary

**Working days**: 22

**Macro-activities**:
- Feature implementation: authentication (12 commits)
- Bug fix: validation (5 commits)
- Code refactoring: components (8 commits)
- Testing: auth (4 commits)

**Total commits**: 89
```

## Commit Message Format

For best results, use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(scope): Add new feature
fix(scope): Fix bug
refactor(scope): Refactor code
chore(scope): Update dependencies
docs(scope): Update documentation
test(scope): Add tests
```

The script recognizes these types and categorizes them automatically:

| Commit Type | Category |
|-------------|----------|
| `feat` | Feature implementation |
| `fix` | Bug fix |
| `refactor` | Code refactoring |
| `chore` | Maintenance |
| `test` | Testing |
| `docs` | Documentation |
| `ci` | CI/CD pipeline |
| `perf` | Performance optimization |
| `style` | Code style |
| `build` | Build system |

## Requirements

- **Git** repository with commit history
- **Bash** 3.2+ (macOS/Linux default)
- **date** command (GNU or BSD)

## Use Cases

- 📋 **Client reporting**: Generate monthly activity reports for clients
- 💼 **Freelance invoicing**: Track billable hours and activities
- 👥 **Team reporting**: Summarize developer contributions
- 📊 **Project retrospectives**: Review what was accomplished each month
- ⏱️ **Time tracking**: Automatic time logging from development work

## Tips

### Improve Accuracy

1. **Commit regularly** throughout your workday
2. **Use descriptive commit messages** with scopes
3. **Follow conventional commits** format
4. **First and last commits** define your working hours

### Multiple Projects

Run the script in each project repository to generate separate timesheets.

### Combining Reports

To merge timesheets from multiple projects, concatenate the daily sections manually or use a text editor.

## Customization

The script is easy to customize:

- **Time format**: Edit the time range display section
- **Activity grouping**: Modify commit categorization logic in `translate_commit_type()`
- **Output format**: Adjust Markdown structure in `generate_month_timesheet()`
- **Colors**: Change terminal output colors at the top of the script

## Limitations

- Only tracks committed work (uncommitted changes are not included)
- Time ranges based on first/last commit (breaks not tracked)
- Requires Git repository with commit history
- Month/day names follow system locale (typically English)

## Troubleshooting

### "Not a Git repository" error

Make sure you run the script from inside a Git repository:

```bash
cd /path/to/your/git/repo
./git-timesheet
```

### "No commits found" error

Check that:
- You have commits in the specified year
- The author name matches your Git config: `git config user.name`
- Try specifying the author explicitly: `./git-timesheet "Your Name"`

### Date command issues

The script supports both BSD (macOS) and GNU (Linux) date commands. If you encounter issues, ensure your system has the `date` command available.

## Contributing

Contributions are welcome! Feel free to:

- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

## License

MIT License - See [LICENSE](LICENSE) file for details.

## Author

Created with ❤️ for developers who need better time tracking.

---

⭐ If this tool helps you, consider starring the repository!

## Related Projects

- [Conventional Commits](https://www.conventionalcommits.org/) - Commit message convention
- [Git Log](https://git-scm.com/docs/git-log) - Git documentation

