# Movie Gallery App - Interview Task

## Task Overview

Build a Netflix-style movie gallery application using Vue 3 and PrimeVue component library. The app should allow users to browse, search, and view movie/TV show information with a visually appealing gallery interface.

## Requirements

- **Framework**: Vue 3 (Options API)
- **UI Library**: PrimeVue components
- **State Management**: Pinia (optional)
- **Routing**: Vue Router (optional)

## Core Features

1. **Movie Gallery**: Display movies/TV shows in a grid or carousel layout with thumbnails
2. **Search Functionality**: Allow users to search for movies/TV shows

## Development Guidelines

- **IDE & Tools**: Use your preferred IDE. AI assistance is allowed
- **Code Explanation**: Be prepared to explain your approach and code decisions
- **Code Quality**: Write clean, readable code with proper component structure
- **PrimeVue Components**: Utilize PrimeVue components (Cards, DataView, Dialog, etc.) for UI
- **Thumbnails**: Use the `poster_path` field to display movie thumbnails (see Image URLs section)

## Evaluation Criteria

- Functionality: Does the app work as expected?
- Code Quality: Is the code well-structured and maintainable?
- UI/UX: Is the interface intuitive and visually appealing?
- Problem Solving: How did you approach challenges?
- Communication: Can you explain your decisions and code?

## Getting Started

1. Review the API documentation below
3. Start coding

## Full Documentation

For complete API reference: https://developers.themoviedb.org/3

## API Credentials

**API Key**:
```
93bb45e02dd1461a6086e5c473c36a9f
```

**Access Token**:
```
eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI5M2JiNDVlMDJkZDE0NjFhNjA4NmU1YzQ3M2MzNmE5ZiIsIm5iZiI6MTc2Mjg4Mzc0NC4wNDgsInN1YiI6IjY5MTM3OGEwNjAwZGIxNjUyYmQyNjMwZiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.Pe8JWGv5TsPm_wVKJn-0KECgEwR6A9XigYP_fUy-2S0
```

**Note**: These credentials may expire. Contact Sam Araiza to renew or generate your own at https://www.themoviedb.org

## Base URL

```
https://api.themoviedb.org/3
```

## Authentication

Use API key as query parameter: `?api_key=YOUR_API_KEY`

Or use Bearer token in header: `Authorization: Bearer YOUR_ACCESS_TOKEN`

## Image URLs (Thumbnails/Posters)

**Image Base URL**: `https://image.tmdb.org/t/p/`

**Available Sizes**:
- `w92` - Small thumbnail
- `w154` - Small poster
- `w185` - Medium thumbnail (good for galleries)
- `w342` - Medium poster
- `w500` - Large poster (recommended for galleries)
- `w780` - Very large poster
- `original` - Full resolution

**How to Build Image URL**:
```javascript
const posterPath = movie.poster_path // e.g., "/abc123.jpg"
const imageUrl = `https://image.tmdb.org/t/p/w500${posterPath}`
```

**Example**:
- If `poster_path` = `/abc123.jpg`
- Full URL = `https://image.tmdb.org/t/p/w500/abc123.jpg`

**Note**: `poster_path` is included in all search/popular/trending results. Use `w500` for gallery thumbnails.

## Quick Examples

### Search Movies

```javascript
const apiKey = '93bb45e02dd1461a6086e5c473c36a9f'
const query = 'inception'
const url = `https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${query}`
// https://api.themoviedb.org/3/search/movie?api_key=93bb45e02dd1461a6086e5c473c36a9f&query=inception
```

**Query Parameters**:
- `api_key` (required): API key
- `query` (required): Search query
- `page` (optional): Page number (default: 1)

### Search TV Shows

```javascript
const url = `https://api.themoviedb.org/3/search/tv?api_key=${apiKey}&query=${query}`
```

### Popular Movies

```javascript
const url = `https://api.themoviedb.org/3/movie/popular?api_key=${apiKey}`
```

### Trending (Today)

```javascript
// Trending movies
const url = `https://api.themoviedb.org/3/trending/movie/day?api_key=${apiKey}`
```

**Time periods**: `day` or `week`

### Movie Details

```javascript
const movieId = 550 // Fight Club
const url = `https://api.themoviedb.org/3/movie/${movieId}?api_key=${apiKey}`
```

### Get Images (Posters/Backdrops)

```javascript
// Movie images
const url = `https://api.themoviedb.org/3/movie/${movieId}/images?api_key=${apiKey}`
// https://api.themoviedb.org/3/movie/550/images?api_key=93bb45e02dd1461a6086e5c473c36a9f
```

## Response Structure

**Search/Popular/Trending Results**:
- `results[]` - Array of movies/TV shows
  - `id`: Unique ID
  - `title` (movies) / `name` (TV): Title
  - `overview`: Description
  - `poster_path`: Poster image path (e.g., `/abc123.jpg`) - **Use this for thumbnails!**
    - Full thumbnail URL: `https://image.tmdb.org/t/p/w500${poster_path}`
  - `backdrop_path`: Backdrop image path (for detail pages)
  - `release_date` (movies) / `first_air_date` (TV): Release date
  - `vote_average`: Rating (0-10)
  - `vote_count`: Number of votes
  - `genre_ids[]`: Array of genre IDs

**Movie/TV Details**:
- `title` / `name`: Title
- `overview`: Description
- `genres[]`: Array of genre objects
- `runtime` (movies) / `episode_run_time[]` (TV): Duration
- `production_companies[]`: Studios
- `vote_average`: Rating
- `poster_path`, `backdrop_path`: Image paths