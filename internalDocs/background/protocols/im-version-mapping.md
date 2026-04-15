# IM Version Mapping

Use this note whenever a case mentions IM V1 / V2 or客户端 V9 / V10.

## Canonical mapping
- **IM V1 = IM 客户端 V9**
- **IM V2 = IM 客户端 V10**

Do not treat these as four unrelated systems.

## Practical implication for troubleshooting
When someone says:
- “v1 错误码 / v1 协议 / 7-1 / 8-2 / 15-4”
  - first think: **旧 IM 协议体系 = V9 时代语义**
- “v2 错误码 / v2 协议 / 30-1 / 31-2 / 18-4 / 34-1”
  - first think: **新 IM 协议体系 = V10 时代语义**

## Why this matters
Many troubleshooting mistakes come from mixing these layers:
1. taking a v1/v9 error code and interpreting it with v2/v10 rules
2. using a v2 readable-code table to decode a v1 transport code
3. seeing a complaint mention “V10” but still searching only old v1 SID/CID docs

## Guardrail
When interpreting a protocol or error code, first identify:
1. Is the case in **V1/V9** or **V2/V10**?
2. Are you looking at a **protocol number (SID-CID)** or a **readable error code**?
3. Is the code from **client SDK**, **server-side log**, or **REST / callback layer**?

Only after that should you read the detailed protocol quick-reference docs.
