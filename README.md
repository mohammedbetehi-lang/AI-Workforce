# AI-Workforce

**Current approved release: v1.5**

AI-Workforce is a browser-based multi-agent software workflow built in ZeroAgent Studio. It turns a natural-language request into a structured specification, Python code, proposed pytest tests, a static review/correction pass, and a delivery package.

**النسخة المعتمدة حالياً: v1.5**

AI-Workforce هو سير عمل برمجي متعدد الوكلاء يعمل عبر ZeroAgent Studio. يحوّل طلب المستخدم إلى مواصفات تقنية، ثم كود Python واختبارات مقترحة ومراجعة ساكنة وحزمة تسليم.

## Current workflow / ملف سير العمل الحالي

- **[ai-workforce.v1.5.zeroagent.json](./ai-workforce.v1.5.zeroagent.json)** — approved v1.5 export.
- **[ai-workforce.multilang-plus.zeroagent.json](./ai-workforce.multilang-plus.zeroagent.json)** — preserved original export (historical reference).

## The five agents / الوكلاء الخمسة

1. **Orchestrator** — writes the SPEC.
2. **Coder** — implements the requested Python module.
3. **Tester** — writes a pytest test file that imports the module.
4. **Debugger** — performs semantic static review, identifies likely defects, and proposes a minimal fix.
5. **Finalizer** — packages the module, tests, status, and local test command.

## Scope and verification limits / النطاق وحدود التحقق

- The approved workflow targets **Python 3.11 only**.
- The Debugger performs **static review**, not execution of Python code.
- The Tester generates pytest tests; ZeroAgent does **not** run pytest in this workflow.
- `STATIC_REVIEW_PASS` means the code was checked statically against the proposed tests. It is **not** proof that pytest passed at runtime.
- `STATIC_REVIEW_FAIL` means a defect was identified and a corrected module was supplied.
- `STATIC_REVIEW_INCONCLUSIVE` means static verification was not possible, for example because the code performs file or network I/O.
- Run the delivered tests locally with: `pytest -q test_<module_name>.py`.
- The current graph does not provide a guaranteed conditional halt of downstream agents after an upstream failure.

## Configuration / الإعداد

The workflow is configured for OpenRouter with `deepseek/deepseek-chat`. API credentials are not stored in this repository; configure them securely in ZeroAgent Studio.

## License

No license is currently included. All rights remain with the repository owner unless a license is added.
