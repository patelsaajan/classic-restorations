---
name: feedback_standard_tailwind
description: Always use standard Tailwind utility classes — never arbitrary bracket notation when a standard equivalent exists
metadata:
  type: feedback
---

Always use standard Tailwind utility classes instead of arbitrary bracket values.

**Why:** User explicitly requested this and asked for it to be remembered as a default behaviour going forward.

**How to apply:**
- Spacing (padding, margin, gap, inset, width, height): use the numeric scale (`px-3.5`, `mt-4.5`, `max-w-330`, `w-27.5`) — any number works in Tailwind v4
- Font sizes: prefer named classes where they are exact matches (`text-xs`=12px, `text-sm`=14px, `text-base`=16px, `text-lg`=18px, `text-xl`=20px, `text-2xl`=24px, `text-4xl`=36px, etc.)
- Line height: prefer named classes (`leading-none`, `leading-tight`, `leading-snug`, `leading-normal`, `leading-relaxed`, `leading-loose`)
- Aspect ratios: use slash syntax without brackets (`aspect-16/9.5` not `aspect-[16/9.5]`)
- Tailwind v4 renames: `bg-linear-to-b` not `bg-gradient-to-b`
- Only keep `[…]` for values with no standard equivalent: sub-12px font sizes, letter-spacing (`tracking-[0.25em]`), hairline borders (`border-[1.5px]`), custom colours, clamp/responsive values, shadows, animation definitions, `content-['']`, `transition-[right]`, line heights below 1
