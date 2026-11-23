# Pragma diagnostic: lecture demo

- Site: https://iskakovdamir.github.io/pragma-diagnostic-demo/
- GA4 property: Pragma diagnostic demo, Measurement ID `G-0ZBK920GZD` (time zone Almaty, KZT)
- GTM container: `GTM-WXG7VH79`, live version 2 "lecture demo"
- GTM config as code: `gtm/container-import.json` (Admin > Import Container > Merge)

## Events

| dataLayer event | GA4 tag | params |
|---|---|---|
| diagnostic_start | GA4 Event - diagnostic funnel | tool_name |
| diagnostic_result | GA4 Event - diagnostic funnel | tool_name, hours_per_week, monthly_cost_kzt, top_process |
| cta_click | GA4 Event - diagnostic funnel | tool_name, cta_text |
| generate_lead | GA4 Event - generate_lead (once per page, key event) | lead_id, value, currency, hours_per_week |

## Seed data (test, not real traffic)

7 runs on 2026-11-23 with `utm_campaign=seed_test`: linkedin x2 (1 lead, 1 stopped at CTA), telegram x3 (2 leads, 1 stopped at result), hh_outreach x2 (1 lead, 1 stopped after start). Funnel: 7 start > 6 result > 5 cta_click > 4 generate_lead.
Filter them out with `Session campaign != seed_test`.

## Live checklist

1. GTM > Preview. In Tag Assistant paste
   `https://iskakovdamir.github.io/pragma-diagnostic-demo/?utm_source=lecture&utm_medium=live&utm_campaign=lecture&debug=1`
   and click Connect. Keep the site window open the whole time.
2. In the site window: answer 7 questions, click the CTA, submit the form twice.
   The `debug=1` panel at the bottom right shows each dataLayer push.
3. Tag Assistant: open `generate_lead` in the left column. The tag fired once. The second submit adds nothing.
4. GA4 > Admin > DebugView: the same events in order, then click `generate_lead` to see its params.
5. GA4 > Explore > Funnel exploration, steps:
   page_view > diagnostic_start > diagnostic_result > cta_click > generate_lead.
   Breakdown: Session source. Today's data shows up in Explore with a delay of a few hours, so build it before the lecture.
6. After Preview: Tag Assistant leaves a `__TAG_ASSISTANT=x` cookie on iskakovdamir.github.io.
   While it is set, that browser loads GTM in debug mode and sends nothing to normal reports or Realtime
   (even after "Stop debugging"). Clear site cookies or use another browser/incognito for non-debug runs.
7. Optional: QR code to the site with `utm_source=lecture_qr`, then show the live audience in Realtime.
