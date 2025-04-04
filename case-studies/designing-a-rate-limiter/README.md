# 🧩 Designing A Rate Limiter

A **Rate Limiter** controls the number of requests a user/client can make within a time window.

---

## 🧱 Strategies

- Token Bucket
- Leaky Bucket
- Fixed or Sliding Window

---

## 📐 Design Considerations

- Use in API Gateways or service layer
- Store state in Redis or in-memory cache
- Return HTTP 429 on limit exceed

---

## 🛠 Recommended Tools

- Redis (with Lua scripts)
- Envoy, NGINX
- Istio, Kong


---

## 📘 Further Reading

- [System Design Primer](https://github.com/donnemartin/system-design-primer)
- [Awesome Scalability](https://github.com/binhnguyennus/awesome-scalability)
- [Designing Data-Intensive Applications](https://dataintensive.net/)
- [High Scalability Blog](http://highscalability.com/)

---

## 💬 Conclusion

Designing scalable systems involves thoughtful trade-offs, proper architecture choices, and deep understanding of the domain-specific needs. These blueprints serve as strong foundations.
