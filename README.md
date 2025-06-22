# alx-project-0x14

## API Overview

The MoviesDatabase API provides access to a comprehensive and frequently updated database of over 9 million movie, series, and episode titles. It offers detailed information, ratings, cast, crew, and more. The API supports flexible filtering, searching, and sorting, making it ideal for developers building movie-related applications. Data is updated weekly for new titles and daily for ratings and episode highlights.

## Version

The API version is not explicitly stated in the documentation, but it is actively maintained and updated as of 2025.

## Available Endpoints

- **/titles**: Returns an array of titles (movies, series, episodes) based on optional filters and sorting.
- **/x/titles-by-ids**: Returns titles for a provided array of IMDb IDs.
- **/titles/{id}**: Returns detailed information for a specific title by IMDb ID.
- **/titles/{id}/ratings**: Returns rating and vote count for a specific title.
- **/titles/series/{id}**: Returns episodes for a series, including episode and season numbers.
- **/titles/seasons/{id}**: Returns the number of seasons for a series.
- **/titles/series/{id}/{season}**: Returns episodes for a specific season of a series.
- **/titles/episode/{id}**: Returns details for a specific episode.
- **/titles/x/upcoming**: Returns upcoming titles based on filters.
- **/titles/search/keyword/{keyword}**: Searches titles by keyword.
- **/titles/search/title/{title}**: Searches titles by title or partial title.
- **/titles/search/akas/{aka}**: Searches titles by alternative names (akas).
- **/actors**: Returns an array of actors based on filters.
- **/actors/{id}**: Returns details for a specific actor by IMDb ID.
- **/title/utils/titleType**: Returns available title types.
- **/title/utils/genres**: Returns available genres.
- **/title/utils/lists**: Returns available lists for the 'list' query parameter.

## Request and Response Format

All endpoints return a JSON object. The main data is under the `results` key. Endpoints with pagination include `page`, `next`, and `entries` keys.

**Example Request:**

```
GET https://moviesdatabase.p.rapidapi.com/titles?limit=2&genre=Action
Headers:
  X-RapidAPI-Key: YOUR_API_KEY
  X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

**Example Response:**

```
{
  "results": [
    {
      "id": "tt1234567",
      "titleText": "Example Movie",
      "primaryImage": "...",
      "titleType": "movie",
      "releaseDate": "2023-01-01",
      "genres": ["Action"],
      ...
    },
    ...
  ],
  "page": 1,
  "next": 2,
  "entries": 2
}
```

## Authentication

All requests require authentication via RapidAPI. You must include the following headers in each request:

- `X-RapidAPI-Key`: Your RapidAPI API key
- `X-RapidAPI-Host`: moviesdatabase.p.rapidapi.com

## Error Handling

Common error responses include:

- **401 Unauthorized**: Missing or invalid API key.
- **429 Too Many Requests**: Rate limit exceeded.
- **400 Bad Request**: Invalid parameters or malformed request.
- **404 Not Found**: Resource not found (e.g., invalid ID).

Handle errors by checking the HTTP status code and the error message in the response. Example error response:

```
{
  "message": "Invalid API key."
}
```

## Usage Limits and Best Practices

- The API enforces rate limits as defined by your RapidAPI subscription plan. Exceeding these limits will result in 429 errors.
- Use pagination parameters (`limit`, `page`) to manage large result sets efficiently.
- Cache frequent queries to reduce API calls and improve performance.
- Always validate and sanitize user input before sending requests to the API.
- Review the API documentation for updates and new features regularly.
