# StackVault

A Clarinet-based smart contract project built on the Stacks blockchain for secure asset management and vault operations.

## 📋 Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Quick Start](#quick-start)
- [Development](#development)
- [Testing](#testing)
- [Network Configuration](#network-configuration)
- [Smart Contracts](#smart-contracts)
- [Contributing](#contributing)
- [License](#license)
- [Resources](#resources)

## Overview

StackVault is a Stacks blockchain smart contract project that leverages Clarinet for development, testing, and deployment. It provides a robust framework for building and testing Clarity smart contracts with multiple network environments (Devnet, Testnet, Mainnet).

**Key Features:**
- Full Clarinet integration for smart contract development
- Comprehensive testing suite with Vitest and Clarinet SDK
- Multi-network configuration (Devnet, Testnet, Mainnet)
- TypeScript support for contract testing
- Pre-configured test accounts with balances for development
- Coverage and cost analysis reporting

## Requirements

- **Node.js** 18 or higher
- **npm** 9 or higher (comes with Node.js)
- **Clarinet** 1.0+ (Stacks smart contract development framework)
- **Git** for version control

## Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd StackVault

2. Install Dependencies

npm install
This will install all necessary dependencies including:

Clarinet SDK
Vitest testing framework
TypeScript and type definitions
Stacks transaction utilities
3. Verify Installation

npm test
3. Verify Installation

npm test
Project Structure

StackVault/├── contracts/                    # Clarity smart contract files (.clar)│   └── (add your contracts here)├── tests/                        # TypeScript test files│   └── (add your tests here)├── settings/                     # Network-specific configurations│   ├── Devnet.toml              # Development environment│   ├── Testnet.toml             # Testing environment│   └── Mainnet.toml             # Production environment├── Clarinet.toml                # Clarinet project configuration├── package.json                 # Node.js project manifest├── tsconfig.json                # TypeScript configuration├── vitest.config.js             # Vitest configuration├── README.md                     # This file└── .gitignore                   # Git ignore rules
Directory Details
Directory	Purpose
contracts	Contains all Clarity smart contract files (.clar extension)
tests	Contains TypeScript test files for unit and integration testing
settings	Network configuration files for different blockchain environments
Quick Start
Run Tests

# Run all tests oncenpm test# Run tests with coverage and cost analysisnpm run test:report# Run tests in watch mode (re-runs on file changes)npm run test:watch
Create Your First Contract
Create a contract file:


touch contracts/my-contract.clar
Add contract code (example):


;; my-contract.clar(define-public (get-message)  (ok "Hello, StackVault!"))
Register in Clarinet.toml:


[contracts.my-contract]path = "contracts/my-contract.clar"epoch = "latest"
Create a test file:


touch tests/my-contract.test.ts
Run tests:


npm test
Development
Available NPM Scripts

npm test              # Run all tests oncenpm run test:report   # Run tests with coverage and cost analysisnpm run test:watch    # Run tests in watch mode
Workflow
Write smart contract in contracts directory
Register contract in Clarinet.toml
Write tests in tests directory
Run tests to verify contract behavior
Debug using test output and coverage reports
Best Practices
Keep contracts focused on a single responsibility
Write tests for all public functions
Use meaningful function and variable names
Comment complex logic in your Clarity code
Test edge cases and error conditions
Testing
Testing Framework
StackVault uses Vitest with the Clarinet SDK for testing. Tests are written in TypeScript and provide:

Unit testing capabilities
Integration testing with contract interactions
Coverage reporting
Cost analysis (gas/blockchain operations)
Fast test execution
Test Structure Example

import { describe, it, expect, beforeEach } from 'vitest';import { initSimnet } from '@hirosystems/clarinet-sdk';describe('my-contract', () => {  let simnet: ReturnType<typeof initSimnet>;  beforeEach(() => {    simnet = initSimnet();  });  it('should execute successfully', () => {    const result = simnet.callPublicFn('my-contract', 'get-message', []);    expect(result.isOk()).toBe(true);  });});
Running Tests

# Single runnpm test# With coverage and cost analysisnpm run test:report# Watch mode (automatic re-run on file changes)npm run test:watch
Network Configuration
Environment Files
Located in settings, these files configure blockchain parameters for each environment:

Devnet (settings/Devnet.toml)
Purpose: Local development
Pre-configured Accounts:
deployer: Main contract deployer account
wallet_1: Test account with initial balance
Features: Pre-funded accounts for development and testing
Testnet (settings/Testnet.toml)
Purpose: Testing before mainnet deployment
Network: Stacks testnet
Use Case: Integration testing with real blockchain behavior
Mainnet (settings/Mainnet.toml)
Purpose: Production deployment
Network: Stacks mainnet
Use Case: Live smart contracts with real value
Account Details
Development accounts include:

STX Balance: 100,000,000,000,000 (per account)
sBTC Balance: 1,000,000,000 (per account)
Mnemonics and secret keys provided for manual account access
Smart Contracts
Creating Contracts
File Location: contracts directory
File Extension: .clar (Clarity language)
Naming Convention: contract-name.clar
Contract Registration
In Clarinet.toml:


[contracts.contract-name]path = "contracts/contract-name.clar"epoch = "latest"
Basic Contract Example

;; contracts/counter.clar(define-data-var counter uint u0)(define-public (increment)  (begin    (var-set counter (+ (var-get counter) u1))    (ok (var-get counter))))(define-read-only (get-counter)  (ok (var-get counter)))
Clarity Resources
Clarity Documentation
Clarity Guide
Hiro Clarinet Docs
Key Dependencies
Package	Version	Purpose
@hirosystems/clarinet-sdk	^3.6.0	Official SDK for testing Clarinet projects
@stacks/transactions	^7.2.0	Stacks transaction utilities and primitives
vitest	^3.2.4	Fast unit test framework
vitest-environment-clarinet	^2.3.0	Clarinet environment for Vitest
@types/node	^24.4.0	TypeScript types for Node.js
chokidar-cli	^3.0.0	File watcher for watch mode
Contributing
Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request
License
ISC

Resources
Official Documentation
Stacks Documentation
Clarinet Documentation
Clarity Language Guide
Community
Stacks Discord
Stacks Forum
GitHub Issues
Tools & IDEs
Clarinet VS Code Extension
Stacks Explorer
Troubleshooting
Tests Not Running

# Clear dependencies and reinstallrm -rf node_modulesnpm installnpm test
Contract Not Recognized
Ensure contract is registered in Clarinet.toml
Check file path and naming conventions
Verify .clar file extension
TypeScript Errors

# Regenerate typesnpm installnpm test
Last Updated: February 2026

For questions or issues, please open a GitHub issue or check the resources above.


This comprehensive README includes detailed sections on getting started, project structure, testing, network configuration, and additional resources. You can copy this entire content into your README.md file.This comprehensive README includes detailed sections on getting started, project structure, testing, network configuration, and additional resources. You can copy this entire content into your README.md file.
