# Lesson 04 — API Design

## Goal
Define how clients communicate with our URL Shortener: endpoints, HTTP methods, request/response contracts, and error behavior.

## What is an API?
An API is a defined way for software systems to communicate. For our service, the client sends a request and our URL Shortener responds with a result.

## Core APIs

### 1. Create a short URL

**Endpoint:** `POST /api/v1/urls`

Request:
```http
POST /api/v1/urls
Content-Type: application/json
```

```json
{
  "original_url": "https://www.example.com/products/mobile"
}
```

The client sends the long URL. The server validates it, generates a short code, stores the mapping, and returns the short link. The server—not the client—generates the code.

Success: `201 Created`

```json
{
  "short_code": "aB72xK",
  "short_url": "https://short.ly/aB72xK",
  "original_url": "https://www.example.com/products/mobile"
}
```

### 2. Redirect using a short code

**Endpoint:** `GET /{short_code}`

Example: `GET https://short.ly/aB72xK`

If the code exists, the service looks up the stored destination and returns a redirect response:

```http
302 Found
Location: https://www.example.com/products/mobile
```

The browser then makes a request directly to the destination website. The shortener handles the initial redirect; it does not proxy the destination page's content.

## HTTP methods — know for now
- `GET`: retrieve/read a resource
- `POST`: create or submit data
- `PUT`: replace a resource
- `PATCH`: partially update a resource
- `DELETE`: delete a resource

## Status codes discussed
- `200 OK`: request succeeded
- `201 Created`: resource created
- `302 Found`: temporary redirect
- `400 Bad Request`: invalid request (e.g., invalid URL)
- `404 Not Found`: short code/mapping does not exist
- `500 Internal Server Error`: unexpected server-side failure

## API design principles
- Use predictable, resource-oriented endpoints. `POST /api/v1/urls` is a conventional choice; the assessment's `/v1/url/create` is understandable but less resource-oriented.
- Choose HTTP methods to match the operation.
- Validate user input and return clear errors.
- Do not expose internal implementation details in the contract.
- The redirect endpoint should resolve a code, not accept a visitor-supplied destination URL.

## URL Shortener's value and trade-offs
A shortener is a shareable, compact alias for a long destination. Recipients click the short link, and the service redirects them to the destination.

Potential benefits (some are future features, not part of our MVP):
- Easier sharing in messages, social posts, QR codes, and print.
- Analytics such as click counts and referrer/device data, subject to privacy considerations.
- Branded domains.
- Destination changes without changing the shared short link, if supported.
- Expiration, revocation, and access controls, if supported.

Trade-offs:
- Adds an extra network request/redirect and some latency.
- The shortener becomes a dependency: if unavailable, links may fail even if the destination site is healthy.

## Security insight — destination integrity
A server-side short-code-to-destination mapping can provide a limited integrity benefit:
- The destination is stored server-side against a short code.
- A visitor's redirect request does not provide a new destination URL to substitute.
- Modifying the short code or adding arbitrary query parameters to the short-link request does not change the stored mapping itself.
- Unknown codes return `404 Not Found`.

**Important limitation:** A short URL is not encryption or authentication. It does not protect the destination site's own query parameters, request body, or authorization checks after the browser follows the redirect. Anyone who can create mappings, compromise the service, or manipulate the destination website's own requests may still cause other issues. Validate URLs when creating mappings, and consider abuse prevention / open-redirect protections.

## Selected resource
- [MDN — HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods): review GET and POST first, then skim PUT/PATCH/DELETE. (5–8 min)
- [MDN — HTTP status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status): focus on 201, 302, 400, 404, and 500. (5–7 min)

## Key takeaway
An API is the contract between client and service. For our MVP, we need one API to create a mapping and one endpoint to resolve a short code and redirect. The stored mapping—not client-supplied redirect data—controls the destination.
