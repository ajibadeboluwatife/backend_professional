# Contributing to Backend Professional

Thank you for your interest in contributing to Backend Professional! This document provides guidelines and instructions for contributing.

## Development Setup

### Prerequisites

- Python 3.12+
- Node.js 18+
- Docker & Docker Compose
- Git

### Initial Setup

1. Fork and clone the repository:
   ```bash
   git clone https://github.com/your-username/backend_professional.git
   cd backend_professional
   ```

2. Set up environment files:
   ```bash
   cp backend/.env.example backend/.env
   cp frontend/.env.example frontend/.env
   ```

3. Start development environment:
   ```bash
   docker compose up --build
   ```

## Project Structure

```
backend_professional/
├── backend/          # FastAPI backend
├── frontend/         # React frontend
├── ollama/          # Ollama LLM service
├── docker-compose.yaml
├── makefile
└── README.md
```

## Making Changes

### Backend Development

1. Navigate to backend directory:
   ```bash
   cd backend
   ```

2. Install dependencies (for local development):
   ```bash
   pip install -r requirements.txt
   ```

3. Make your changes in `app/` directory

4. Test your changes:
   ```bash
   python -m pytest  # if tests exist
   ```

5. Check code style:
   ```bash
   python -m black app/
   python -m isort app/
   ```

### Frontend Development

1. Navigate to frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start development server:
   ```bash
   npm run dev
   ```

4. Make your changes in `src/` directory

5. Check for issues:
   ```bash
   npm run lint
   npm run build  # ensure build succeeds
   ```

## Coding Standards

### Python (Backend)

- Follow PEP 8 style guide
- Use type hints for function parameters and return values
- Write docstrings for all functions and classes
- Keep functions focused and concise
- Use async/await for I/O operations

Example:
```python
async def process_data(input_data: str) -> dict:
    """Process input data and return results.
    
    Args:
        input_data: Raw input string to process.
        
    Returns:
        dict: Processed data with metadata.
    """
    # Implementation
    return result
```

### TypeScript (Frontend)

- Use TypeScript for all new files
- Define interfaces for data structures
- Use functional components with hooks
- Follow React best practices
- Add comments for complex logic

Example:
```typescript
interface Message {
  id: string
  content: string
  sender: 'user' | 'assistant'
}

function ChatComponent(): React.ReactElement {
  // Implementation
  return <div>...</div>
}
```

## Commit Guidelines

### Commit Message Format

```
<type>: <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

### Examples

```
feat: add user authentication to chat endpoint

- Implement JWT token validation
- Add user context to chat requests
- Update API documentation

Closes #123
```

```
fix: resolve CORS issue in production

Update CORS middleware to allow specific origins
instead of wildcard in production environment.
```

## Pull Request Process

1. **Create a feature branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes and commit:**
   ```bash
   git add .
   git commit -m "feat: add your feature"
   ```

3. **Push to your fork:**
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Open a Pull Request:**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your branch
   - Fill in the PR template

5. **PR Requirements:**
   - Clear description of changes
   - Link to related issues
   - All tests passing
   - No linting errors
   - Updated documentation if needed

## Testing

### Backend Testing

```bash
cd backend
pytest tests/
```

### Frontend Testing

```bash
cd frontend
npm test
```

## Documentation

When adding new features:

1. Update relevant README files
2. Add docstrings to functions
3. Update API documentation
4. Add inline comments for complex logic

## Code Review

All contributions go through code review:

- Be responsive to feedback
- Make requested changes promptly
- Ask questions if unclear
- Be respectful and constructive

## Questions?

- Open an issue for bugs or feature requests
- Start a discussion for general questions
- Check existing issues before creating new ones

## License

By contributing, you agree that your contributions will be licensed under the same license as the project.
