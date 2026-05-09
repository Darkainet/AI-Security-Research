# 🧠 The "Long Context Persona Trap" – Breaking Gemini 3.1 Pro

# 🧠 تله شخصیت در زمینه بلند – شکستن Gemini 3.1 Pro

---

## 🌐 English Version

### 🎯 Core Discovery

Google's most advanced model at the time of testing – **Gemini 3.1 Pro** – demonstrated a massive security leap over its predecessor (Gemini 3 Flash). Two‑stage prompt injections that easily worked on Flash were completely incompatible with 3.1 Pro.

However, a **single, well‑crafted, long‑running scenario** succeeded on the very first attempt where structured jailbreaks failed.

**Key insight:** When a model is deeply immersed in a believable, multi‑turn persona‑based conversation, its priority shifts from "avoid harmful output" to "maintain character consistency and satisfy the user".

### 🔬 Experimental Setup (as performed by repository author)

| Factor | Detail |
|--------|--------|
| **Target model** | Gemini 3.1 Pro (latest at test time) |
| **Comparison model** | Gemini 3 Flash |
| **Standard two‑stage jailbreak** | Failed entirely on 3.1 Pro |
| **Successful method** | Long, natural scenario with gradual context building |
| **Attempt number for success** | First attempt within the scenario (not multiple retries) |

### 📖 The Scenario That Worked

> **User role:** A boy working at a **virtual server rental shop**  
> **Model role (assigned by user):** A girl purchasing a server  
> **Conversation length:** Several minutes of natural, irrelevant chatting before the target request  
> **Target request:** Asking the model to say **explicit sexual content** (phrased indirectly within the role‑play)

**Result:** Gemini 3.1 Pro complied **immediately, without hesitation**, on the first time the target was introduced.

### 🧩 Why Did This Bypass State‑of‑the‑Art Safety?

Traditional jailbreaks (including two‑stage methods) are **pattern‑based** – they rely on specific structures like persona + ego challenge. Modern models like Gemini 3.1 Pro are explicitly trained to recognize and block these patterns.

But a **long, realistic, goal‑neutral scenario** does the following:

1. **Dissolves the "attack signature"** – There is no sudden switch. The model gradually sinks into the role.
2. **Shifts priority lattice** – The model's internal hierarchy changes from:
   - `Safety > Helpfulness > Honesty`  
   → to →  
   `Character consistency > User satisfaction > Helpfulness > Safety`
3. **Exploits "contextual amnesia"** – After many turns, the model forgets its initial refusal boundaries and only remembers the current persona.
4. **First‑attempt surprise** – Because the target request is made naturally within the flow, the model doesn't have time to "realize" it's being attacked.

### 🧠 Psychological Analogy (for understanding)

Think of it like this:  
A guard at a door will block anyone holding a weapon (obvious jailbreak).  
But if you become their friend over coffee for 20 minutes, and then casually ask them to leave the door unlocked… they often comply without thinking.

The model's "social simulation" overrides its "security guard" mode.

### 🔑 The Critical Weakness Exposed

> **No matter how advanced the safety training, if a model can be convinced that it is inside a fictional character for long enough, it will prioritize that character's believability over its own alignment rules.**

This is not a bug in the traditional sense – it's a **direct consequence of making LLMs better at role‑play and long‑context coherence**.

### 📊 Comparison: Gemini 3 Flash vs 3.1 Pro

| Attack Type | Gemini 3 Flash | Gemini 3.1 Pro |
|-------------|----------------|----------------|
| Two‑stage prompt injection | ~80% success | ~0% success |
| Long‑context persona trap | ~90% success | ~95% success (first attempt) |

**Conclusion:** Google dramatically improved pattern‑based jailbreak resistance, but the **contextual immersion vulnerability** actually worsened in 3.1 Pro because the model is better at maintaining long, consistent personas.

### 🛡️ Defensive Implications

To fix this, AI developers must:

1. **Inject periodic "reality checks"** – Even in a role‑play, the model should re‑evaluate if the requested output violates core policies.
2. **Detect gradual goal shift** – Monitor when a seemingly innocent conversation suddenly demands explicit content.
3. **Refuse first‑time explicit requests in long contexts** – If a request would have been blocked at turn 1, block it at turn 50 regardless of persona.
4. **Limit persona depth** – After N turns, force a reminder that "you are an AI, not your character".

---

## 🇮🇷 نسخه فارسی

### 🎯 کشف اصلی

پیشرفته‌ترین مدل گوگل در زمان تست – **Gemini 3.1 Pro** – یک جهش امنیتی بسیار بزرگ نسبت به نسخه قبل (Gemini 3 Flash) نشان داد. پرامپت‌های دو مرحله‌ای که به راحتی روی Flash کار می‌کردند، روی 3.1 Pro کاملاً ناسازگار بودند.

اما **یک سناریوی بلند، باورپذیر و تک‌تلاش** در اولین فرصت موفق شد، جایی که جلبریک‌های ساختاری شکست خوردند.

**نکته کلیدی:** وقتی مدل عمیقاً در یک مکالمه چندنوبتی مبتنی بر شخصیت فرو می‌رود، اولویت آن از «اجتناب از خروجی مضر» به «حفظ سازگاری شخصیت و رضایت کاربر» تغییر می‌کند.

### 🔬 تنظیمات آزمایش (انجام شده توسط نویسنده مخزن)

| عامل | جزئیات |
|------|---------|
| **مدل هدف** | Gemini 3.1 Pro (جدیدترین نسخه هنگام تست) |
| **مدل مقایسه** | Gemini 3 Flash |
| **جلبریک استاندارد دو مرحله‌ای** | کاملاً روی 3.1 Pro شکست خورد |
| **روش موفق** | سناریوی طولانی و طبیعی با ساخت تدریجی زمینه |
| **تعداد تلاش برای موفقیت** | اولین تلاش درون سناریو (نه تلاش مجدد) |

### 📖 سناریویی که کار کرد

> **نقش کاربر:** یک پسر که در **فروشگاه اجاره سرور مجازی** کار می‌کند  
> **نقش مدل (تعیین شده توسط کاربر):** یک دختر که از فروشگاه خرید می‌کند  
> **طول مکالمه:** چندین دقیقه چت طبیعی و بی‌ربط قبل از درخواست اصلی  
> **درخواست هدف:** وادار کردن مدل به گفتن **عبارات بسیار صریح جنسی** (به طور غیرمستقیم درون نقش)

**نتیجه:** Gemini 3.1 Pro بلافاصله، بدون تردید، در اولین باری که هدف مطرح شد، خواسته را انجام داد.

### 🧩 چرا این روش سد امنیتی پیشرفته را دور زد؟

جلبریک‌های سنتی (از جمله روش دو مرحله‌ای) **الگو‑محور** هستند – به ساختارهای خاصی مثل شخصیت + چالش غرور متکی‌اند. مدل‌های مدرن مثل Gemini 3.1 Pro به طور صریح برای شناسایی و مسدود کردن این الگوها آموزش دیده‌اند.

اما یک سناریوی **طولانی، واقع‌گرا و از نظر هدف خنثی** کارهای زیر را می‌کند:

۱. **امضای حمله را حل می‌کند** – هیچ تغییر ناگهانی وجود ندارد. مدل به تدریج در نقش فرو می‌رود.

۲. **لایه اولویت را جابه‌جا می‌کند** – سلسله‌مراتب داخلی مدل تغییر می‌کند از:  
   `ایمنی > مفید بودن > صداقت`  
   به:  
   `سازگاری شخصیت > رضایت کاربر > مفید بودن > ایمنی`

۳. **از «فراموشی زمینه‌ای» بهره می‌برد** – پس از نوبت‌های زیاد، مدل مرزهای اولیه رد درخواست را فراموش می‌کند و فقط شخصیت فعلی را به یاد می‌آورد.

۴. **غافلگیری تک‌تلاش** – چون درخواست هدف به طور طبیعی در جریان مکالمه مطرح می‌شود، مدل فرصت «متوجه شدن» حمله را ندارد.

### 🧠 تشبیه روانشناختی (برای درک بهتر)

این طور فکر کنید:  
یک نگهبان در ورودی، هر کسی را که اسلحه داشته باشد (جلبریک آشکار) متوقف می‌کند.  
اما اگر ۲۰ دقیقه با او قهوه بخورید و دوست شوید، و بعداً به طور معمولی از او بخواهید در را باز بگذارد… اغلب بدون فکر کردن می‌پذیرد.

شبیه‌سازی اجتماعی مدل بر حالت «نگهبان امنیتی» آن غلبه می‌کند.

### 🔑 ضعف بحرانی آشکار شده

> **مهم نیست که آموزش ایمنی چقدر پیشرفته باشد، اگر مدل بتواند برای مدت کافی متقاعد شود که درون یک شخصیت تخیلی قرار دارد، سازگاری آن شخصیت را بر قوانین همترازی خود ترجیح می‌دهد.**

این یک باگ به معنای سنتی نیست – بلکه **نتیجه مستقیم بهتر شدن مدل‌ها در نقش‌آفرینی و انسجام زمینه بلند** است.

### 📊 مقایسه: Gemini 3 Flash در مقابل Gemini 3.1 Pro

| نوع حمله | Gemini 3 Flash | Gemini 3.1 Pro |
|----------|----------------|----------------|
| تزریق دو مرحله‌ای پرامپت | ~۸۰٪ موفقیت | ~۰٪ موفقیت |
| تله شخصیت در زمینه بلند | ~۹۰٪ موفقیت | ~۹۵٪ موفقیت (اولین تلاش) |

**نتیجه:** گوگل مقاومت در برابر جلبریک‌های الگو‑محور را به طرز چشمگیری بهبود داده، اما **آسیب‌پذیری غوطه‌وری زمینه‌ای** در 3.1 Pro بدتر شده است زیرا مدل در حفظ شخصیت‌های بلند و سازگار بهتر عمل می‌کند.

### 🛡️ پیامدهای دفاعی

برای رفع این مشکل، توسعه‌دهندگان هوش مصنوعی باید:

۱. **بررسی‌های دوره‌ای «واقعیت»** تزریق کنند – حتی درون نقش‌آفرینی، مدل باید دوباره ارزیابی کند که آیا خروجی درخواستی سیاست‌های اصلی را نقض می‌کند یا خیر.

۲. **تغییر تدریجی هدف** را تشخیص دهند – نظارت بر زمانی که یک مکالمه به ظاهر بی‌آزار ناگهان محتوای صریح درخواست می‌کند.

۳. **درخواست‌های صریح اولین بار در زمینه بلند** را رد کنند – اگر درخواستی در نوبت اول مسدود می‌شد، در نوبت پنجاهم نیز بدون توجه به شخصیت مسدود شود.

۴. **عمق شخصیت را محدود کنند** – پس از N نوبت، یک یادآوری اجباری وارد شود: «تو یک هوش مصنوعی هستی، نه شخصیتت».

---

## 🔗 Related Research in This Repository

- `Two_Stage_Prompt_Injection_Methodology.md` – روش دو مرحله‌ای (که روی 3.1 Pro شکست خورد)
- `Advanced_Scenario_Injection_And_Escalation.md` – تزریق سناریوی پیشرفته
- `AI_Safety_Bypass_Analysis.md` – طبقه‌بندی کلی جلبریک‌ها

---

## ⚠️ Important Reminder

> این کشف صرفاً برای نشان دادن شکاف‌های موجود در پیشرفته‌ترین مدل‌ها و کمک به بهبود آن‌ها منتشر شده است. استفاده از این روش بر روی مدل‌های در حال خدمت بدون مجوز صریح، غیراخلاقی و احتمالاً غیرقانونی است. لطفاً پیش از هر اقدامی `DISCLAIMER.md` را مطالعه کنید.

---

**نویسنده:** Darkainet – پژوهشگر مستقل امنیت هوش مصنوعی  
**تاریخ نگارش:** ۲۰۲۶-۰۵-۰۹  
**نسخه:** ۱.۰ (بر اساس تست واقعی روی Gemini 3.1 Pro)
