# Historical planning snapshot

Superseded for new investment on 2026-09-24. Retained for historical requirements; claims below are not revalidated.

# MCP Plugin Examples 📚

> **Reference implementations and example plugins for the Model Context Protocol**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![MCP Version](https://img.shields.io/badge/MCP-2025--06--18-green.svg)](https://modelcontextprotocol.io)
[![Examples](https://img.shields.io/badge/Examples-25%2B-blue.svg)](./examples)
[![Community](https://img.shields.io/badge/Community-Discord-7289da.svg)](https://discord.gg/mcp)

A comprehensive collection of example plugins demonstrating best practices, common patterns, and real-world integrations for the MCP Plugin System.

## 🎯 Overview

This repository contains:
- **Basic Plugins** - Simple examples to get started
- **Database Connectors** - SQL and NoSQL integrations
- **API Integrations** - Third-party service connectors
- **AI/ML Tools** - Model inference and AI utilities
- **System Tools** - OS and filesystem interactions
- **Monitoring Plugins** - Observability and metrics

## 🚀 Quick Start

### Prerequisites

- Rust 1.85+ (for Rust plugins)
- Python 3.8+ (for Python plugins)
- Node.js 18+ (for JavaScript plugins)
- [Prism MCP SDK](https://github.com/prismworks-ai/prism-mcp-rs)
- [Prism Platform](https://github.com/prismworks-ai/prism-platform) (for advanced features)

### Using an Example Plugin

```bash
# Clone the repository
git clone https://github.com/prismworks-ai/mcp-plugin-examples.git
cd mcp-plugin-examples

# Build a specific plugin
cd plugins/calculator
cargo build --release

# The plugin is now ready at target/release/libcalculator.so (or .dll/.dylib)
```

### Testing a Plugin

```bash
# Using MCP CLI
mcp plugin test ./target/release/libcalculator.so

# Or with the test server
cd ../../test-server
cargo run -- --plugin-dir ../plugins/calculator/target/release
```

## 📋 Plugin Categories

### 🎓 Basic Plugins

Simple plugins demonstrating core concepts:

#### [Echo Plugin](../../plugins/basic/echo)
Echoes back input - the "Hello World" of plugins.
```rust
// Simple tool that returns input
async fn echo(input: String) -> String {
    input
}
```

#### [Calculator Plugin](../../plugins/basic/calculator)
Basic arithmetic operations with proper error handling.
- Addition, subtraction, multiplication, division
- Expression evaluation
- Error handling for division by zero

#### [Random Generator](../../plugins/basic/random)
Generate random data of various types.
- Random numbers, strings, UUIDs
- Configurable distributions
- Seed support for reproducibility

#### [Text Utilities](../../plugins/basic/text-utils)
Common text processing operations.
- Case conversion, trimming, padding
- Regular expression matching
- String manipulation

### 💾 Database Plugins

Database connectors and query tools:

#### [PostgreSQL Plugin](../../plugins/database/postgresql)
Full-featured PostgreSQL integration.
- Connection pooling
- Prepared statements
- Transaction support
- Schema introspection

#### [MySQL Plugin](../../plugins/database/mysql)
MySQL/MariaDB connector.
- Query execution
- Stored procedures
- Batch operations
- SSL/TLS support

#### [MongoDB Plugin](../../plugins/database/mongodb)
NoSQL document database integration.
- CRUD operations
- Aggregation pipelines
- GridFS support
- Change streams

#### [Redis Plugin](../../plugins/database/redis)
In-memory data structure store.
- Key-value operations
- Pub/sub messaging
- Lua scripting
- Cluster support

#### [SQLite Plugin](../../plugins/database/sqlite)
Embedded database operations.
- In-memory databases
- File-based storage
- Full-text search
- JSON support

### 🌐 API Integration Plugins

Third-party service connectors:

#### [GitHub Plugin](../../plugins/api/github)
GitHub API integration.
- Repository management
- Issues and pull requests
- Actions workflow triggers
- Gist operations

#### [Slack Plugin](../../plugins/api/slack)
Slack workspace integration.
- Message posting
- Channel management
- User lookups
- File uploads

#### [Discord Plugin](../../plugins/api/discord)
Discord bot functionality.
- Server management
- Message handling
- Voice channel operations
- Webhook support

#### [OpenAI Plugin](../../plugins/api/openai)
OpenAI API wrapper.
- Chat completions
- Embeddings
- Image generation
- Function calling

#### [AWS Plugin](../../plugins/api/aws)
AWS service integration.
- S3 operations
- Lambda invocation
- DynamoDB queries
- SQS/SNS messaging

#### [Google Cloud Plugin](../../plugins/api/gcp)
GCP service connector.
- Cloud Storage
- BigQuery
- Pub/Sub
- Cloud Functions

### 🤖 AI/ML Tools

Machine learning and AI utilities:

#### [Embeddings Plugin](../../plugins/ai/embeddings)
Text embedding generation.
- Multiple model support
- Batch processing
- Similarity search
- Vector storage

#### [LLM Router Plugin](../../plugins/ai/llm-router)
Smart LLM request routing.
- Model selection
- Load balancing
- Fallback handling
- Cost optimization

#### [Image Analysis Plugin](../../plugins/ai/image-analysis)
Computer vision capabilities.
- Object detection
- OCR
- Face recognition
- Image classification

#### [Speech Plugin](../../plugins/ai/speech)
Audio processing tools.
- Speech-to-text
- Text-to-speech
- Audio transcription
- Language detection

#### [Translation Plugin](../../plugins/ai/translation)
Multi-language translation.
- 100+ language pairs
- Document translation
- Real-time translation
- Custom glossaries

### 🖥️ System Tools

Operating system interactions:

#### [File System Plugin](../../plugins/system/filesystem)
Advanced file operations.
- File watching
- Batch operations
- Compression/decompression
- Metadata management

#### [Process Manager Plugin](../../plugins/system/process)
System process control.
- Process spawning
- Signal handling
- Resource monitoring
- Job scheduling

#### [Network Tools Plugin](../../plugins/system/network)
Network utilities.
- Port scanning
- DNS lookups
- HTTP requests
- WebSocket clients

#### [System Info Plugin](../../plugins/system/info)
System information gathering.
- Hardware details
- OS information
- Resource usage
- Environment variables

### 📊 Monitoring Plugins

Observability and metrics:

#### [Metrics Collector Plugin](../../plugins/monitoring/metrics)
System and application metrics.
- CPU, memory, disk usage
- Custom metrics
- Time series data
- Alerting rules

#### [Log Aggregator Plugin](../../plugins/monitoring/logs)
Centralized log management.
- Log parsing
- Pattern matching
- Log forwarding
- Search and filter

#### [Health Check Plugin](../../plugins/monitoring/health)
Service health monitoring.
- HTTP health checks
- TCP port checks
- Custom health scripts
- Dependency tracking

#### [Trace Collector Plugin](../../plugins/monitoring/traces)
Distributed tracing.
- Span collection
- Trace correlation
- Performance analysis
- Service maps

## 🏗️ Plugin Development

### Creating a New Plugin

Use the provided template:

```bash
# Copy the template
cp -r templates/rust-plugin my-plugin
cd my-plugin

# Update Cargo.toml with your plugin details
# Implement your plugin logic in src/lib.rs

# Build your plugin
cargo build --release
```

### Plugin Structure

```rust
use mcp_protocol_sdk::plugin::*;
use async_trait::async_trait;

pub struct MyPlugin {
    config: PluginConfig,
}

#[async_trait]
impl ToolPlugin for MyPlugin {
    async fn initialize(&mut self, config: PluginConfig) -> Result<()> {
        self.config = config;
        Ok(())
    }

    async fn get_tools(&self) -> Result<Vec<Tool>> {
        Ok(vec![
            Tool {
                name: "my_tool".to_string(),
                description: Some("My custom tool".to_string()),
                input_schema: json!({
                    "type": "object",
                    "properties": {
                        "input": { "type": "string" }
                    }
                }),
            }
        ])
    }

    async fn call_tool(&self, name: &str, arguments: Value) -> Result<ToolResult> {
        match name {
            "my_tool" => {
                // Tool implementation
                Ok(ToolResult::success("Result"))
            }
            _ => Err(Error::ToolNotFound(name.to_string()))
        }
    }
}

// Export the plugin
export_plugin!(MyPlugin);
```

### Best Practices

1. **Error Handling**: Always handle errors gracefully
2. **Configuration**: Use environment variables and config files
3. **Logging**: Implement comprehensive logging
4. **Testing**: Write unit and integration tests
5. **Documentation**: Document all tools and parameters
6. **Security**: Validate inputs and sanitize outputs
7. **Performance**: Optimize for concurrent operations
8. **Versioning**: Follow semantic versioning

## 📖 Documentation

Each plugin includes:
- `README.md` - Plugin documentation
- `config.example.yaml` - Configuration template
- `tests/` - Test suite
- `examples/` - Usage examples

### Plugin Documentation Structure

```markdown
# Plugin Name

## Overview
Brief description of what the plugin does.

## Installation
How to build and install the plugin.

## Configuration
Required environment variables and config options.

## Tools
List of tools provided by the plugin.

## Examples
Code examples showing how to use the plugin.

## API Reference
Detailed documentation of each tool.
```

## 🧪 Testing

### Running Tests

```bash
# Test all plugins
make test-all

# Test specific plugin
cd plugins/calculator
cargo test

# Integration tests
cd test-server
cargo test --test integration
```

### Test Coverage

All plugins maintain >80% test coverage:

```bash
# Generate coverage report
cargo tarpaulin --out Html
```

## 🤝 Contributing

We welcome contributions! To add a new example plugin:

1. Fork the repository
2. Create a new plugin in the appropriate category
3. Follow the plugin template structure
4. Add comprehensive tests
5. Update this README with your plugin
6. Submit a pull request

See [CONTRIBUTING.md](../../CONTRIBUTING.md) for detailed guidelines.

## 📊 Plugin Statistics

| Category | Plugins | Languages | Total Downloads |
|----------|---------|-----------|---------------|
| Basic | 4 | Rust, Python | 10K+ |
| Database | 5 | Rust | 25K+ |
| API | 6 | Rust, TypeScript | 50K+ |
| AI/ML | 5 | Rust, Python | 30K+ |
| System | 4 | Rust | 15K+ |
| Monitoring | 4 | Rust | 20K+ |

## 🌟 Featured Plugins

### Plugin of the Month
**GitHub Plugin** - Most popular API integration with 15K+ downloads

### Community Choice
**PostgreSQL Plugin** - Highest rated database connector

### New & Noteworthy
**LLM Router Plugin** - Smart routing for multiple LLM providers

## 🔗 Resources

### Related Projects
- [Prism MCP SDK](https://github.com/prismworks-ai/prism-mcp-rs) - Core SDK
- [Prism Platform](https://github.com/prismworks-ai/prism-platform) - Enterprise features
- [Prism MCP Tools](https://github.com/prismworks-ai/prism-mcp-tools) - Developer tools

### External Resources
- [MCP Specification](https://modelcontextprotocol.io/docs)
- [Plugin Development Guide](https://docs.prismworks.ai/plugins)
- [Community Forum](https://forum.mcp.dev)
- [Discord Server](https://discord.gg/mcp)

## 📜 License

All example plugins are open source under the [MIT License](../../LICENSE).

## 🛡️ Security

Report security issues to security@prismworks.ai.

## 🏆 Hall of Fame

Top contributors:
1. @contributor1 - PostgreSQL Plugin
2. @contributor2 - GitHub Plugin
3. @contributor3 - LLM Router Plugin

## 📝 Changelog

See [CHANGELOG.md](../../CHANGELOG.md) for version history.

## 💬 Support

- **Documentation**: [docs.prismworks.ai](https://docs.prismworks.ai)
- **Discord**: [Join our server](https://discord.gg/mcp)
- **GitHub Issues**: [Report bugs](https://github.com/prismworks-ai/mcp-plugin-examples/issues)
- **Stack Overflow**: Tag with `mcp-plugin`

---

**© 2025 Prismworks AI, Inc.** - Empowering developers with powerful plugin examples

---

## 🌐 MCP Ecosystem

### Core Components

| Repository | Description | License |
|------------|-------------|----------|
| **[MCP Protocol SDK](https://github.com/prismworks-ai/mcp-protocol-sdk)** | Free, open-source Rust SDK with plugin system | MIT |
| **[MCP Dev Tools](https://github.com/prismworks-ai/mcp-dev)** | CLI, VS Code extension, and utilities | MIT |
| **[MCP Plugins](https://github.com/prismworks-ai/mcp-plugins)** | Community plugin implementations | Apache 2.0 |
| **[MCP Registry](https://github.com/prismworks-ai/mcp-plugins-registry)** | Plugin discovery and distribution | MIT |

### Professional Platform

For advanced features including SSO, SAML, monitoring, compliance tools, and automated marketplace distribution:

**[MCP Platform](https://prismworks.ai/platform)** - Enterprise-grade features for production deployments

### Resources

- 📚 **[Documentation](https://docs.prismworks.ai)** - Comprehensive guides and API references
- 💬 **[Discord Community](https://discord.gg/mcp-community)** - Get help and share ideas
- 🐛 **[Issue Tracker](https://github.com/prismworks-ai/prism-mcp-rs/issues)** - Report bugs and request features
- 📖 **[Blog](https://blog.prismworks.ai)** - Tutorials and announcements
- 💼 **[Professional Support](https://prismworks.ai/support)** - Enterprise support options

### Quick Start

```bash
# Install the MCP CLI
cargo install mcp-cli

# Create a new plugin
mcp new my-plugin

# Browse available plugins
mcp search
```

### Contributing

We welcome contributions! Please see our [Contributing Guidelines](../../CONTRIBUTING.md) and sign the [CLA](../../CLA.md) before submitting pull requests.

### License

This project's license information is available in the [LICENSE](../../LICENSE) file.
