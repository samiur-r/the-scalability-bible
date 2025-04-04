# 🧠 Trade Offs

System design involves **trade-offs** between competing concerns like latency, throughput, consistency, and availability.

---

## 📌 Common Trade-offs

- **Latency vs Throughput**: Fast response vs handling more requests
- **Consistency vs Availability**: (CAP Theorem) – pick 2 of 3 (Consistency, Availability, Partition Tolerance)
- **Speed vs Accuracy**: ML systems, search results

---

## 🧰 How to Use

- Prioritize based on business goals
- Identify critical paths and acceptable risks
- Document design decisions and revisit regularly

---

## 🧠 Use Cases

- Eventual consistency for high availability
- Strong consistency for financial transactions
- High throughput for logging or telemetry systems

---

## 🛠 Recommended Tools

- Event Sourcing, CQRS
- Apache Kafka, Cassandra
- RDBMS for transactional consistency


---

## 📘 Further Reading

- [Designing Data-Intensive Applications](https://dataintensive.net/)
- [Google SRE Book](https://sre.google/books/)
- [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
- [Principles of Robust System Design](https://principlesofchaos.org/)

---

## 💬 Conclusion

Design principles guide how systems are built and evolve. Understanding the trade-offs and patterns helps you make smarter architectural choices that align with your goals.
