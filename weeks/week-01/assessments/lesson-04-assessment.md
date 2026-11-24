# Lesson 04 — API Design Assessment

## Original answers

1. **Method and endpoint:** `POST /v1/url/create`
2. **Request:** Client sends the full/original URL.
3. **Success response:** `201 Created`; response includes the original URL, short URL, and token/code mapped to the original URL in the database.
4. **Invalid URL:** `400 Bad Request`

## Evaluation

**Result: All answers correct.**

- `POST` is appropriate for creating a short URL.
- The client should send the original URL in the request body.
- `201 Created` is a suitable success status. Returning the original URL, short URL, and short code is a reasonable response contract.
- `400 Bad Request` is appropriate for an invalid URL.

### Suggested API convention
A resource-oriented endpoint such as `POST /api/v1/urls` is more conventional than `/v1/url/create`, but the original answer is valid and the alternative is a design improvement, not a correctness fix.

## Discussion: Why shorten a URL if it still redirects?

The service is useful because the **recipient shares/uses the short link**, rather than needing the long URL. The short link is compact and convenient for messaging, QR codes, print, and other sharing contexts.

The shortener handles the initial request and responds with a redirect. The browser then loads the destination directly; the shortener does not proxy the destination page or its content.

Potential benefits beyond sharing—analytics, branded links, destination updates, expiry and revocation—are optional future capabilities.

### Trade-offs
- Extra redirect and latency.
- Availability dependency on the shortener.

## Security insight: destination integrity (limited guarantee)

The learner proposed that a server-side mapping and token check add security: the visitor cannot freely modify the original destination, and only a known code redirects; otherwise, the service returns `404`.

This is a useful design property when stated carefully:
- The redirect request resolves only through a stored mapping.
- The redirect endpoint should not take a visitor-provided destination and redirect to it.
- Altering the short code does not let a visitor rewrite the stored destination.

**Limitation:** This is not encryption or authentication. It does not prevent modification of the destination site's own request parameters, body, or access controls after the redirect. Security depends also on creation-time URL validation, authorization where needed, and protections against abuse/open redirects.

## Feedback
Good answers and an important product-level question about the shortener's actual value. The learner identified the redirect layer's role and its availability trade-off, then surfaced destination integrity as an additional consideration.
