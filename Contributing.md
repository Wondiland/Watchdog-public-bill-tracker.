# Contributing to Watchdog

Thanks for your interest in making government more transparent! Here's how you can help.

---

## 🎯 How to Contribute

There are many ways to contribute, regardless of your skill level:

### 1. **Code Contributions**
- Fix bugs or implement features
- Improve performance or refactor code
- Add tests or documentation

### 2. **Data & Research**
- Document government API endpoints
- Research data formats from different jurisdictions
- Test data scrapers for accuracy

### 3. **Design & UX**
- Improve the interface
- Create mockups for new features
- Make it more accessible

### 4. **Documentation**
- Write guides for users or developers
- Improve README clarity
- Create video tutorials

### 5. **Community**
- Answer questions in issues
- Help review pull requests
- Share the project

---

## 🚀 Getting Started

### Prerequisites

```bash
# You need Node.js 16+ and npm
node --version
npm --version
```

### Setup

```bash
# 1. Fork this repo on GitHub
# 2. Clone your fork
git clone https://github.com/YOUR-USERNAME/watchdog.git
cd watchdog

# 3. Install dependencies
npm install

# 4. Create a branch
git checkout -b feature/your-feature-name

# 5. Run the dev server
npm start

# 6. Make your changes
# 7. Test them
npm test

# 8. Commit and push
git add .
git commit -m "Add feature: your description"
git push origin feature/your-feature-name

# 9. Open a Pull Request on GitHub
```

---

## 🎨 Code Style

- **TypeScript preferred** for type safety
- **Functional style** where possible (pure functions, immutability)
- **Clear naming** — `analyzeBill()` not `doStuff()`
- **Comments** for complex logic only
- **Keep it simple** — readability over cleverness

### Example: Good vs. Bad

**Good:**
```typescript
function isSuspiciousTiming(passedDate: Date): boolean {
  const hour = passedDate.getHours();
  return hour >= 22 || hour < 6;
}
```

**Bad:**
```typescript
function chk(d) {
  return d.getHours() >= 22 || d.getHours() < 6 ? true : false;
}
```

---

## 🧪 Testing

We use **Jest** for testing. All detection logic should be tested.

```bash
# Run all tests
npm test

# Run tests in watch mode
npm test -- --watch

# Run tests with coverage
npm test -- --coverage
```

### Writing Tests

```typescript
import { analyzeBill } from './analyzer';

describe('analyzeBill', () => {
  it('flags late-night votes', () => {
    const bill = {
      id: 'test-001',
      passedDate: '2024-10-28T23:30:00Z', // 11:30 PM
      introducedDate: '2024-10-20T10:00:00Z'
    };
    
    const flags = analyzeBill(bill);
    
    expect(flags).toContainEqual(
      expect.objectContaining({ type: 'late-night' })
    );
  });
});
```

---

## 📋 What Needs Doing

Check the **[Issues](https://github.com/yourusername/watchdog/issues)** page for current tasks.

### Priority Areas

**High Priority:**
1. **Government API Integration** — Connect to real data feeds
2. **Backend Development** — Build scraper and database
3. **Email Notifications** — Daily digests and alerts

**Medium Priority:**
4. **More Jurisdictions** — Add NSW, VIC, SA, etc.
5. **User Accounts** — Save watchlists and preferences
6. **Mobile Optimization** — Better responsive design

**Low Priority:**
7. **Historical Data** — Trend analysis over time
8. **Public API** — Let researchers access our data
9. **Internationalization** — Support other countries

---

## 🔧 Technical Priorities

### 1. Government API Integration

**What we need:**
- Scrapers for Federal Register of Legislation
- Scrapers for Parliament of Australia bills/Hansard
- Scrapers for state parliaments (QLD first)

**Skills needed:** Python or Node.js, API consumption, HTML parsing

**Where to start:**
- Check `server/scrapers/` directory (create it)
- Document the API endpoints you're using
- Write tests with sample data first

**Example structure:**
```python
# server/scrapers/federal_register.py

class FederalRegisterScraper:
    def fetch_recent_bills(self, since_date):
        """Fetch bills introduced since given date"""
        # Implementation here
        pass
    
    def parse_bill_details(self, bill_url):
        """Extract bill metadata and content"""
        # Implementation here
        pass
```

### 2. Backend API

**What we need:**
- REST API to serve bill data to frontend
- Database schema for bills, flags, users
- Scheduled jobs to run scrapers

**Skills needed:** Python/FastAPI or Node.js/Express, PostgreSQL

**Where to start:**
- Design database schema (see below)
- Create `/api/bills` endpoint
- Document API with OpenAPI/Swagger

**Database Schema (Draft):**
```sql
CREATE TABLE bills (
  id VARCHAR(50) PRIMARY KEY,
  title TEXT NOT NULL,
  jurisdiction VARCHAR(50),
  introduced_date TIMESTAMP,
  passed_date TIMESTAMP,
  text_change_percent INTEGER,
  summary TEXT,
  source_url TEXT,
  status VARCHAR(20),
  votes_for INTEGER,
  votes_against INTEGER,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE flags (
  id SERIAL PRIMARY KEY,
  bill_id VARCHAR(50) REFERENCES bills(id),
  flag_type VARCHAR(20),
  severity VARCHAR(10),
  message TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE,
  notification_prefs JSONB,
  created_at TIMESTAMP DEFAULT NOW()
);
```

### 3. Email Notifications

**What we need:**
- Integration with SendGrid or similar
- Daily digest email template
- User subscription management

**Skills needed:** Node.js/Python, SendGrid API, HTML emails

**Where to start:**
- Create email templates in `server/templates/`
- Build subscription form in frontend
- Test with your own email first

---

## 🐛 Bug Reports

Found a bug? Open an issue with:

1. **Clear title** — "Late-night detection fails for UTC times"
2. **Steps to reproduce** — How we can see the bug
3. **Expected vs. actual** — What should happen vs. what does happen
4. **Screenshots** — If relevant
5. **Environment** — Browser, OS, versions

---

## 💡 Feature Requests

Have an idea? Open an issue with:

1. **Problem statement** — What problem does this solve?
2. **Proposed solution** — How would it work?
3. **Alternatives considered** — What else could work?
4. **Mockups/examples** — If applicable

---

## 📝 Pull Request Guidelines

Before submitting a PR:

- [ ] Code follows the style guide
- [ ] Tests added for new features
- [ ] All tests pass (`npm test`)
- [ ] Documentation updated if needed
- [ ] Branch is up to date with `main`

**PR Description Template:**
```markdown
## What does this PR do?
Brief description

## Why is this needed?
Problem it solves

## How was it tested?
Steps you took to verify it works

## Screenshots (if applicable)
Add images

## Checklist
- [ ] Tests pass
- [ ] Documentation updated
- [ ] No breaking changes
```

---

## 🤔 Questions?

- **General questions:** Open a discussion on GitHub
- **Quick questions:** Email akka@duck.com
- **Bug reports:** Open an issue

---

## 👥 Community Guidelines

Be respectful, constructive, and collaborative. This is a civic tech project — we're all here to improve transparency and democracy.

**We do not tolerate:**
- Harassment or discrimination
- Spam or self-promotion
- Bad faith arguments

**We encourage:**
- Asking questions
- Helping others
- Constructive feedback
- Diverse perspectives

---

## 🙏 Recognition

All contributors will be:
- Listed in CONTRIBUTORS.md
- Credited in release notes
- Thanked publicly (if desired)

---

**Thank you for helping make government more transparent!** 🔍
