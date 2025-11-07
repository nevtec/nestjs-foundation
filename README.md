# the-nucleus-premis/nestjs-foundation

# The Nucleus Premise NestJS API Framework

A comprehensive, production-ready NestJS framework designed to accelerate development and eliminate repetitive CRUD operations. This framework of thinking has evolved over the past 10 years, and as soon as we found NestJS, we knew it was a game changer and also very familiar since we use Angular for the frontend. Built with SOLID principles and DRY methodology, NevTec provides everything you need to jump-start your next API project. We are excited for this version of our framework and have some exciting ideas to do with it. As we continue to work on it, feedback is very helpful! Looking for peer review, suggestions, criticism, kudos, and insights on what we might be missing.

> **"NestJS + Opinionated Structure"** - Built on NestJS with our battle-tested patterns for rapid development  
> **"Enterprise-Ready from Day One"** - Multi-tenant, security, audit trails  
> **"10 Years of Lessons Learned"** - Battle-tested patterns and solutions 

## 🚀 Philosophy & Core Principles

### The Problem We Solved
After building multiple NestJS applications, we found ourselves repeatedly writing the same boilerplate code for:
- Basic CRUD operations
- Authentication and authorization
- Database schema standardization
- Error handling and logging
- API documentation

### Our Solution: The NevTec Framework
We created a comprehensive library that follows **SOLID principles** and **DRY methodology** to eliminate repetitive code while maintaining flexibility and extensibility.

## 🏗️ Core Architecture

### BaseSchema & BaseDto - Standardization Foundation
Every top-level schema extends `BaseSchema`, providing consistent properties across all entities:
- `_id`, `company_id`, `location_id` - Multi-tenant support
- `date_entered`, `last_updated`, `date_deleted` - Audit trail
- `last_updated_by_id`, `locked_by_id` - User tracking
- `ip_address` - Security logging

`BaseDto` mirrors `BaseSchema` properties, keeping your DTOs DRY and type-safe.

### BaseController & BaseService - CRUD Automation
Instead of writing the same CRUD methods repeatedly, extend our base classes:

```typescript
// Your controller becomes incredibly simple
@Controller('users')
export class UserController extends BaseController<UserDocument, UserDto> {
  constructor(service: UserService) {
    super(service);
  }
  // All CRUD operations are inherited!
}
```

**Key Benefits:**
- **REST-style query parsing** - Automatically converts query strings to Mongoose filters
- **Method chaining** - Chain operations just like using Mongoose directly
- **Automatic filtering** - Soft deletes, tenant filtering, role-based access
- **Override flexibility** - Override any method for custom behavior

### Multi-Tenant Architecture
Built-in support for:
- **Company separation** - Each client gets isolated data
- **Location-based filtering** - Multi-location support within companies
- **Role-based access control** - Automatic filtering based on user roles
- **Automatic tenant injection** - JWT data automatically populates new records

## 🔐 Authentication & Authorization

### Complete Auth System
- **JWT-based authentication** with refresh tokens
- **Role-based access control** with configurable permissions
- **Multi-tenant user management** with company/location isolation
- **Password hashing** with bcrypt
- **Skip auth decorators** for public endpoints

### Smart Decorators
- `@SkipAuth()` - Mark endpoints as public
- `@Roles()` - Restrict access by user roles
- `@CurrentUser()` - Inject current user data
- Automatic JWT payload extraction and validation

## 🛠️ Developer Experience Features

### Automatic Interface Generation
Our CLI automatically generates TypeScript interfaces from your DTOs:
```bash
npm run start:dev  # Runs NestJS server + interface generation (via concurrently)
npm run watch-interfaces  # Or run interface generation separately
```
Your Angular frontend automatically knows the exact structure of your API responses as you make changes.

### Intelligent Logging System
- **Logger mixin** - Toggle logging on/off without code changes
- **Email notifications** - Critical errors automatically emailed to developers
- **Stack trace parsing** - Clean, readable error reports
- **Context-aware logging** - Includes user, location, and request context

### Database Module
- **Environment-based configuration** - Reads `.env` for MongoDB connection
- **Automatic connection management** - Handles reconnections and errors
- **Multi-database support** - Easy switching between environments

#### 🚧 Coming Soon
- **Docker support** - Containerized deployment with Docker Compose
- **PM2 integration** - Process management for production environments
- **Deployment scripts** - Automated deployment workflows

### Roadmap & Development Status

<div style="overflow-x: auto; margin: 20px 0;">

<div style="margin-bottom: 16px;">

![Not Started](https://img.shields.io/badge/Status-Not%20Started-red) ![In Progress](https://img.shields.io/badge/Status-In%20Progress-yellow) ![Complete](https://img.shields.io/badge/Status-Complete-green) ![Planned](https://img.shields.io/badge/Status-Planned-blue) ![Review Requested](https://img.shields.io/badge/Status-Review%20Requested-purple) ![Considering](https://img.shields.io/badge/Status-Considering-orange)

</div>

<table style="min-width: 800px; width: 100%; border-collapse: collapse;">
<thead>
<tr>
<th style="text-align: left; padding: 8px 12px;">Feature</th>
<th style="text-align: left; padding: 8px 12px;">Status</th>
<th style="text-align: left; padding: 8px 12px;">Description</th>
<th style="text-align: left; padding: 8px 12px;">Progress Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding: 8px 12px;"><strong>Bash/CLI Helper</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Enhanced CLI tools for project management, database operations, and deployment</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Deployment Scripts</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Automated deployment workflows and production setup</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Zipcode Collection Population</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Automated script to populate zipcode collection using mongodump/restore</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Audit History</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Complete audit trail system with frontend configuration support</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Angular Frontend Extension</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Angular v21 with signals, auth service, multiple layouts, user preferences, Cordova compilation for iOS/Android stores</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Ultra-Simple Startup</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Docker-based instant setup with MongoDB, zipcode data, and Postman collection</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Performance Monitoring</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">APM integration, request/response metrics, and performance insights</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Testing Utilities</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Review%20Requested-purple" /></td>
<td style="padding: 8px 12px;">Base test classes, mocking utilities, and testing patterns</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Caching Layer</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Redis integration for common operations and query caching</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Mobile API Support</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Mobile-specific response formats and optimization</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Internationalization</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">i18n support for multi-language APIs and responses</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>WebSocket Support</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Real-time communication, live updates, and event streaming</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>GraphQL Integration</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Considering-orange" /></td>
<td style="padding: 8px 12px;">Flexible query language for efficient data fetching and API flexibility</td>
<td style="padding: 8px 12px;">—</td>
</tr>
<tr>
<td style="padding: 8px 12px;"><strong>Ollama LLM Integration</strong></td>
<td style="padding: 8px 12px;"><img alt="Status" src="https://img.shields.io/badge/Status-Not%20Started-red" /></td>
<td style="padding: 8px 12px;">Cost-effective AI capabilities with local LLM models for intelligent features</td>
<td style="padding: 8px 12px;">—</td>
</tr>
</tbody>
</table>

</div>

### Swagger Documentation
- **Automatic API documentation** - Generated from your controllers
- **Bearer token support** - Built-in authentication documentation
- **Base controller decorators** - Consistent documentation across all endpoints
- **DTO structure visibility** - Complete DTO schemas displayed via class-transformer integration
- **Custom documentation override** - Override base controller method documentation using `@ApiOperation()` and `@ApiResponse()` decorators

#### Customizing Base Controller Documentation
To override the automatic Swagger documentation for methods inherited from `BaseController`, simply add Swagger decorators to your controller:

```typescript
@Controller('users')
export class UserController extends BaseController<UserDocument, UserDto> {
  constructor(service: UserService) {
    super(service);
  }

  @Post()
  @ApiOperation({ 
    summary: 'Create a new user',
    description: 'Creates a new user with custom validation rules and business logic'
  })
  @ApiResponse({ 
    status: 201, 
    description: 'User successfully created',
    type: UserDto 
  })
  @ApiResponse({ 
    status: 400, 
    description: 'Invalid input data' 
  })
  async create(@Body() createUserDto: CreateUserDto): Promise<UserDto> {
    // Your custom implementation here
    return super.create(createUserDto);
  }
}
```

### Mongoose Decorators
- **@Sensitive()** - Mark fields as sensitive and exclude them from JSON/Object serialization
- **@Encrypt()** - Automatically encrypt/decrypt fields when saving to database
- **Flexible options** - Customize encryption algorithms and sensitive field behavior
- **Type-safe** - Full TypeScript support with decorator metadata

#### Example Usage
```typescript
@Schema()
export class User extends BaseSchema {
    @Prop({ required: true })
    email: string;

    @Prop({ required: true, select: false })
    @Sensitive() // Never included in JSON responses
    password: string;

    @Prop()
    @Sensitive({ fromObject: false }) // Excluded from JSON but included in Object
    @Encrypt({ algorithm: 'aes-256-gcm' }) // Custom encryption
    ssn: string;
}

export const UserSchema = SchemaFactory.createForClass(User);
// ⚠️ REQUIRED: Setup functions must be called for decorators to work
setupSensitiveTransforms(UserSchema, User);
setupEncryptionTransforms(UserSchema, User);
```

## 🌍 General Utilities

### Built-in Data Services
- **State list** - Complete US states with proper formatting for use in easy population for front end forms
- **Timezone support** - Comprehensive timezone data for use in easy population for front end forms
- **Zipcode lookup** - City and state lookup by zipcode
- **Version checking** - Frontend cache invalidation system

#### 🚧 Coming Soon
- **Zipcode data import** - Automated script to populate zipcode collection for new setups

### Error Handling
- **Global exception filters** - Consistent error responses
- **Stack trace parsing** - Clean error reporting
- **User context tracking** - Know exactly who encountered what error
- **Email notifications** - Critical errors sent to developers

## 🚀 Getting Started

### Quick Setup
```bash
# Clone and setup
git clone <your-repo>
cd your-project/rest-api

# Install dependencies
npm install

# Setup environment
cp .env.template .env
# Edit .env with your MongoDB credentials

# Start development
npm run start:dev
```

### 🚧 Ultra-Simple Startup (Coming Soon)
We're working on an instant gratification experience where developers can:

1. **Set environment variables** - Just configure your `.env` file
2. **Start with Docker** - `docker-compose up` handles everything
3. **Automatic data seeding** - Zipcode collection restored on first startup
4. **Ready-to-test API** - Postman collection generated and ready to import
5. **Instant login** - Pre-configured test user for immediate testing (in dev mode)

**Docker vs Local MongoDB:**
- **Docker mode**: Complete containerized setup with MongoDB, zipcode data, and API
- **Local mode**: Connect to your existing MongoDB instance
- **Hybrid mode**: Use Docker for MongoDB but run API locally for development

This approach eliminates the "works on my machine" problem and gets developers productive in minutes, not hours.

### 🚀 Future Vision

We're building more than just a framework - we're creating an ecosystem:

- **Full-Stack Integration** - Seamless Angular + NestJS development experience
- **Cloud-Native Ready** - Docker, Kubernetes, and cloud deployment patterns
- **AI-Powered Development** - Code generation, intelligent suggestions, and automated testing
- **Enterprise Features** - SSO, advanced RBAC, compliance tools, and audit reporting
- **Community-Driven** - Open source with commercial support options
- **Learning Platform** - Tutorials, best practices, and real-world examples

### Creating New Modules
Use our CLI to generate new modules with the base structure:
```bash
./nevtec
# Select "Generate Module"
# Enter module name (e.g., "Product")
# All boilerplate code is generated!
```

## 📦 Available Modules

### Core Modules
- **@nevtec/base** - BaseSchema, BaseDto, BaseController, BaseService
- **@nevtec/auth** - Complete authentication system
- **@nevtec/common** - Utilities, filters, interceptors, decorators

### Features
- **Multi-tenant support** - Company and location isolation
- **Role-based access** - Configurable permissions
- **Soft delete support** - Automatic filtering of deleted records
- **Audit trails** - Complete change tracking
- **Email notifications** - Error reporting system

## 🔧 CLI Tools

### NevTec CLI
Interactive project management tool:
- **Setup new projects** - Complete Angular + NestJS setup
- **Generate modules** - Create new modules with base structure
- **Database operations** - Backup, restore, manage databases
- **Dependency management** - Install required packages
- **Postman generation** - Create API collections

## 🎯 Why NevTec?

### Built on NestJS with Opinionated Structure
NestJS is already the "Angular of backends" - providing familiar patterns and structure. NevTec adds our opinionated layer on top, giving you battle-tested patterns for rapid development. If you love Angular's structure and NestJS's approach, you'll feel right at home with NevTec's additional structure and conventions.

### Enterprise-Ready from Day One
- **Jump-start development** - Get a working API in minutes
- **Consistent patterns** - All modules follow the same structure
- **Built-in best practices** - Security, logging, error handling included
- **Type safety** - Full TypeScript support throughout
- **Multi-tenant architecture** - Built for real-world, scalable applications
- **Production monitoring** - Logging, error tracking, and performance insights

### 10 Years of Lessons Learned
This isn't just another boilerplate - it's a distillation of a decade of building production applications. Every feature exists because we've encountered the problem in real projects.

### What Makes Us Different

| Feature | NevTec | Other Solutions |
|---------|--------|----------------|
| **Multi-tenant** | ✅ Built-in | ❌ Manual implementation |
| **Audit trails** | ✅ Automatic | ❌ Custom code required |
| **Type safety** | ✅ End-to-end | ⚠️ Partial |
| **Auto documentation** | ✅ Swagger + custom | ⚠️ Basic only |
| **Angular integration** | ✅ Seamless | ❌ Manual setup |
| **Production ready** | ✅ From day one | ⚠️ Requires setup |

## 📚 Documentation

- **API Documentation** - Available at `/api` when running
- **Code Examples** - See `src/` directory for implementation examples
- **Integration Tests** - Comprehensive test coverage
- **CLI Help** - Run `./NevTec` for interactive help

## 🤝 Contributing

We welcome contributions! The framework is designed to be:
- **Extensible** - Easy to add new features
- **Maintainable** - Clean, well-documented code
- **Testable** - Comprehensive test coverage
- **Type-safe** - Full TypeScript support

## 💬 Feedback & Community

We're actively seeking feedback from the developer community! Your input helps us:

- **Identify missing features** - What would make your development experience better?
- **Improve documentation** - Is anything unclear or could be explained better?
- **Validate our approach** - Are we solving the right problems?
- **Discover new use cases** - How are you using the framework?

### Ways to Contribute Feedback

- **GitHub Issues** - Report bugs, request features, or ask questions
- **Discussions** - Share ideas, best practices, or implementation examples
- **Pull Requests** - Submit improvements or new features
- **Code Reviews** - Help us maintain code quality and consistency

### What We're Looking For

- **Real-world usage** - How does this fit into your development workflow?
- **Pain points** - What's still frustrating or missing?
- **Feature requests** - What would make this framework more valuable?
- **Performance insights** - Any bottlenecks or optimization opportunities?
- **Security concerns** - Are we handling security correctly?
- **Documentation gaps** - What needs better explanation?

**Every piece of feedback matters!** Whether it's a small typo, a major feature request, or a completely different approach - we want to hear from you.

---

## Development Notes

### DEP0190 Deprecation Warning during `npm run start:dev`

When running `npm run start:dev`, you may see:

```
(node:####) [DEP0190] DeprecationWarning: Passing args to a child process with shell option true can lead to security vulnerabilities, as the arguments are not escaped, only concatenated.
```

#### Why this appears

The `start:dev` script uses `concurrently` to run multiple commands:

```
concurrently "nest start --watch" "npm run watch-interfaces"
```

Internally, `concurrently` uses Node.js `child_process` with `shell: true` to orchestrate commands. Node.js warns because using `shell: true` with dynamic or untrusted input can enable shell injection.

#### Is it safe here?

Yes. In this project, the commands passed to `concurrently` are static, hardcoded strings, not user input. This is a development-only script, so the warning is cosmetic in our context.

#### How to reduce or avoid the warning

- Keep `concurrently` up to date (`devDependency`) as newer versions may improve behavior.
- Ensure no untrusted input is ever concatenated into shell commands.

Update `concurrently` to the latest version:

```bash
cd rest-api
npm install --save-dev concurrently@latest
```

You can verify the installed version with:

```bash
cd rest-api
npx concurrently --version
```
