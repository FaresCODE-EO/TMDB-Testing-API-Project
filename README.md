# TMDB Testing API Project

A Postman collection for testing **The Movie Database (TMDB) API v3**. It provides a set of ready-to-use requests for searching, retrieving details, credits, genres, discovery, and watchlist management across movies, TV shows, and people. The collection is intended as a learning and testing playground for the TMDB REST API.

**Postman Share Link Collection** `https://fm502601-7820399.postman.co/workspace/Fares-Mohamed's-Workspace~5c800b2d-7909-4da5-8190-16e636c41821/collection/56724135-6c7fcb31-db7b-40e6-9cfd-b52fe887546c?action=share&creator=56724135&active-environment=56724135-6e9c8d75-e4ea-44b6-8964-cb620fa8ca01`


---

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Authentication](#authentication)
- [Environment & Variables](#environment--variables)
- [Requests](#requests)
- [Running the Collection](#running-the-collection)
- [Project Structure](#project-structure)
- [Security Notes](#security-notes)
- [Resources](#resources)

---

## Overview

- **API:** The Movie Database (TMDB) API v3
- **Base URL:** `https://api.themoviedb.org/3`
- **Protocol:** HTTPS / REST
- **Auth:** Bearer token (TMDB API Read Access Token)
- **Format:** JSON
- **Requests:** 12 endpoints (see table below)
- **Postman Documentation** `https://documenter.getpostman.com/view/56724135/2sBY4VLxvZ`
- **Postman Share Link Collection** `https://fm502601-7820399.postman.co/workspace/Fares-Mohamed's-Workspace~5c800b2d-7909-4da5-8190-16e636c41821/collection/56724135-6c7fcb31-db7b-40e6-9cfd-b52fe887546c?action=share&creator=56724135&active-environment=56724135-6e9c8d75-e4ea-44b6-8964-cb620fa8ca01`

The collection uses a `{{base_url}}` variable so you can switch between environments easily, and Bearer token authentication set at the collection level (inherited by most requests).

---

## Prerequisites

- [Postman](https://www.postman.com/downloads/) (desktop app or web)
- A free [TMDB account](https://www.themoviedb.org/signup)
- A TMDB **API Read Access Token** (v4 auth) — get it from your [TMDB API settings](https://www.themoviedb.org/settings/api)

---

## Getting Started

1. **Clone this repository:**
   ```bash
   git clone https://github.com/<your-username>/tmdb-testing-api.git
   cd tmdb-testing-api
   ```
2. **Import into Postman:**
   - Open Postman → `Import` → drag in the exported collection `.json` file.
   - Also import the `TMDB Environment` if it is included.
3. **Select the environment** (`TMDB Environment`) from the environment dropdown (top-right).
4. **Set your credentials** (see [Authentication](#authentication)).
5. Send the **Testing Request** to verify everything works.

---

## Authentication

The collection uses **Bearer token** auth defined at the collection level. Most requests inherit this automatically.

- Get your **API Read Access Token** from https://www.themoviedb.org/settings/api
- Set it as the collection's Bearer token, or store it in a variable / Postman Vault.

> Note: A few requests currently reference vault variables (e.g. `{{auth_secret_0764}}`, `{{json_web_token_0764}}`). Make sure those resolve to your valid TMDB token, or switch them to inherit the collection auth.

---

## Environment & Variables

| Variable | Scope | Description |
|----------|-------|-------------|
| `base_url` | Environment | Base URL for the API, e.g. `https://api.themoviedb.org/3` |
| `person_id` | Environment | A TMDB person ID used by the person details request |
| `auth_secret_0764` | Vault | TMDB token reference used by some requests |
| `json_web_token_0764` | Vault | TMDB token reference used by some requests |

---

## Requests

| # | Request | Method | Endpoint | Description |
|---|---------|--------|----------|-------------|
| 1 | Testing Request | GET | `{{base_url}}/movie/550` | Quick sanity check against a known movie (Fight Club) |
| 2 | Search Movies by Keyword | GET | `{{base_url}}/search/movie?query={keyword}` | Search movies by keyword/title |
| 3 | Search TV Shows by Name | GET | `{{base_url}}/search/tv?query={name}` | Search TV shows by name |
| 4 | Get Movies Details by Movie ID | GET | `{{base_url}}/movie/{movie_id}` | Full details for a specific movie |
| 5 | Get Movie Credits | GET | `{{base_url}}/movie/{movie_id}/credits` | Cast and crew for a movie |
| 6 | Get Popular Movies | GET | `{{base_url}}/movie/popular` | Currently popular movies |
| 7 | Get TV Show Details by ID | GET | `{{base_url}}/tv/{tv_id}` | Full details for a TV show |
| 8 | Get Movie Genres List | GET | `{{base_url}}/genre/movie/list` | Official list of movie genres |
| 9 | Discover Movies By Genre | GET | `{{base_url}}/discover/movie?with_genres={genre_id}` | Discover movies filtered by genre |
| 10 | Get Now Playing Movies | GET | `{{base_url}}/movie/now_playing` | Movies currently in theaters |
| 11 | Get Person Details (Actor/Director) | GET | `{{base_url}}/person/{{person_id}}` | Details for a person (actor/director) |
| 12 | Add a Movie to Watchlist | POST | `{{base_url}}/account/{account_id}/watchlist` | Add/remove a movie from a watchlist |

> Note: Several requests in the collection do not yet have URLs configured. The endpoints above reflect the correct TMDB v3 paths so you can fill them in. "Add a Movie to Watchlist" should use **POST** with a JSON body `{ "media_type": "movie", "media_id": 550, "watchlist": true }`, even though it is currently saved as GET.

---

## Running the Collection

You can run the whole collection with the Postman Collection Runner:

1. Click the collection → **Run**.
2. Select the requests and iteration count.
3. (Optional) Attach a data file for data-driven runs.
4. Click **Run TMDB Testing API Project**.

You can also automate runs on a schedule with a Postman **Monitor**.
