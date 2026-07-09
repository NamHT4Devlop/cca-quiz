# ⚠️ Các câu có mâu thuẫn trong PDF gốc — nên kiểm tra lại

Dữ liệu website được trích **trung thực 100%** từ file PDF của bạn (mọi đáp án khớp chính xác dòng `Answer : X`).
Tuy nhiên, khi đối chiếu chéo toàn bộ 300 câu, có **22 câu mà phần _Giải thích_ trong chính PDF bị mâu thuẫn/nhầm nhãn**. Đây là lỗi có sẵn trong nguồn, không phải lỗi trích xuất.

---

## 🔴 Nhóm 1 — Mâu thuẫn thật sự: đáp án có thể SAI (4 câu — ưu tiên kiểm tra)

Ở các câu này, phần giải thích lại lập luận cho một phương án KHÁC với đáp án được đánh dấu. Bạn nên tự tra cứu tài liệu chính thức để xác định đáp án đúng.

### Câu 86 — PDF đánh dấu đáp án: **B**
> An architect is evaluating whether to use Claude's structured outputs (output_config.format) or tool_use with JSON schemas for a data extraction pipeline. The pipeline processes diverse document types and must always return exactly one extraction result per document. Which approach is more appropriate?

- **A.** tool_use with tool_choice 'any' — guarantees a tool call (structured output) even when the document type is unknown
- **B.** Neither — use prompt instructions to request JSON output and parse the response ✅(PDF chọn)
- **C.** Both approaches concatenated — tool_use for extraction, then output_config for final formatting
- **D.** output_config.format with json_schema — response-level structured output regardless of content

**Vấn đề:** Marked answer is B ('Neither — use prompt instructions to request JSON output and parse the response'), but the explanation clearly justifies option D. It states output_config provides response-level guarantees and concludes 'output_config.format is the more appropriate feature for response-level structured output' — which is option D. The explanation never supports B; B (using prompt instructions instead of a structured-output feature) directly contradicts the explanation's reasoning. Answer letter should be D. The RAW itself says 'Answer : B', so this is a source-level answer/explanation mismatch faithfully carried into the JSON.

---

### Câu 182 — PDF đánh dấu đáp án: **C**
> A developer uses the Anthropic API with prompt caching. They have a 6,000-token system prompt, a 3,000-token set of examples, and variable user messages. They want to cache the system prompt and examples. How should they structure the cache breakpoints?

- **A.** Single breakpoint at the end of the system prompt only
- **B.** Breakpoint after the system prompt AND after the examples, creating two cached segments
- **C.** No explicit breakpoints needed — automatic caching handles it with Sonnet 4.5+ ✅(PDF chọn)
- **D.** Breakpoint only at the end of the examples, caching everything as one segment

**Vấn đề:** Marked answer is C ('No explicit breakpoints needed - automatic caching handles it with Sonnet 4.5+'). The explanation's opening supports C, but its closing contradicts the marked answer: it groups the answer among 'Manual breakpoints (Options A-C)' and then explicitly states 'Option D is the correct approach for current models', naming a DIFFERENT letter (D) as correct. Internal answer/explanation inconsistency present identically in RAW and PARSED (source error, faithfully parsed).

---

### Câu 201 — PDF đánh dấu đáp án: **C**
> An architect builds an agent for legal document review. The agent needs to identify clauses that conflict with a set of regulatory requirements. The regulatory requirements document is 80,000 tokens. Each legal document is approximately 20,000 tokens. The total context window is 200,000 tokens. They want to process batches of documents efficiently. How many documents can they process per batch with room for Claude's output and system prompt?

- **A.** One document at a time to maximize quality per document
- **B.** Three documents per batch: 80K + 3*20K + system overhead + output buffer = ~160K, leaving room for analysis
- **C.** Five documents per batch: 80K (regulations) + 5*20K (documents) + system overhead = ~190K tokens ✅(PDF chọn)
- **D.** Ten documents: load only relevant regulation sections per document to fit within context

**Vấn đề:** Marked answer is C (five documents, ~190K). The explanation undermines it: it says five documents 'push to ~190K which is too tight,' then 'Option B is actually safer,' and 'Answer A is calculated as feasible at ~190K.' The reasoning points toward B (and mislabels the five-doc case as 'A') rather than supporting the marked answer C. Faithfully parsed from RAW; this is a source-level inconsistency in the explanation.

---

### Câu 205 — PDF đánh dấu đáp án: **D**
> A developer builds a structured output pipeline where Claude extracts product specifications from manufacturer datasheets. The extraction schema uses anyOf to allow a measurement to be either {value: number, unit: string} or {range: {min: number, max: number}, unit: string}. After deployment, they notice the schema validation sometimes fails. What is the likely issue?

- **A.** The union types in anyOf are exceeding the maximum of 16 types per union allowed in strict mode
- **B.** anyOf is not supported in Claude's structured output schema
- **C.** Each member of the anyOf union must be a distinct type with no overlapping required fields, and both types share the 'unit' field causing ambiguity
- **D.** anyOf requires a discriminator field to help the model distinguish between union members ✅(PDF chọn)

**Vấn đề:** Marked answer is D (anyOf requires a discriminator field). The question asks 'what is the likely issue?' and the explanation identifies the issue as 'both schemas include unit as a required field, which can cause validation ambiguity' — which is verbatim option C's diagnosis ('both types share the unit field causing ambiguity'). It only weakly endorses D as 'a best practice that would fix the issue.' The stated issue points to C while D is marked. Faithfully parsed from RAW; source-level inconsistency.

---

## 🟡 Nhóm 2 — Lỗi diễn đạt nhỏ: đáp án VẪN ĐÚNG (18 câu)

Ở các câu này, lập luận chính của phần giải thích vẫn ủng hộ đúng đáp án được đánh dấu; chỉ có **một câu 'chê phương án' bị ghi nhầm nhãn** (ví dụ viết 'Option A' nhưng ý là 'Option B'). **Không ảnh hưởng việc học** — đáp án đúng vẫn chính xác. Liệt kê để bạn nắm:

| Câu | Đáp án đúng | Ghi chú |
|----|----|----|
| 2 | A | Giải thích nhầm nhãn khi chê phương án |
| 3 | D | Giải thích nhầm nhãn khi chê phương án |
| 5 | D | Giải thích nhầm nhãn khi chê phương án |
| 6 | B | Giải thích nhầm nhãn khi chê phương án |
| 8 | D | Giải thích nhầm nhãn khi chê phương án |
| 9 | D | Giải thích nhầm nhãn khi chê phương án |
| 10 | D | Giải thích nhầm nhãn khi chê phương án |
| 11 | C | Giải thích nhầm nhãn khi chê phương án |
| 12 | B | Giải thích nhầm nhãn khi chê phương án |
| 14 | C | Giải thích nhầm nhãn khi chê phương án |
| 15 | B | Giải thích nhầm nhãn khi chê phương án |
| 16 | A | Giải thích nhầm nhãn khi chê phương án |
| 18 | C | Giải thích nhầm nhãn khi chê phương án |
| 20 | C | Giải thích nhầm nhãn khi chê phương án |
| 21 | B | Giải thích nhầm nhãn khi chê phương án |
| 22 | A | Giải thích nhầm nhãn khi chê phương án |
| 23 | C | Giải thích nhầm nhãn khi chê phương án |
| 24 | D | Giải thích nhầm nhãn khi chê phương án |

> Nếu muốn, mình có thể **tự động dọn lại nhãn** trong phần giải thích của 18 câu này (chỉ sửa câu chữ, không đổi đáp án). Chỉ cần bạn yêu cầu.