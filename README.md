# Cafe Manager

A TypeScript-based coffee shop management system that demonstrates several design patterns and modern TypeScript features.

## Overview

Cafe Manager is a system designed to manage coffee orders, ingredients, and apply customizations to orders. It showcases multiple design patterns and TypeScript features:

- **Singleton Pattern**: For inventory management
- **Factory Pattern**: For coffee creation
- **Decorator Pattern**: For adding customizations to coffee orders
- **DAO Pattern**: For data persistence
- **Async/Await**: For handling asynchronous operations

## Features

- Create different types of coffee (Espresso, Latte, Cappuccino)
- Add customizations dynamically (milk, sugar, whipped cream)
- Track ingredient inventory
- Save and retrieve order history
- Calculate prices based on coffee type and customizations

## Project Structure

```
cafe-manager/
├── src/
│   ├── coffee.ts        - Base Coffee interface
│   ├── types.ts         - Coffee type implementations
│   ├── decorators.ts    - Coffee customization decorators
│   ├── factory.ts       - Coffee creation factory
│   ├── inventory.ts     - Singleton inventory manager
│   ├── dao.ts           - Data Access Object for IndexedDB
│   ├── dao-mock.ts      - Mock DAO for testing
│   └── main.ts          - Main application entry point
├── package.json
└── tsconfig.json
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/saidrassai/cafe_manager.git
cd cafe_manager
```

2. Install dependencies:
```bash
npm install
```

3. Build the project:
```bash
npx tsc
```

## Usage

```typescript
// Create a coffee order
const coffee = CoffeeFactory.createCoffee("cappuccino");

// Add customizations
const customizedCoffee = new MilkDecorator(
  new SugarDecorator(
    new WhippedCreamDecorator(coffee)
  )
);

// Get description and price
console.log(customizedCoffee.getDescription()); // "Cappuccino, Milk, Sugar, Whipped Cream"
console.log(customizedCoffee.getPrice()); // 4.9 (3.5 + 0.5 + 0.2 + 0.7)
```

## Design Patterns Implemented

1. **Singleton Pattern**: `InventoryManager` ensures only one inventory instance exists
2. **Factory Pattern**: `CoffeeFactory` creates coffee objects without exposing creation logic
3. **Decorator Pattern**: `CoffeeDecorator` and its subclasses add features to coffee objects
4. **DAO Pattern**: `CoffeeDAO` abstracts data access layer

## Technologies Used

- TypeScript
- IndexedDB (with mock implementation)
- Node.js
## diagram UML
![diagram](https://github.com/user-attachments/assets/8088415d-6f72-451d-aef8-a9f58f0222c1)

