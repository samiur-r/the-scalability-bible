# 🚦 Rate Limiting & Throttling: Controlling the Flow

**Rate limiting** and **throttling** are techniques used to control how many requests a client can make to your system over a given period. They are essential for security, resource protection, and fair usage enforcement.

---

## 📌 What is Rate Limiting?

Rate limiting sets a cap on the number of requests a user or client can make to an API or service in a fixed timeframe (e.g., 100 requests per minute).

---

## 🎯 Why Use Rate Limiting?

- 🛡️ Prevent abuse or DoS attacks
- 🚫 Avoid system overload
- ⚖️ Ensure fair usage among clients
- 💸 Control cost (especially on cloud APIs)

---

## 🔧 How It Works

- Identify the client (via IP, API key, user ID)
- Track the number of requests in a time window
- Allow or deny new requests based on limit

---

## 🧠 Throttling vs Rate Limiting

| Concept      | Description |
|--------------|-------------|
| **Rate Limiting** | Reject requests that exceed the limit |
| **Throttling**    | Slow down responses or queue excess requests |

---

## 📊 Algorithms

- **Fixed Window**: Count requests per time window (e.g., 1 minute)
- **Sliding Window**: Smooth out limits over a rolling window
- **Token Bucket**: Tokens refill over time; requests consume tokens
- **Leaky Bucket**: Requests flow at a constant rate, bursts are queued

---

## 🛠 Tools & Libraries

- **NGINX**: `limit_req` and `limit_conn` modules
- **Express-rate-limit** (Node.js)
- **Redis-based limiters**: Fast, scalable counters
- **Cloud APIs**: AWS API Gateway, GCP Cloud Endpoints have built-in rate limiting

---

## ✅ Best Practices

- Use headers to communicate limits (`X-RateLimit-Limit`, `Retry-After`)
- Combine with authentication and logging
- Adjust limits per client tier (free vs paid)
- Monitor and alert on abuse or overload patterns

---

## 💬 Conclusion

Rate limiting is a simple but powerful way to protect your backend, keep performance steady, and ensure a fair experience for all users.

