# Portfolio Manager Mobile

Mobile investment portfolio application built with React Native, Expo, and TypeScript, focused on portfolio tracking, persistent data, market synchronization, state management, testing, and production-oriented mobile workflows.

## Overview

This project is a mobile portfolio management application designed to help users track investments, monitor portfolio value, and work with market-driven financial data through a responsive mobile interface.

The application combines persistent local data with remote market information, using modern state-management and server-state patterns to keep the experience reliable across loading, error, offline, and synchronization scenarios.

The goal is to demonstrate practical mobile engineering with React Native, Expo, TypeScript, testing, performance, and deployment workflows.

## Features

- Mobile investment portfolio management
- Persistent local portfolio data
- Market-price synchronization
- Portfolio value calculations
- Asset-level performance tracking
- Loading, error, and offline states
- Shared application state with Zustand
- Server-state management with TanStack Query
- Query caching and refetching
- Mobile-focused performance optimization
- Unit and component testing
- Automated validation through GitHub Actions
- Expo Application Services workflows

## Tech Stack

- React Native
- Expo
- TypeScript
- Zustand
- TanStack Query
- Vitest
- React Native Testing Library
- Expo Application Services (EAS)
- GitHub Actions

## Architecture

The application separates local application state from remote server state.

```text
User
↓
React Native UI
↓
Application State
↓
Zustand

External Market Data
↓
TanStack Query
↓
Cached Server State
↓
Portfolio Calculations
↓
UI
```

Persistent portfolio data and remote market data are managed independently and combined through derived calculations when necessary.

## State Management

The project separates state according to responsibility.

### Application State

Zustand is used for shared client-side state such as:

- portfolio information
- selected assets
- local UI state
- persisted portfolio data

### Server State

TanStack Query is used for remote data such as:

- asset prices
- market information
- request status
- caching
- retries
- refetching

This separation avoids mixing local application state with remote asynchronous data.

## Portfolio Calculations

The application combines stored portfolio data with synchronized market prices.

Example:

```text
Asset Quantity
+
Current Market Price
↓
Current Asset Value
```

Portfolio-level calculations can include:

- total portfolio value
- asset allocation
- individual asset value
- performance metrics
- derived portfolio summaries

## Data Persistence

Portfolio information is persisted locally so that users do not lose their data between application sessions.

The persistence layer is responsible for:

- restoring saved portfolio data
- updating local state
- handling missing or invalid persisted data
- keeping local data independent from market API availability

## Market Synchronization

Remote market data is managed through TanStack Query.

The synchronization flow includes:

```text
Application Starts
↓
Load Persisted Portfolio
↓
Fetch Market Prices
↓
Cache Response
↓
Combine Local + Remote Data
↓
Update Portfolio View
```

The application handles:

- loading states
- stale data
- refetching
- API failures
- offline conditions

## Offline and Error States

The mobile interface is designed to remain understandable when external services are unavailable.

Possible states include:

- loading
- successful synchronization
- stale market data
- offline mode
- API failure
- missing portfolio data

The UI should communicate these states clearly rather than failing silently.

## Performance

Mobile performance practices include:

- reducing unnecessary renders
- memoization where justified
- controlled data refetching
- efficient portfolio calculations
- optimized list rendering
- minimizing unnecessary network requests

Performance improvements are introduced based on actual application behavior rather than premature optimization.

## Testing

The project includes multiple testing layers.

### Unit Testing

Vitest is used for logic such as:

- portfolio calculations
- formatters
- utility functions
- derived state

### Component Testing

React Native Testing Library is used for:

- portfolio views
- loading states
- error states
- user interactions
- state-driven UI behavior

## CI/CD

GitHub Actions is used to automate project validation.

Typical pipeline:

```text
Push / Pull Request
↓
Install Dependencies
↓
Lint
↓
Typecheck
↓
Unit / Component Tests
↓
Build Validation
```

## Expo Application Services

Expo Application Services (EAS) is used for mobile build and delivery workflows.

EAS can support:

- development builds
- preview builds
- production builds
- build configuration
- application distribution

## Running Locally

### Prerequisites

Make sure you have installed:

- Node.js
- npm
- Expo-compatible development environment

You can run the application using a physical device with Expo Go or through an available simulator/emulator depending on the project configuration.

### Installation

```bash
git clone https://github.com/igor-souza-engineer/portfolio-manager-mobile.git
cd portfolio-manager-mobile
npm install
```

### Environment Variables

If the project requires external market APIs, create a local environment file based on the provided example.

```bash
cp .env.example .env
```

Configure the required values without committing real credentials.

Example:

```env
EXPO_PUBLIC_MARKET_API_URL=
EXPO_PUBLIC_MARKET_API_KEY=
```

### Start the Application

```bash
npm start
```

or:

```bash
npx expo start
```

Follow the Expo CLI instructions to open the application on a supported device, emulator, or simulator.

## Usage

1. Open the application.
2. Add or load portfolio assets.
3. Enter the relevant asset quantities.
4. The application restores persistent portfolio data.
5. Market prices are synchronized from the configured data source.
6. Portfolio values are recalculated using current market data.
7. Review asset-level and portfolio-level information.
8. If network access is unavailable, the interface preserves local portfolio data and handles remote-data failure states.

## Deployment

The project is designed to use Expo Application Services for build and delivery workflows.

Production deployment should include:

- environment-specific configuration
- secure API configuration
- production build validation
- EAS build profiles
- automated validation through CI
- mobile performance checks

## Reliability

The application includes production-oriented practices such as:

- persistent local state
- loading and error handling
- remote-data retry strategies
- query caching
- offline-aware behavior
- separation between local and server state
- build validation through CI

## Security

Security considerations include:

- no API keys committed to GitHub
- environment-based configuration
- `.env` excluded from version control
- `.env.example` containing only placeholders
- no sensitive user credentials stored unnecessarily
- validation of external data before use

## Repository Structure

```text
portfolio-manager-mobile/
├── src/
│   ├── app/
│   ├── components/
│   ├── features/
│   ├── hooks/
│   ├── services/
│   ├── store/
│   ├── types/
│   └── utils/
├── tests/
├── .github/
│   └── workflows/
├── .env.example
├── app.json
├── eas.json
├── package.json
└── README.md
```

The repository structure should evolve with the application and avoid unnecessary abstractions.

## Project Goals

This project was built to demonstrate practical experience with:

- React Native
- Expo
- TypeScript
- mobile application development
- state management
- server-state management
- persistent data
- market-data synchronization
- offline and error states
- portfolio calculations
- testing
- mobile performance
- Expo Application Services
- GitHub Actions
- CI/CD

## License

This project is intended for educational and portfolio purposes.
