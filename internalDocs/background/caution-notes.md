# Caution Notes

Use these notes to avoid overconfident or outdated conclusions.

## 1. Conflicting threshold / behavior notes
### 安全通超时阈值
Different source docs mention different thresholds:
- one source says 文本 500ms、图片 2s
- another source says 3 秒

Do not present a single hard threshold as universal truth unless live evidence or a more authoritative source confirms it.

## 2. Historical case notes are not universal rules
Audio/video troubleshooting handbooks contain many historical cases and version-specific behaviors.
Treat them as:
- patterns
- possible explanations
- escalation hints
Not as always-valid product rules.

## 3. Presence in backend does not guarantee frontend visibility
Common trap across IM troubleshooting:
- message exists in backend != client definitely displayed it
- roaming exists != client definitely consumed it
- send success != receive success

## 4. Evidence shortage should reduce confidence
If you do not yet have enough evidence, say so explicitly.
Prefer:
- “当前高概率方向是 ...，但还缺 ... 证据”
Over:
- “问题就是 ...”

## 5. Special cases may be under-documented
Some source docs explicitly leave TODO areas unfinished, such as:
- 第三方回调
- 拉黑等特殊场景
When a case matches these areas, avoid pretending the existing playbook is complete.
