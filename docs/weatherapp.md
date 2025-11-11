# Weather App - Interview Task

## Task Overview

Build a weather application using Vue 3 and PrimeVue component library. The app should allow users to search for locations and display current weather information and forecasts.

## Requirements

- **Framework**: Vue 3 (Options API)
- **UI Library**: PrimeVue components
- **State Management**: Pinia (optional)
- **Routing**: Vue Router (optional)

## Core Features

1. **Location Search**: Allow users to search for cities/locations
2. **Current Weather Display**: Show current temperature, conditions, and weather icon

## Development Guidelines

- **IDE & Tools**: Use your preferred IDE. AI assistance is allowed
- **Code Explanation**: Be prepared to explain your approach and code decisions
- **Code Quality**: Write clean, readable code with proper component structure
- **PrimeVue Components**: Utilize PrimeVue components (Cards, Buttons, Inputs, etc.) for UI

## Evaluation Criteria

- Functionality: Does the app work as expected?
- Code Quality: Is the code well-structured and maintainable?
- UI/UX: Is the interface intuitive and visually appealing?
- Problem Solving: How did you approach challenges?
- Communication: Can you explain your decisions and code?

## Getting Started

1. Review the API documentation below
2. Start coding

## Full Documentation

For complete API reference: https://www.weatherapi.com/docs/


## API Key

```
3aaca0ad6a004647a39174307251111
```

**Note**: This API key may expire. Contact Sam Araiza to renew or generate your own at https://www.weatherapi.com

## Base URL

```
https://api.weatherapi.com/v1
```

## Quick Examples

### Current Weather

```javascript
const apiKey = '3aaca0ad6a004647a39174307251111'
const url = `https://api.weatherapi.com/v1/current.json?key=${apiKey}&q=London`
// https://api.weatherapi.com/v1/current.json?key=3aaca0ad6a004647a39174307251111&q=London
```

**Query Parameters**:
- `key` (required): API key
- `q` (required): City name, zip code, or `auto:ip` for user's location
- `aqi` (optional): `aqi=yes` for air quality data

### Forecast (1-14 days)
**Note**: Key may be limited to 3 days for free trial

```javascript
const url = `https://api.weatherapi.com/v1/forecast.json?key=${apiKey}&q=London&days=7`
```

**Query Parameters**:
- `key` (required): API key
- `q` (required): Location
- `days` (required): 1-14

### Search Cities

```javascript
const url = `https://api.weatherapi.com/v1/search.json?key=${apiKey}&q=lond`
```

