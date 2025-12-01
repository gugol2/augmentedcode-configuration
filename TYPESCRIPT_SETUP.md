# TypeScript Setup Guide

This configuration is now set up for TypeScript development with VS Code.

## What Changed

### 1. Rules Configuration
- **Rules File**: `.agents/rules/base.md` - TypeScript rules (single source of truth)
- **Symlinks**: `CLAUDE.md`, `AGENTS.md`, `GEMINI.md` point to `base.md`

### 2. VS Code Configuration
Created `.vscode/` directory with:
- **tasks.json** - Quick access to npm scripts (Ctrl+Shift+B for validate)
- **settings.json** - TypeScript, ESLint, Prettier configuration
- **extensions.json** - Recommended VS Code extensions

### 3. Key Changes from Python Version

| Python | TypeScript |
|--------|-----------|
| `pytest` | `jest` or `vitest` |
| `mypy` | `tsc` (TypeScript compiler) |
| `black` | `prettier` |
| `flake8` | `eslint` |
| `make validate` | `npm run validate` |
| `make test-unit` | `npm run test` |

## Getting Started

### 1. Copy to Your Project

```bash
# Copy configuration files
cp -r .vscode /path/to/your/project/
cp CLAUDE.md /path/to/your/project/  # Or create symlink
```

### 2. Set Up Package.json

Copy the template and customize:
```bash
cp package.json.template /path/to/your/project/package.json
```

Edit `package.json` to match your project structure.

### 3. Create TypeScript Configuration

Create `tsconfig.json`:
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "lib": ["ES2020"],
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true,
    "declaration": true,
    "declarationMap": true,
    "sourceMap": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist", "**/*.test.ts", "**/*.spec.ts"]
}
```

### 4. Create Jest Configuration

Create `jest.config.js`:
```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  roots: ['<rootDir>/src'],
  testMatch: ['**/__tests__/**/*.ts', '**/?(*.)+(spec|test).ts'],
  collectCoverageFrom: [
    'src/**/*.ts',
    '!src/**/*.test.ts',
    '!src/**/*.spec.ts',
    '!src/**/__tests__/**'
  ],
  coverageThreshold: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80
    }
  }
};
```

### 5. Create ESLint Configuration

Create `.eslintrc.js`:
```javascript
module.exports = {
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaVersion: 2020,
    sourceType: 'module',
    project: './tsconfig.json'
  },
  plugins: ['@typescript-eslint'],
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
    'plugin:@typescript-eslint/recommended-requiring-type-checking',
    'prettier'
  ],
  rules: {
    '@typescript-eslint/explicit-function-return-type': 'error',
    '@typescript-eslint/no-explicit-any': 'error',
    '@typescript-eslint/no-unused-vars': ['error', { argsIgnorePattern: '^_' }],
    'max-lines-per-function': ['warn', { max: 20, skipBlankLines: true, skipComments: true }]
  }
};
```

### 6. Create Prettier Configuration

Create `.prettierrc`:
```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 100,
  "tabWidth": 2
}
```

### 7. Install Dependencies

```bash
npm install
```

### 8. Install Recommended VS Code Extensions

Press `Ctrl+Shift+P` → "Extensions: Show Recommended Extensions" → Install all

## Using VS Code Tasks

### Run Tasks
- **Validate**: `Ctrl+Shift+B` (default build task)
- **Test**: `Ctrl+Shift+P` → "Tasks: Run Test Task"
- **All Tasks**: `Ctrl+Shift+P` → "Tasks: Run Task"

### Available Tasks
- `validate` - Run all checks (default build)
- `test` - Run tests
- `test:watch` - Watch mode
- `test:coverage` - Coverage report
- `type-check` - TypeScript check
- `lint` - ESLint check
- `lint:fix` - Auto-fix issues
- `format` - Format code
- `build` - Build TypeScript
- `dev` - Development mode

## Working with Claude Code

The AI agent will now:
- Use `npm run` scripts instead of `make` commands
- Follow TypeScript/Jest patterns instead of Python/pytest
- Enforce strict TypeScript typing
- Use Prettier for formatting
- Use ESLint for linting

## Claude Code Slash Commands

The Cursor IDE slash commands in `.cursor/commands/` are specific to Cursor. For VS Code with Claude Code:
- Use Claude Code directly in the terminal
- Reference the commands as templates for prompts
- Use VS Code tasks for quick validation

## Example Workflow

1. **Start Test Watch Mode**:
   ```bash
   npm run test:watch
   ```

2. **Write Failing Test** (TDD):
   - Claude will write a single test that fails

3. **Implement Feature**:
   - Claude implements minimal code to pass

4. **Validate Before Commit**:
   ```bash
   npm run validate
   ```

5. **Fix Any Issues**:
   ```bash
   npm run lint:fix
   npm run format
   ```

6. **Commit** (only after validate passes)

## Differences from Cursor IDE

| Cursor IDE | VS Code + Claude Code |
|------------|----------------------|
| Slash commands in `.cursor/commands/` | Use Claude Code in terminal or as prompts |
| Built-in AI chat | Claude Code CLI interface |
| `.cursor/rules/` | Uses `CLAUDE.md` symlink |

## Notes

- **Single ruleset**: All rules are in `.agents/rules/base.md`
- **Customize**: Edit `base.md` for project-specific rules
- **Test frameworks**: Choose Jest (more popular) or Vitest (faster, better ESM support)

## Troubleshooting

### Tests not running
- Check `jest.config.js` paths match your structure
- Verify `ts-jest` is installed

### Type checking fails
- Ensure `tsconfig.json` includes all source files
- Check `strict: true` is enabled

### ESLint errors
- Run `npm run lint:fix` to auto-fix
- Check `.eslintrc.js` rules match your style

### VS Code not finding TypeScript
- Reload window: `Ctrl+Shift+P` → "Reload Window"
- Check workspace TypeScript version: `Ctrl+Shift+P` → "Select TypeScript Version" → "Use Workspace Version"
