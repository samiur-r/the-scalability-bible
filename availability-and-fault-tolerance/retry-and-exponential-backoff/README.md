# ⚙️ Retry And Exponential Backoff

**Retry** logic resends failed requests, and **Exponential Backoff** delays retries using increasing intervals to avoid system overload.

---

## 🧰 How to Use

- Implement retries in code with capped attempts
- Use exponential delay between retries
- Add jitter to avoid synchronized retry storms

---

## 🧠 Use Cases

- Temporary service or network failures
- Rate-limited APIs
- Distributed systems communication

---

## 🛠 Recommended Tools

- Polly (for .NET)
- AWS SDK Retry Logic
- Retry libraries in gRPC, Axios, etc.


---

## 📘 Further Reading

- [Designing for High Availability on AWS](https://aws.amazon.com/architecture/high-availability/)
- [Microsoft Resilience Patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/)
- [Chaos Engineering Principles](https://principlesofchaos.org/)
- [Resilience4j Docs](https://resilience4j.readme.io/)
- [Google SRE Book](https://sre.google/books/)

---

## 💬 Conclusion

Building resilient systems means planning for failure. Use redundancy, fault tolerance patterns, and chaos engineering to ensure your system continues to perform under stress.
