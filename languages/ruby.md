## Ruby Guidelines

- Follow the Ruby Style Guide
- Use Ruby 3.0+ features where appropriate
- Prefer symbols over strings for hash keys
- Use guard clauses for early returns

## Naming Conventions

- snake_case for methods and variables
- PascalCase for classes and modules
- SCREAMING_SNAKE_CASE for constants
- Use predicate methods ending in `?` for boolean returns

## Error Handling

- Raise specific exceptions, not generic RuntimeError
- Create custom exception classes inheriting from StandardError
- Use `begin/rescue/end` blocks judiciously
- Fail fast with meaningful error messages

## Project Structure

```
lib/
  gem_name/
    version.rb
    ...
  gem_name.rb
spec/
  gem_name/
    ...
  spec_helper.rb
Gemfile
gem_name.gemspec  # For gems
```

## Dependencies

- Use Bundler for dependency management
- Lock dependencies with Gemfile.lock
- Keep dependencies minimal and up to date
- Use semantic versioning constraints

## Testing

- Use RSpec for testing
- Follow describe/context/it patterns
- Use FactoryBot for test fixtures
- Mock external services appropriately

## Type Checking

- Use Sorbet or RBS for type annotations
- Add type signatures to public interfaces
- Consider `# typed: strict` for new files

## Common Commands

- Run tests: `bundle exec rspec`
- Lint: `bundle exec rubocop`
- Type check: `bundle exec srb tc` (Sorbet)
- Console: `bundle exec irb` or `rails console`
