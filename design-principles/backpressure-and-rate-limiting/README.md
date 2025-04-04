# 🧠 Backpressure And Rate Limiting

**Backpressure** is the ability of a system to signal upstream systems to slow down. **Rate Limiting** restricts the number of operations to avoid overload.

---

## 🧰 How to Use

- Apply rate limits on APIs per user/IP/token
- Use queues and monitor throughput
- Reject or throttle requests when thresholds are exceeded

---

## 🧠 Use Cases

- Public APIs and gateways
- Stream processing pipelines
- Microservice communication

---

## 🛠 Recommended Tools

- NGINX, Envoy, or API Gateway rate limiting
- Kafka (backpressure by design)
- Redis or Token Bucket algorithms


---

## 📘 Further Reading

- [Designing Data-Intensive Applications](https://dataintensive.net/)
- [Google SRE Book](https://sre.google/books/)
- [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
- [Principles of Robust System Design](https://principlesofchaos.org/)

---

## 💬 Conclusion

Design principles guide how systems are built and evolve. Understanding the trade-offs and patterns helps you make smarter architectural choices that align with your goals.
