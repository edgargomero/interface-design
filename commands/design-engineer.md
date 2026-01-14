# design-engineer

Smart dispatcher for design system management.

## Usage

```
/design-engineer              # Auto-detect action
/design-engineer status       # Show current system
/design-engineer audit <path> # Check code against system
/design-engineer extract      # Extract patterns from code
```

## Dispatcher Logic

**Check for `.design-engineer/system.md`:**

### System Exists
Show current status:
- Direction and foundation
- Established patterns
- Recent updates
- Suggest: `/design-engineer audit` to check existing code

### No System
Suggest: `/design-engineer extract` to pull patterns from existing code, OR start building UI to establish system automatically.

## Commands

- **status** → Show current design system state
- **audit** → Validate existing code against system
- **extract** → Extract patterns from existing code

Run without arguments for smart suggestions based on project state.
