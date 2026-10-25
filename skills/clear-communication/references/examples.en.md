# Communication examples

These are hypothetical teaching scenarios, not quotations or real project results. Use their specific details only when supported by the actual task. The numbered cases correspond to the [Chinese examples](examples.md); they illustrate decisions, not mandatory phrasing.

## 1. Connect cause and action

Given: the test environment still uses the old database, so the new table is missing. The connection must be updated before retesting.

Unclear: “Table not synced. Old config. Regression needed. Check database.”

Better: “The test environment still connects to the old database, so it cannot see the new table. Update the connection to the new database, then rerun the relevant tests.”

The reader can follow the cause, action, and verification order.

## 2. Keep a useful term and explain it

Audience: someone unfamiliar with backend development, asking how payment retries avoid duplicate charges.

Too dense: “Guarantee retry semantics through idempotency keys.”

Too vague: “Make sure doing the same thing again does not do that thing again.”

Better: “The payment endpoint needs to be idempotent: submitting the same payment request repeatedly must result in only one charge. Assign each payment a unique identifier and reuse it on retries so the server can recognize duplicates.”

This introduces a reusable term. An implementation also needs concurrency-safe duplicate handling and payment processing; the explanation is not a complete design.

## 3. Reuse shared knowledge

Given: the reader understands caching; the change reduces cache lifetime from ten minutes to two.

Better: “The cache lifetime changes from ten minutes to two, reducing how long users may see old data. Database reads may increase.”

Do not redefine caching here. For a beginner, explain it briefly as temporarily storing recent results to avoid reading the database each time.

## 4. Replace empty abstractions with actual behavior

Given: one page shows refund requests, review results, and payment status.

Unclear: “Build a visibility loop to empower user certainty.”

Better: “Users can view their refund request, review result, and payment status on one page.”

If those details are not provided, ask for or identify the missing information instead of inventing this feature description.

## 5. Preserve conditions when shortening

Given: a small test found lower average response time with caching; production is untested.

Misleading: “Caching makes the system faster.”

Better: “Caching reduced average response time in a small test. Its effect in production has not been verified.”

The shorter explanation still preserves the evidence boundary.

## 6. Explain the mechanism directly

Question: why does the page show old data? The cache has not expired.

Better: “The page reads an older result stored in the cache. Because that cached result has not expired, the page has not fetched fresh data.”

A story about a memory box adds no useful explanation here.

## 7. Use an analogy when it helps

The reader remains confused about database indexes and requests an analogy.

Better: “A database index can work like the index at the back of a book: find the relevant locations first, then read those parts. It helps the database narrow the data it needs to examine. It is not always faster; when a query needs most rows, scanning the table may be preferable.”

Return from the analogy to the actual mechanism and its relevant limit.

## 8. Use sentences to express relationships

Given: three independent requests run sequentially, so their waiting times add up.

Fragmented: “Serial. Waiting. Performance. Concurrency.”

Better: “The three requests run one after another, so their waiting times add up. They are independent and can run concurrently to reduce total waiting time.”

## 9. Correct a false premise respectfully

Question: “If all tests pass, there definitely aren't any bugs, right?”

Better: “No. Passing tests show that the tested cases meet expectations; uncovered inputs or environments can still expose bugs.”

State the correction and reason without habitual praise or a long disclaimer.

## 10. Comments explain constraints

Given: a payment service deduplicates requests only when their identifiers match.

Unhelpful: `// Send request`

Better: `// Reuse the original request ID on retries so the payment service can identify duplicates.`

The code expresses how; the comment explains the constraint.

## 11. Distinguish delivery states

Given: the change is written, related unit tests pass, and deployment has not happened.

Misleading: “The issue is completely resolved.”

Better: “The duplicate-submission handling has been updated and related unit tests pass. It has not been deployed, so production behavior remains unverified.”

## 12. Preserve precision across languages

Request: explain a timeout to an English reader, without an analogy.

Better: “A timeout limits how long the client waits for a response. If the limit is reached, the client stops waiting; the server may still be processing the request.”

Do not equate “stops waiting” with “the server stops executing.” Follow the requested language without adding a second-language translation by default.

## 13. Improve an edited passage without renaming its objects

Given: “Return Bay” is the project's established retry-queue name. Failed tasks enter it and are archived after three total attempts fail. The current task changes this to four total attempts and updates the related comment.

Original: `// Return Bay closes the failure-state loop; archive at three hops`

Better: `// Failed tasks enter Return Bay (the retry queue); archive them if all four attempts fail.`

Keep the recognizable name and clarify the comment already being edited. Do not invent a new name or revise unrelated sections. Total attempts and additional retries are different; follow the established behavior. If the user permits only changing the number, respect that restriction.

## 14. Reading a document does not authorize rewriting it

Task: use the document to answer who receives a notification; do not edit files. The document says, “Enable the outcome-awareness loop by notifying the applicant after review.”

Better: “The applicant is notified after the review.”

Extract the stated fact without copying empty phrasing or changing the source. If the source mentions only a “loop” without specifying behavior, do not infer a notification recipient.
