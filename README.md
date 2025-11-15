# Philippine Earthquake API

A simple and efficient FastAPI backend that serves recent earthquake data for the Philippines region. The data is sourced in real-time from the [U.S. Geological Survey (USGS) Earthquake API](https://earthquake.usgs.gov/fdsnws/event/1/).

This backend is designed to be used by client applications, such as a Flutter mobile app, to display earthquake information.

## Features

- **Real-time Data**: Fetches the latest earthquake events from the last 7 days.
- **Geographically Focused**: Data is filtered specifically for the Philippines using a geographic bounding box.
- **Fast and Modern**: Built with FastAPI for high performance.
- **Interactive Docs**: Automatic, interactive API documentation powered by Swagger UI and ReDoc.

## API Endpoint

### Get Recent Earthquakes

- **GET** `/api/v1/earthquakes/philippines`

  Returns a GeoJSON FeatureCollection of earthquake events in the Philippines from the last 7 days.

  **Success Response (200 OK)**:
  - **Content-Type**: `application/json`
  - **Body**: A JSON object matching the USGS GeoJSON format. See [USGS documentation](https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php) for details on the structure.

  **Error Responses**:
  - `502 Bad Gateway`: If the backend fails to get a valid response from the upstream USGS API.
  - `503 Service Unavailable`: If the backend cannot connect to the upstream USGS API.

## Getting Started

### Prerequisites

- Python 3.8+
- `pip` (Python package installer)

### Installation

1.  **Set up the project files:**
    Ensure `main.py`, `models.py`, and `requirements.txt` are in the same directory.

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### Running the Server

Use `uvicorn` to run the FastAPI application:

```bash
uvicorn main:app --reload
```

- `--reload` enables auto-reloading, which is useful for development. The server will restart automatically after you make code changes.

The API will be available at `http://127.0.0.1:8000`.

### Exploring the API

Once the server is running, you can access the interactive documentation in your browser:

- **Swagger UI**: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- **ReDoc**: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

These interfaces allow you to explore and test the API endpoints directly from your browser.
