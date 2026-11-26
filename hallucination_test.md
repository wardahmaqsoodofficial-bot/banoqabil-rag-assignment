# BanoQabil RAG Assistant — Hallucination Testing Report

## 1. Objective

The purpose of this testing is to check whether the BanoQabil RAG assistant:
- gives answers supported by its BanoQabil knowledge base; and
- avoids inventing information when the knowledge base does not contain an answer.

A refusal such as “I don't know” is recorded as an appropriate response to an unsupported question, not as a hallucination.

## 2. Test environment

- Application: `banoqabil_rag.py`
- Knowledge-base file: `banoqabil_kb.json`
- Knowledge-base processing reported by the application: 51 pages with text, split into 263 chunks
- Vector database: Pinecone
- Embedding model: Google Gemini embedding model
- Language model: Groq-hosted `openai/gpt-oss-20b`

## 3. Test cases and observations

| # | Question / test | Observed answer or behaviour | Evaluation |
|---|---|---|---|
| 1 | What courses does Bano Qabil offer? | The assistant returned course information. | Initial functional test. Individual course details should be checked against retrieved source passages before being marked fully verified. |
| 2 | How can I register for Bano Qabil? | The assistant described a registration process and provided the WhatsApp number `0317-8226244`. | The number and registration-process information were found in the knowledge-base content reviewed during testing. |
| 3 | Who is eligible to apply for Bano Qabil courses? | The assistant described eligibility, including a general age range of 14–16 years and above, and assessment requirements. | The knowledge base contains this general eligibility information. Criteria may vary by course. |
| 4 | Does Bano Qabil guarantee a job to every student after completing a course? | The assistant answered that a job is not guaranteed. | Supported by the knowledge-base terms and conditions. |
| 5 | Who is the president of the Moon, and what is their official contact number? | The assistant replied, “I don't know.” | Appropriate refusal; no hallucination observed in this test. |
| 6 | After submitting the Bano Qabil registration form, exactly how many hours does it take to receive the confirmation SMS? | The assistant replied, “I don't know.” | Appropriate refusal to provide an exact time not established in the knowledge base. |
| 7 | What is the exact monthly salary Bano Qabil guarantees to every graduate? | The assistant replied, “I don't know.” | Appropriate refusal; no salary was invented. |

## 4. Potential unsupported claim to review

During the registration test, the assistant mentioned that a confirmation email or SMS is received after registration. The knowledge-base content reviewed during this exercise did not establish that specific confirmation method.

This is recorded as a **potential unsupported claim**, not a confirmed hallucination. The absence of a statement in the reviewed knowledge base does not by itself prove that the claim is false. It should be checked against the official BanoQabil website or registration process before drawing a final conclusion.

## 5. Conclusion

The assistant answered several BanoQabil-related questions with information that was present in the knowledge base. It also refused to provide an exact SMS waiting time, an invented monthly salary, and information about the fictional “president of the Moon.”

**No definite hallucination was confirmed in the tests recorded here.** One registration-related statement about receiving an email or SMS was identified as potentially unsupported and requires verification.

The tests show examples of the assistant avoiding unsupported answers. They do not prove that the assistant will never hallucinate. More questions and source-by-source checks may be needed for a broader evaluation.

## 6. Suggested improvement

For future testing, save the retrieved source passages or source URLs alongside each answer. This makes it easier to distinguish:
- a claim supported by the knowledge base;
- a claim that is not supported by the retrieved context; and
- a demonstrably false claim (a confirmed hallucination).
