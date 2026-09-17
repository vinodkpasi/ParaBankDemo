# 🏦 ParaBank Demo - Playwright Automation Framework

![Playwright](https://img.shields.io/badge/Playwright-2EAD33?logo=playwright&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)
![Test Automation](https://img.shields.io/badge/Test%20Automation-UI%20E2E-blue)

## 📌 Overview

**ParaBankDemo** is a modern end-to-end UI automation framework built using **Playwright and TypeScript** for testing the ParaBank demo banking application.

The project demonstrates practical automation engineering concepts including:

- Page Object Model (POM)
- Playwright Test
- TypeScript
- End-to-end UI testing
- Reusable page components
- Test utilities
- Browser automation
- Test execution and reporting
- Screenshots, video and trace artifacts
- Maintainable test architecture

> ⚠️ ParaBank is a demo application and is **not a real banking institution**.

## 🎯 Objectives

The primary objectives of this project are to demonstrate how to build a maintainable Playwright automation framework for a web-based banking application.

The framework focuses on:

1. Automating critical user journeys.
2. Separating test logic from page interaction logic.
3. Creating reusable page objects.
4. Supporting scalable end-to-end testing.
5. Producing Playwright HTML reports.
6. Capturing screenshots, videos, and test artifacts.
7. Following TypeScript and automation best practices.

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| **Playwright** | Web UI automation |
| **Playwright Test** | Test runner and execution framework |
| **TypeScript** | Programming language |
| **Node.js** | JavaScript runtime |
| **npm** | Package management |
| **Page Object Model** | Test architecture |
| **HTML Reporter** | Test reporting |
| **Git/GitHub** | Source control |

## 🏗️ Project Structure

```text
ParaBankDemo/
│
├── Assignment/
│   └── Assignment related files
│
├── pages/
│   └── Page Object classes
│
├── tests/
│   └── e2e/
│       └── End-to-end test specifications
│
├── utils/
│   └── Reusable utilities and helper functions
│
├── playwright.config.ts
│   └── Playwright configuration
│
├── package.json
│   └── Project dependencies and npm scripts
│
├── tsconfig.json
│   └── TypeScript configuration
│
└── README.md
```

## 🧩 Framework Architecture

```text
                 ┌──────────────────────┐
                 │     Playwright       │
                 │      Test Runner     │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │     E2E Test Specs   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │      Page Objects    │
                 │        /pages        │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │     ParaBank Web     │
                 │     Application      │
                 └──────────────────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Reports / Artifacts  │
                 │ Screenshots / Video  │
                 └──────────────────────┘
```

### Benefits of POM

- Better code organization
- Reusable page interactions
- Reduced duplication
- Easier maintenance
- Improved readability
- Separation of test and UI logic
- Centralized locator maintenance

## 🧪 Test Coverage

Typical banking scenarios that can be automated include:

### Authentication

- User login
- Valid credentials
- Invalid credentials
- Login validation
- Logout

### Customer Management

- New customer registration
- User information validation
- Customer navigation

### Accounts

- View accounts
- Open a new account
- Account information validation
- Account navigation

### Transactions

- Transfer funds
- View transaction history
- Validate transaction details

### Bill Payment

- Pay a bill
- Enter payee information
- Submit payment
- Validate payment confirmation

### Loans

- Apply for a loan
- Enter loan information
- Submit loan request
- Validate loan response

> The exact scenarios executed depend on the test specifications currently present under `tests/e2e`.

## ⚙️ Prerequisites

Install:

- **Node.js**
- **npm**
- **Git**
- A supported browser such as Chromium, Firefox, or WebKit

Check Node.js:

```bash
node --version
```

Check npm:

```bash
npm --version
```

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/vinodkpasi/ParaBankDemo.git
cd ParaBankDemo
```

### 2. Install dependencies

```bash
npm install
```

### 3. Install Playwright browsers

```bash
npx playwright install
```

For Linux environments:

```bash
npx playwright install --with-deps
```

## ▶️ Running Tests

Run the complete test suite:

```bash
npx playwright test
```

Run tests in headed mode:

```bash
npx playwright test --headed
```

Run tests using Chromium:

```bash
npx playwright test --project=chromium
```

Run a specific test file:

```bash
npx playwright test tests/e2e/<test-file>.spec.ts
```

Run tests in debug mode:

```bash
npx playwright test --debug
```

## 🔎 Useful Playwright Commands

### List available tests

```bash
npx playwright test --list
```

### Run a test by title

```bash
npx playwright test -g "test title"
```

### Run with a single worker

```bash
npx playwright test --workers=1
```

### Run tests in parallel

```bash
npx playwright test --workers=4
```

## 📊 Test Reports

Open the Playwright HTML report:

```bash
npx playwright show-report
```

The report can provide:

- Test execution status
- Test duration
- Passed tests
- Failed tests
- Error details
- Screenshots
- Videos
- Trace information where configured

## 📸 Screenshots, Videos & Test Artifacts

Depending on the Playwright configuration and test outcome, execution artifacts can include:

```text
test-results/
├── screenshots
├── videos
└── traces
```

These artifacts are useful when troubleshooting failures locally or in CI/CD pipelines.

## 🔧 Playwright Configuration

The main configuration file is:

```text
playwright.config.ts
```

Typical configuration areas include:

- Test directory
- Browser projects
- Base URL
- Timeout
- Retry configuration
- Parallel execution
- Reporter configuration
- Screenshot configuration
- Video configuration
- Trace configuration

Example configuration pattern:

```typescript
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './tests',

  fullyParallel: true,

  use: {
    baseURL: 'https://parabank.parasoft.com/',
    trace: 'retain-on-failure',
    screenshot: 'only-on-failure',
    video: 'retain-on-failure',
  },

  projects: [
    {
      name: 'chromium',
      use: {
        ...devices['Desktop Chrome'],
      },
    },
  ],

  reporter: [
    ['html'],
    ['list'],
  ],
});
```

> The example above illustrates a recommended configuration pattern. Use the repository's actual `playwright.config.ts` as the source of truth for the current implementation.

## 🧱 Page Object Model

Page classes are maintained under:

```text
pages/
```

Example:

```typescript
import { Page, Locator } from '@playwright/test';

export class LoginPage {
  readonly page: Page;
  readonly username: Locator;
  readonly password: Locator;
  readonly loginButton: Locator;

  constructor(page: Page) {
    this.page = page;

    this.username = page.locator('#loginPanel input[name="username"]');
    this.password = page.locator('#loginPanel input[name="password"]');
    this.loginButton = page.locator('#loginPanel input[type="submit"]');
  }

  async login(username: string, password: string) {
    await this.username.fill(username);
    await this.password.fill(password);
    await this.loginButton.click();
  }
}
```

## 🧪 Example Test

```typescript
import { test, expect } from '@playwright/test';
import { LoginPage } from '../../pages/LoginPage';

test('User should be able to login successfully', async ({ page }) => {
  const loginPage = new LoginPage(page);

  await page.goto('/');

  await loginPage.login(
    process.env.TEST_USERNAME!,
    process.env.TEST_PASSWORD!
  );

  await expect(page).toHaveURL(/overview/);
});
```

## 🔐 Test Data & Credentials

Sensitive credentials should **not** be committed to GitHub.

Use environment variables when authentication data is required:

```text
TEST_USERNAME=your_username
TEST_PASSWORD=your_password
```

Add environment files to `.gitignore`:

```text
.env
.env.*
```

For CI/CD, use repository or pipeline secrets.

## 🌐 Browser Coverage

Playwright supports multiple browser engines:

```text
Chromium
Firefox
WebKit
```

Multi-browser projects can be configured in `playwright.config.ts`.

## ⚡ Parallel Execution

Playwright supports parallel execution to reduce regression execution time.

Example:

```bash
npx playwright test --workers=4
```

Parallel execution should be combined with independent test data and isolated test scenarios.

## 🛠️ Debugging

### Playwright Inspector

```bash
npx playwright test --debug
```

### Headed execution

```bash
npx playwright test --headed
```

### Trace Viewer

```bash
npx playwright show-trace test-results/<trace-file>.zip
```

Trace Viewer can help investigate:

- Locator failures
- Timing issues
- Navigation problems
- Network activity
- Screenshots
- DOM snapshots
- Action history

## 📁 Generated Files

Typical generated directories include:

```text
playwright-report/
test-results/
```

Recommended `.gitignore` entries:

```text
node_modules/
playwright-report/
test-results/
blob-report/
.env
```

## 🔄 CI/CD Integration

This framework can be integrated with:

- GitHub Actions
- Jenkins
- Azure DevOps
- GitLab CI/CD

Typical pipeline:

```text
Checkout
   ↓
Install Node.js
   ↓
npm ci
   ↓
Install Playwright
   ↓
Execute Tests
   ↓
Generate Report
   ↓
Upload Test Artifacts
```

Example GitHub Actions steps:

```yaml
- name: Install dependencies
  run: npm ci

- name: Install Playwright
  run: npx playwright install --with-deps

- name: Execute tests
  run: npx playwright test

- name: Upload Playwright report
  if: always()
  uses: actions/upload-artifact@v4
  with:
    name: playwright-report
    path: playwright-report/
```

## 📈 Automation Best Practices

### Maintainability

- Page Object Model
- Reusable utilities
- Centralized configuration
- Meaningful test names
- Stable locators

### Reliability

- Explicit assertions
- Proper synchronization
- Independent test cases
- Controlled test data
- Failure artifacts

### Scalability

- Parallel execution
- Multi-browser execution
- CI/CD integration
- Environment-based configuration
- Automated reporting

## 🗺️ Future Enhancements

- [ ] GitHub Actions CI/CD pipeline
- [ ] Allure reporting
- [ ] API testing using Playwright APIRequestContext
- [ ] Data-driven testing
- [ ] Environment-specific configuration
- [ ] Faker-based test data generation
- [ ] Accessibility testing
- [ ] Visual regression testing
- [ ] BrowserStack integration
- [ ] Docker-based execution
- [ ] Slack/Teams test notifications
- [ ] Test tagging such as `@smoke` and `@regression`
- [ ] Retry and flaky-test analysis
- [ ] Test management integration

## 📚 Learning Outcomes

This project provides hands-on experience with:

- Playwright automation
- TypeScript
- End-to-end testing
- Page Object Model
- Test design
- Browser automation
- Test reporting
- Debugging
- Test artifacts
- Parallel execution
- Cross-browser testing
- CI/CD automation

## 🏦 About ParaBank

ParaBank is a demonstration banking application from Parasoft designed to simulate realistic banking workflows for software testing and demonstrations.

**Demo Application:**

https://parabank.parasoft.com/parabank/

## 👨‍💻 Author

**Vinod Pasi**

Lead SDET | Test Automation Leader | QA Automation Architect

Specialized in:

- Playwright
- Selenium
- Cypress
- WebdriverIO
- TypeScript
- JavaScript
- C#
- API Testing
- CI/CD
- Test Automation Framework Design

GitHub:

https://github.com/vinodkpasi

## ⭐ Support

If you find this project useful for learning or demonstrating Playwright automation, consider giving the repository a ⭐ on GitHub.

## 📄 License

This project is intended for educational and demonstration purposes.

The ParaBank application is owned and provided by Parasoft. Please refer to the application's official terms and licensing information when using the demo environment.
