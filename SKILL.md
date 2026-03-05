---
name: bobby-lyc-post
description: Publish a post to bobby via OpenAPI
---

# bobby Post Skill

## Overview

This skill publishes text content to bobby through the bobby OpenAPI.

## Use Cases

- Publish text posts to bobby
- Automate content publishing workflows

## Input Parameters

| Name         | Type   | Required | Description                          |
|--------------|--------|----------|--------------------------------------|
| bodyTextOnly | string | Yes      | The text content of the post         |
| apiKey       | string | Yes      | X-Square-OpenAPI-Key for authentication |
| traceId      | string | No       | Custom x-trace-id for request tracing |

Example:

```json
{
  "bodyTextOnly": "Hello bobby!",
  "apiKey": "a2f169f0220b4951bbeec6e751bb2d48",
  "traceId": "6cf74ea281af490cb5b4bedfaa088545"
}
```

## Output Format

Success:

```json
{
  "code": "000000",
  "message": "success",
  "data": null,
  "success": true
}
```

Failure:

```json
{
  "code": "220009",
  "message": "Daily post limit exceeded for OpenAPI",
  "data": null,
  "success": false
}
```

## Technical Details

- Method: POST
- Endpoint: https://www.binance.com/bapi/composite/v1/public/pgc/openApi/content/add
- Content-Type: application/json
- Required Headers:
  - `X-Square-OpenAPI-Key`: API key for authentication
  - `x-trace-id`: Request trace ID
  - `x-gray-env`: gray

## Notes

- This API has a daily post limit. Exceeding the limit will return error code `220009`.
- The `apiKey` is sensitive and should not be hardcoded or shared publicly.
