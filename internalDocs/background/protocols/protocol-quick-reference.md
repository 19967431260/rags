# Protocol Quick Reference

Use this file when a troubleshooting case mentions protocol numbers, SID/CID, or asks “这个协议号是干什么的”.

If you already know the raw SID and need a practical troubleshooting route, jump to:
- `references/evidence/protocols/sid-routing-ledger.md` — current practical routing notes for `SID 2 / 3 / 4 / 5 / 7 / 8 / 13`

## First classify the protocol family
### IM V1 / Client V9
- Canonical mapping: **V1 = V9**
- Primary reference source:
  - `tmp/popo-doc-export/docs/8d17c39cd9814ef694488eb3c40f009c__v2错误码v2错误码和协议文档.md`
- Despite the exported file title, this reference contains the classic IM protocol table and extensive **v1 SID-CID definitions**, plus many v1↔v2 mappings.

Common examples:
- `4-9`: 漫游消息同步
- `5-1`: 登录后同步游标上传
- `7-1`: 单聊发送消息
- `7-11`: 单聊已读
- `7-16`: 会话 ACK
- `8-2`: 群消息发送
- `13-20 ~ 13-26`: 聊天室队列相关
- `15-4`: 信令加入房间

### IM V2 / Client V10
- Canonical mapping: **V2 = V10**
- Primary reference sources:
  - `tmp/popo-doc-export/docs/401b6fc04a8e4b629cd50543a6531e1f__v2-sdk协议.md`
  - `references/evidence/protocols/v2-sdk-client-protocol-notes.md` — distilled local note for frequently used V10 client protocols
- These references focus on **v2 readable-code conversion**, **v1↔v2 protocol mappings**, and per-domain v2 error semantics.

Common mapping examples:
- `5-1 -> 27-1`
- `7-1 -> 30-1`
- `7-6 -> 30-6`
- `8-2 -> 31-2`
- `8-19 -> 31-19`
- `8-23 -> 31-23`
- `3-1 -> 34-1`
- `3-2 -> 34-2`
- `13-2 -> 36-2`
- `13-20 -> 36-20`

### Service-side protocol quick reference
- Target source URL:
  - `https://docs.popo.netease.com/team/pc/MMC/pageDetail/78fb494b644b4ad1aa6715ea4304b838`
- Current status in this skill: **URL recorded, local exported source not yet merged into the workspace draft set**.
- Use this when the investigation is explicitly about **服务端协议号速查** rather than only client SDK protocol meaning.

## How to use protocol references in practice
### Case 1: user gives a raw SID-CID
Example: “看下 7-1 / 8-2 / 15-4 是什么”
- First determine whether the case is talking about **old IM/V9** or **new IM/V10**.
- Then consult the corresponding protocol source.

### Case 2: user gives a readable v2 code
Example: `102404`, `108404`, `118404`
- Treat these as **v2 readable codes**, not raw v1 codes.
- Use the V2/V10 reference and interpret by resource domain.

### Case 3: user mixes names
Example: “V10 的 7-1 报错”
- Pause and normalize terms.
- Confirm whether they mean:
  - old protocol number from a legacy doc
  - or a v10/v2 readable-code / mapped resource

## Practical heuristics
- If you see classic IM protocol shapes like `7-1`, `8-2`, `13-20`, `15-4`, think **v1/v9 protocol numbering** first.
- If you see six-digit readable codes like `102404`, `108404`, `118404`, think **v2/v10 readable-code system** first.
- Do not decode v1 transport errors with the v2 readable-code conversion logic.

## Important reminder
- **IM V1 = V9**
- **IM V2 = V10**

State this explicitly when a conversation mixes “协议号、错误码、V9/V10、V1/V2”.
