# GitHub Copilot Space Rules for Environment Variables

This directory contains GitHub Copilot Space rules to help manage environment variable tables in the Datadog documentation.

## Overview

The rules in this directory help maintain consistent formatting and structure for environment variable documentation across the Datadog documentation site. These rules assist with:

- Adding new environment variables to existing tables
- Creating new environment variable tables with proper formatting
- Ensuring consistent description formatting and required field marking
- Following Datadog documentation standards

## Files

- `env_vars.yaml` - Contains the Copilot Space rules for environment variable tables

## Rules

### 1. Add environment variable to existing table

This rule helps add new environment variable entries to existing tables while maintaining proper formatting.

**Pattern:**
```markdown
| `VARIABLE_NAME` | Description |
```

**Examples:**

For required variables:
```markdown
| `DD_API_KEY` | [Datadog API Key][1] - **Required** |
```

For optional variables with defaults:
```markdown
| `DD_LOGS_ENABLED` | When true, send logs to Datadog. Defaults to false. |
```

### 2. Create new environment variables table

This rule helps create new environment variable sections with proper markdown table formatting.

**Template:**
```markdown
### Environment Variables

| Variable | Description |
| -------- | ----------- |
|`DD_API_KEY`| [Datadog API Key][1] - **Required**|
| `DD_SITE` | [Datadog site][2] - **Required** |
| `DD_SERVICE` | See [Unified Service Tagging][3] |
```

### 3. Format environment variable descriptions

This rule ensures consistent formatting for variable descriptions.

**Guidelines:**
- Mark required variables with `**Required**`
- Include documentation links using `[Link Text][reference]` format
- For boolean variables, specify behavior for true/false values
- State default values when applicable
- Reference Unified Service Tagging for standard variables

## Usage Instructions

### Using with GitHub Copilot

1. **Adding to existing tables**: When you have an environment variables table and want to add a new entry, GitHub Copilot will suggest properly formatted entries based on the context.

2. **Creating new tables**: When starting a new environment variables section, Copilot will suggest the complete table structure with common Datadog variables.

3. **Formatting descriptions**: When writing variable descriptions, Copilot will suggest consistent formatting patterns.

### Manual Usage

Even without Copilot, you can follow these patterns manually:

#### Adding a required environment variable:
```markdown
| `DD_API_KEY` | [Datadog API Key][1] - **Required** |
```

#### Adding an optional environment variable:
```markdown
| `DD_SERVICE` | Service name for unified service tagging |
```

#### Adding a variable with default value:
```markdown
| `DD_LOGS_ENABLED` | When true, send logs to Datadog. Defaults to false. |
```

## Examples

### Example 1: Adding to existing table

**Before:**
```markdown
| Variable | Description |
| -------- | ----------- |
|`DD_API_KEY`| [Datadog API Key][6] - **Required**|
| `DD_SITE` | [Datadog site][4] - **Required** |
```

**After adding DD_SERVICE:**
```markdown
| Variable | Description |
| -------- | ----------- |
|`DD_API_KEY`| [Datadog API Key][6] - **Required**|
| `DD_SITE` | [Datadog site][4] - **Required** |
| `DD_SERVICE` | Service name for unified service tagging |
```

### Example 2: Creating new table

```markdown
### Environment Variables

Configure the following environment variables for the integration:

| Variable | Description |
| -------- | ----------- |
|`DD_API_KEY`| [Datadog API Key][1] - **Required**|
| `DD_SITE` | [Datadog site][2] - **Required** |
| `DD_SERVICE` | See [Unified Service Tagging][3] |
| `DD_VERSION` | See [Unified Service Tagging][3] |
| `DD_ENV` | See [Unified Service Tagging][3] |
| `DD_LOGS_ENABLED` | When true, send logs to Datadog. Defaults to false. |
| `DD_TRACE_ENABLED` | When true, enable APM tracing. Defaults to true. |
```

## Testing

To test these rules:

1. **Create a new markdown file** in the documentation with an environment variables section
2. **Use GitHub Copilot** to suggest new entries or create new tables
3. **Verify formatting** matches the patterns defined in the rules
4. **Check that**:
   - Variable names are in backticks
   - Required variables are marked with `**Required**`
   - Links use proper markdown reference format
   - Table formatting is consistent

## Validation Checklist

When using these rules, ensure:

- [ ] Variable names are in backticks (`` `DD_VARIABLE` ``)
- [ ] Table headers are exactly `| Variable | Description |`
- [ ] Table separator is exactly `| -------- | ----------- |`
- [ ] Required variables include `**Required**`
- [ ] Links use markdown reference format `[text][ref]`
- [ ] Boolean variables explain true/false behavior
- [ ] Default values are specified when applicable

## Contributing

When updating these rules:

1. Maintain consistency with existing Datadog documentation patterns
2. Test rules with real documentation examples
3. Update both the YAML rules and this README
4. Ensure examples reflect current best practices