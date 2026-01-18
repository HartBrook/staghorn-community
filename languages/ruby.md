## Ruby Guidelines

- Use Ruby 3.2+ and leverage modern features
- Follow the Ruby Style Guide
- Prefer symbols over strings for hash keys
- Use guard clauses for early returns
- Prefer keyword arguments for methods with multiple parameters

## Modern Ruby Features

- **Pattern matching**: Use for destructuring and matching
- **Data class**: Use for simple immutable value objects (Ruby 3.2+)
- **Endless methods**: Use for simple one-liner methods
- **Numbered block parameters**: Use `_1`, `_2` for simple blocks

```ruby
# Data class for immutable value objects
User = Data.define(:id, :name, :email)

# Pattern matching
case response
in { status: 200, body: }
  process(body)
in { status: 404 }
  raise NotFoundError
in { status: status } if status >= 500
  raise ServerError
end

# Endless method for simple transformations
def full_name = "#{first_name} #{last_name}"
```

## Naming Conventions

- snake_case for methods, variables, and file names
- PascalCase for classes and modules
- SCREAMING_SNAKE_CASE for constants
- Predicate methods end in `?` (`valid?`, `empty?`)
- Dangerous methods end in `!` (`save!`, `destroy!`)
- Use descriptive method names; avoid abbreviations

## Error Handling

- Raise specific exceptions inheriting from `StandardError`
- Create a base application error class
- Include context in error messages
- Use `begin/rescue/end` sparingly; let errors propagate when appropriate
- Never rescue `Exception`; rescue `StandardError` or specific errors

```ruby
module MyApp
  class Error < StandardError; end

  class NotFoundError < Error
    attr_reader :resource, :id

    def initialize(resource, id)
      @resource = resource
      @id = id
      super("#{resource} not found: #{id}")
    end
  end
end
```

## Dependencies

- Use Bundler for dependency management
- Commit `Gemfile.lock` for applications; exclude for gems
- Use pessimistic version constraints (`~>`) for gems
- Keep dependencies minimal; audit regularly
- Group gems appropriately (`:development`, `:test`, `:production`)

## Testing

- Use RSpec with `describe`, `context`, `it` patterns
- Use `let` and `let!` for test setup; prefer `let` over instance variables
- Use FactoryBot for test data factories
- Use WebMock or VCR for HTTP request stubbing
- Test behavior, not implementation

```ruby
RSpec.describe UserService do
  describe "#find" do
    subject(:service) { described_class.new(repository:) }

    let(:repository) { instance_double(UserRepository) }
    let(:user) { build(:user) }

    context "when user exists" do
      before { allow(repository).to receive(:find).with("1").and_return(user) }

      it "returns the user" do
        expect(service.find("1")).to eq(user)
      end
    end

    context "when user does not exist" do
      before { allow(repository).to receive(:find).with("1").and_return(nil) }

      it "raises NotFoundError" do
        expect { service.find("1") }.to raise_error(NotFoundError)
      end
    end
  end
end
```

## Type Checking

- Use Sorbet for type annotations in critical code paths
- Add `# typed: strict` for new files when using Sorbet
- Use RBS for standard library type definitions
- Type-check public interfaces; internal methods can be more relaxed

```ruby
# typed: strict
class UserService
  extend T::Sig

  sig { params(id: String).returns(User) }
  def find(id)
    # ...
  end
end
```

## Common Commands

- Run tests: `bundle exec rspec`
- Run specific test: `bundle exec rspec spec/path_spec.rb:42`
- Lint: `bundle exec rubocop`
- Auto-fix: `bundle exec rubocop -A`
- Type check: `bundle exec srb tc`
- Console: `bundle exec irb` or `bin/rails console`
