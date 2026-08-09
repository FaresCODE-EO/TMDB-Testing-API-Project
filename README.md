# TMDB Testing API Project

A Postman collection for testing **The Movie Database (TMDB) API v3**. It covers
searching, fetching details, credits, genres, discovery, and watchlist management
for movies, TV shows, and people.

## Overview

- **Base URL:** `https://api.themoviedb.org/3` (set via a `base_url` variable)
- **Auth:** Bearer token (TMDB API Read Access Token)
- **Environment:** `TMDB Environment` (holds `base_url`, `person_id`, and your token)

## Requests

| # | Request | Method | Description |
|---|---------|--------|-------------|
| 1 | Testing Request | GET | Sample call to `/movie/550` for a quick sanity check |
| 2 | Search Movies by Keyword | GET | Search movies by a keyword/query |
| 3 | Search TV Shows by Name | GET | Search TV shows by name |
| 4 | Get Movies Details by Movie ID | GET | Full details for a movie |
| 5 | Get Movie Credits | GET | Cast and crew for a movie |
| 6 | Get Popular Movies | GET | Currently popular movies |
| 7 | Get TV Show Details by ID | GET | Full details for a TV show |
| 8 | Get Movie Genres List | GET | List of official movie genres |
| 9 | Discover
