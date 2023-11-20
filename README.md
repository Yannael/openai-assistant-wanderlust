# OpenAI assistant Wanderlust

Basic recreation of OpenAI's DevDay Wanderlust demo app. It relies on Gradio and the new OpenAI Assistants API. [Huggingface repository](https://huggingface.co/spaces/Yannael/openai-assistant-wanderlust)

The code is inspired by the implementation of [Fanilo Andrianasolo using Streamlit](https://www.youtube.com/watch?v=tLeqCDKgEDU)

## Open Assistant configuration

### Instructions

'You are a helpful assistant that can write and execute code, and has access to a digital map to update information'

### Signature for `update-map`:


```
{
  "name": "update_map",
  "description": "Update map to center on a particular location",
  "parameters": {
    "type": "object",
    "properties": {
      "longitude": {
        "type": "number",
        "description": "Longitude of the location to center the map on"
      },
      "latitude": {
        "type": "number",
        "description": "Latitude of the location to center the map on"
      },
      "zoom": {
        "type": "number",
        "description": "Zoom level of the map"
      }
    },
    "required": [
      "longitude",
      "latitude",
      "zoom"
    ]
  }
}
```

### Signature for `add-markers`:

```
{
  "name": "add_markers",
  "description": "Add list of markers to the map",
  "parameters": {
    "type": "object",
    "properties": {
      "longitudes": {
        "type": "array",
        "items": {
          "type": "number"
        },
        "description": "List of longitude of the location to each marker"
      },
      "latitudes": {
        "type": "array",
        "items": {
          "type": "number"
        },
        "description": "List of latitude of the location to each marker"
      },
      "labels": {
        "type": "array",
        "items": {
          "type": "string"
        },
        "description": "List of text to display on the location of each marker"
      }
    },
    "required": [
      "longitudes",
      "latitudes",
      "labels"
    ]
  }
}
```