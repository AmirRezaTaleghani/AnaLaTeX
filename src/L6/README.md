🇮🇷 fa | [🇬🇧 en](./README.en.md)

# LaTeX ساخت کلاس ها در 


در بخش قبلی یاد گرفتیم چطور یک بسته (package) بسازیم.  
سؤال مهمی که پیش می‌آید این است: چه زمانی باید از بسته استفاده کنیم و چه زمانی کلاس؟

- اگر دستورات شما بتوانند با هر کلاس سندی استفاده شوند → آن‌ها را در قالب **بسته (.sty)** پیاده‌سازی کنید.  
- اگر دستورات مخصوص یک نوع سند خاص هستند و قابل استفاده با سایر کلاس‌ها نیستند → باید یک **کلاس (.cls)** بسازید.

#### انواع کلاس‌ها
1. کلاس‌های مستقل مثل `article`، `report` یا `letter`.  
2. کلاس‌های توسعه‌یافته که بر پایه یک کلاس دیگر ساخته شده‌اند.  
   - مثال: کلاس `proc` بر پایه‌ی `article` ساخته شده است.

#### مثال‌ها

یک شرکت می‌تواند کلاسی محلی به نام `ownlet` برای چاپ نامه‌های مخصوص خودش بسازد.  
  این کلاس روی `letter` ساخته شده است و نمی‌تواند با کلاس دیگری استفاده شود → پس فایل آن `ownlet.cls` خواهد بود.  

بسته‌ی `graphics` مجموعه‌ای از دستورات برای درج تصویر ارائه می‌دهد و می‌تواند با هر کلاسی استفاده شود → پس فایل آن `graphics.sty` است.


#### استفاده از docstrip و doc برای نوشتن کلاس‌ها

اگر قصد دارید یک **کلاس بزرگ در LaTeX** بسازید، بهتر است از ابزار **doc** که همراه LaTeX ارائه می‌شود استفاده کنید.  

کلاس‌هایی که با این روش نوشته می‌شوند را می‌توان به دو شکل پردازش کرد:
1. اجرای فایل با LaTeX → تولید مستندات.  
2. پردازش فایل با **docstrip** → تولید فایل `.cls`.

##### مزایای استفاده از doc
- تولید خودکار فهرست تعریف‌ها و دستورات.  
- ثبت تغییرات در قالب یک لیست.  
- مناسب برای نگهداری و مستندسازی سورس‌های بزرگ.

##### منابع استاندارد
- هسته‌ی LaTeX و کلاس‌های استاندارد به صورت فایل‌های **`.dtx`** نوشته شده‌اند.  
- این فایل‌ها هم شامل کد منبع هستند و هم می‌توانند مانند یک سند حروف‌چینی شوند.  
- برای نمونه، اجرای LaTeX روی `source2e.tex` مستندات هسته را تولید می‌کند.  

##### نکته
مستندسازی این فایل‌ها با استفاده از کلاس `ltxdoc.cls` انجام می‌شود.  
برای اطلاعات بیشتر می‌توانید به فایل‌های `docstrip.dtx` و `doc.dtx` یا کتاب *The LaTeX Companion* مراجعه کنید.


#### سیاست مربوط به کلاس‌های استاندارد

بسیاری از گزارش‌هایی که درباره‌ی کلاس‌های استاندارد دریافت می‌شوند، در واقع باگ نیستند؛ بلکه پیشنهاد تغییر در طراحی آن‌ها هستند.  

اما تغییر در **کلاس‌های استاندارد** مانند `article`، `report` یا `book` کار درستی نیست، چون:  

- رفتار فعلی همان چیزی است که در طراحی اولیه مدنظر بوده است.  
- کاربران زیادی به همین طراحی موجود متکی هستند.  
- تغییر این کلاس‌ها باعث ناسازگاری و مشکلات گسترده می‌شود.  

بنابراین، سیاست LaTeX این است که تغییرات اساسی در این کلاس‌ها انجام نشود اگر کاستی‌هایی در آن‌ها وجود داشته باشد.  

راه‌حل پیشنهادی این است که در صورت نیاز به قابلیت‌ها یا طراحی متفاوت، یک **کلاس جدید** ساخته شود که روی کلاس‌های استاندارد بنا شده و رفتار دلخواه را اضافه کند.  

#### نام فرمان‌ها در کلاس‌ها

پیش از معرفی لایه برنامه‌نویسی L3، LaTeX سه نوع فرمان داشت:

1. فرمان‌های نویسنده (Author commands)
   فرمان‌هایی که نویسنده مستقیماً استفاده می‌کند، مانند:  
  ```latex
   \section
   \emph
   \times
  ```

2. فرمان‌های نویسنده کلاس (Class writer commands)
    این فرمان‌ها برای استفاده در فایل‌های کلاس (.cls) هستند و معمولاً نام‌های طولانی‌تر یا ترکیبی از حروف کوچک و بزرگ دارند، مانند:
  ```latex
    \InputIfFileExists
    \PassOptionsToClass
    \LoadClassWithOptions
   ```

3. فرمان‌های داخلی (Internal commands)
  این فرمان‌ها در پیاده‌سازی داخلی LaTeX استفاده می‌شوند و اغلب شامل علامت @ هستند، مانند:
  ```latex
    \@tempcnta
    \@ifnextchar
    \@eha
  ```
وجود @ نشان می‌دهد که این فرمان‌ها برای استفاده در سند عادی مناسب نیستند و فقط در کلاس‌ها مجازند.

قاعده کلی:

فرمان‌هایی که شامل @ هستند، جزو زبان رسمی LaTeX نیستند و ممکن است رفتار آن‌ها در نسخه‌های بعد تغییر کند.

فرمان‌هایی با نام ترکیبی (mixed-case) یا توصیف‌شده در کتاب LaTeX: A Document Preparation System، پشتیبانی رسمی دارند و در آینده هم حفظ خواهند شد.

#### فرمان‌های جعبه و رنگ در کلاس‌ها

برای اطمینان از سازگاری کلاس‌ها با رنگ و جلوگیری از مشکلات احتمالی، بهتر است همیشه از فرمان‌های جعبه در LaTeX استفاده کنید و از دستورات اولیه TeX پرهیز کنید:

- به جای `\setbox` از `\sbox`  
- به جای `\hbox` از `\mbox`  
- به جای `\vbox` از `\parbox` یا محیط `minipage`

فرمان‌های جعبه در LaTeX گزینه‌های پیشرفته‌ای دارند که به اندازه دستورات ابتدایی TeX قدرتمند هستند.

##### مشکل احتمالی رنگ
در حالت زیر، فونت قبل از `}` درست بازگردانده می‌شود:

```latex
{\ttfamily <text>}
```
اما در حالت رنگی:
```latex
{\color{green} <text>}
```
رنگ بعد از آخرین `}` بازگردانده می‌شود. اگر از دستورات ابتدایی TeX استفاده شود، مانند:

```latex
\setbox0=\hbox{\color{green} <text>}
```

#### سبک کلی کلاس‌ها

<div dir="rtl">
LaTeX تعداد زیادی فرمان ارائه می‌دهد که به شما کمک می‌کنند کلاس‌هایی بسازید که ساختارمند، پایدار و قابل حمل باشند.
</div>

##### بارگذاری کلاس‌های دیگر

برای استفاده از کلاس‌ها درون سایر کلاس‌ها، LaTeX فرمان‌های زیر را فراهم کرده است:

```latex
\LoadClass
\LoadClassWithOptions
```
توصیه می‌شود از این فرمان‌ها استفاده کنید و از دستور ابتدایی `\input` پرهیز کنید.

دلایل:

فایل‌های بارگذاری‌شده با `\input` در لیست `\listfiles` قرار نمی‌گیرند.

کلاس‌ها با `\LoadClass` حتی اگر چند بار درخواست شوند، فقط یک بار بارگذاری می‌شوند.

استفاده از `\input` ممکن است باعث نتایج غیرمنتظره شود و گزینه‌های کلاس به درستی پردازش نشوند.


#### ساختار یک کلاس

طرح کلی یک فایل کلاس به صورت زیر است:

1. **شناسایی (Identification)**  
فایل مشخص می‌کند که یک کلاس LaTeX2ε است و توضیح کوتاهی درباره خود ارائه می‌دهد.  
2. **اعلامیه‌های مقدماتی (Preliminary declarations)**  
در این بخش برخی فرمان‌ها اعلام شده و می‌توان سایر کلاس‌ها یا فایل‌های مورد نیاز را بارگذاری کرد. معمولاً این فرمان‌ها برای پردازش گزینه‌ها لازم هستند.  
3. **گزینه‌ها (Options)**  
کلاس گزینه‌های خود را اعلام و پردازش می‌کند.  
4. **اعلامیه‌های بیشتر (More declarations)**  
در این بخش بیشتر کار کلاس انجام می‌شود: اعلام متغیرها، فرمان‌ها و فونت‌های جدید و همچنین بارگذاری سایر فایل‌ها.

#### شناسایی کلاس‌ها

اولین کاری که یک فایل کلاس انجام می‌دهد، شناسایی خود است.

##### ساختار شناسایی کلاس:

```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{<class-name>}[<date> <other information>]
```

مثال:
```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{article}[2022-06-01 Standard LaTeX class]
```
تاریخ `<date>` باید به شکل `yyyy-mm-dd` یا `yyyy/mm/dd` باشد.

سال دقیقاً چهار رقم، ماه و روز هر کدام دو رقم باشند.

اگر تاریخ صحیح وارد نشود، ممکن است تفسیر اشتباه شود و استفاده از کلاس با مشکل مواجه گردد.

نکات مهم:

این تاریخ هنگام استفاده از `\documentclass` بررسی می‌شود:
```latex
\documentclass{article}[2022-06-01]
```

توضیح کلاس هنگام استفاده از آن نمایش داده می‌شود و در فایل log ثبت می‌گردد.

عبارت Standard LaTeX تنها برای کلاس‌های موجود در توزیع استاندارد LaTeX استفاده شود.

#### استفاده از کلاس‌ها در کلاس‌های دیگر

یک کلاس LaTeX می‌تواند کلاس دیگری را بارگذاری کند تا از امکانات و ساختار آن استفاده نماید.

##### دستورات اصلی

```latex
\LoadClass[<options>]{<class-name>}[<date>]
```

مثال:
```latex
\RequirePackage{ifthen}[2022-06-01]
```

این دستور همانند \documentclass عمل می‌کند و اجازه می‌دهد کلاس‌ها بر اساس یک کلاس موجود ساخته شوند.

نویسنده کلاس می‌تواند فقط بخش‌هایی از کلاس پایه را تغییر دهد بدون اینکه از صفر شروع کند.

بارگذاری کلاس با همان گزینه‌ها:
```latex
\LoadClassWithOptions{<class-name>}[<date>]
```

مثال:
```latex
 \LoadClass[twocolumn]{article}
 ```
 این روش به کلاس اجازه می‌دهد تمام گزینه‌های استفاده‌شده در کلاس فعلی را برای کلاس پایه اعمال کند.

 #### یک فایل کلاس حداقلی

یک کلاس LaTeX حداقلی باید شامل تعاریف اصلی برای ظاهر سند و شماره‌گذاری صفحات باشد.

##### موارد اصلی در کلاس حداقلی

- تعریف اندازه متن اصلی با `\normalsize`
- تعیین عرض و ارتفاع متن: `\textwidth` و `\textheight`
- مشخص کردن شماره‌گذاری صفحات

##### مثال فایل کلاس حداقلی

```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{minimal}[2022-06-01 Standard LaTeX minimal class]

% تعریف اندازه متن
\renewcommand{\normalsize}{\fontsize{10pt}{12pt}\selectfont}

% تعیین ابعاد متن
\setlength{\textwidth}{6.5in}
\setlength{\textheight}{8in}

% شماره‌گذاری صفحات
\pagenumbering{arabic}
```

توجه: این کلاس حداقلی از پاورقی‌ها، حاشیه‌ها و شناورها (floats) پشتیبانی نمی‌کند و هیچ‌یک از دستورهای فونت دو حرفی مانند `\rm` را ارائه نمی‌دهد. اکثر کلاس‌ها محتوا و امکانات بیشتری نسبت به این حداقل ارائه می‌کنند.

#### مثال1 : یک کلاس نامه محلی

یک شرکت ممکن است کلاس نامه مخصوص به خود داشته باشد تا نامه‌ها را با سبک شرکت تنظیم کند. در اینجا یک پیاده‌سازی ساده از چنین کلاسی نشان داده شده است.

#### معرفی کلاس

```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{neplet}[2022-06-01 NonExistent Press letter class]
```
انتقال گزینه‌ها و بارگذاری کلاس پایه

```latex
\DeclareOption*{\PassOptionsToClass{\CurrentOption}{letter}}
\ProcessOptions\relax
\LoadClass[a4paper]{letter}
```
تعریف سبک صفحه برای سربرگ نامه

```latex
\renewcommand{\ps@firstpage}{%
  \renewcommand{\@oddhead}{<letterhead goes here>}%
  \renewcommand{\@oddfoot}{<letterfoot goes here>}%
}
```
این مثال ساده نشان می‌دهد که چگونه می‌توان یک کلاس نامه محلی ایجاد کرد. کلاس واقعی ممکن است به ساختار و امکانات بیشتری نیاز داشته باشد.

#### مثال2 : یک کلاس خبرنامه

می‌توان یک خبرنامه ساده را با LaTeX و با استفاده از یک واریانت از کلاس article ایجاد کرد. کلاس با معرفی خود به عنوان `smplnews.cls` آغاز می‌شود:

```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{smplnews}[2022-06-01 The Simple News newsletter class]
\newcommand{\headlinecolor}{\normalcolor}
```

پردازش گزینه‌ها و بارگذاری کلاس پایه:

```latex
\DeclareOption{onecolumn}{\OptionNotUsed}
\DeclareOption{green}{\renewcommand{\headlinecolor}{\color{green}}}
\DeclareOption*{\PassOptionsToClass{\CurrentOption}{article}}
\ProcessOptions\relax
\LoadClass[twocolumn]{article}
```

تعریف `\maketitle` سفارشی:

```latex
\renewcommand{\maketitle}{%
\twocolumn[% 
\fontsize{72}{80}\fontfamily{phv}\fontseries{b}%
\fontshape{sl}\selectfont\headlinecolor
\@title
]% 
}
```

بازتعریف \section و شماره‌گذاری بخش‌ها:

```latex
\renewcommand{\section}{%
  \@startsection
  {section}{1}{0pt}{-1.5ex plus-1ex minus-.2ex}%
  {1ex plus .2ex}{\large\sffamily\slshape\headlinecolor}%
}
\setcounter{secnumdepth}{0}
```

تنظیم اندازه فونت و ابعاد صفحه:

```latex
\renewcommand{\normalsize}{\fontsize{9}{10}\selectfont}
\setlength{\textwidth}{17.5cm}
\setlength{\textheight}{25cm}
```

این اسکلت یک شروع برای ایجاد کلاس خبرنامه است. کلاس واقعی ممکن است امکانات بیشتری مانند شماره نسخه‌ها، نویسندگان مقالات و سبک صفحات ارائه دهد.

#### فرمان‌ها برای نویسندگان کلاس

این بخش به طور خلاصه فرمان‌های پرکاربرد برای نویسندگان کلاس را توضیح می‌دهد.  

برای مطالعه‌ی بیشتر درباره‌ی سیستم LaTeX می‌توانید به منابع استانداردی مثل *LaTeX: A Document Preparation System* یا *The LaTeX Companion* مراجعه کنید.

##### شناسایی کلاس‌ها

برای شناسایی یک فایل کلاس در LaTeX از فرمان‌های زیر استفاده می‌شود:

 `\NeedsTeXFormat{⟨format-name⟩}[⟨release-date⟩]` 

  مشخص می‌کند که این فایل باید با فرمت خاصی پردازش شود.  
   فرمت استاندارد: `LaTeX2e`  
   تاریخ (اختیاری): باید به صورت `yyyy-mm-dd` یا `yyyy/mm/dd` نوشته شود.  
   اگر تاریخ سیستم قدیمی‌تر باشد، هشدار داده می‌شود.  

  **مثال:**
  ```latex
  \NeedsTeXFormat{LaTeX2e}[2022-06-01]
  ```

`\ProvidesClass{⟨class-name⟩}[⟨release-info⟩]`

اعلام می‌کند که فایل جاری یک کلاس است.

 این release-info شامل تاریخ انتشار و در صورت نیاز توضیح کوتاه یا شماره نسخه است.

این اطلاعات برای بررسی نسخه هنگام بارگذاری کلاس استفاده می‌شود.

توضیحات نباید طولانی باشند.

مثال:
```latex
\ProvidesClass{article}[2022-06-01 v1.0 Standard LaTeX class]
```

`\ProvidesFile{⟨file-name⟩}[⟨release-info⟩]`

مشابه دستور قبلی است ولی برای اعلام فایل‌های جانبی (غیر از فایل اصلی کلاس).

مثال:
```latex
\ProvidesFile{T1enc.def}[2022-06-01 v1.0 Standard LaTeX file]
```
 نکته: عبارت Standard LaTeX فقط باید در فایل‌های رسمی توزیع استاندارد LaTeX استفاده شود.

#### بارگذاری کلاس‌ها

برای ساخت یک کلاس جدید می‌توان از کلاس‌های موجود استفاده کرد. این کار با دستورات زیر انجام می‌شود:

 `\LoadClass[⟨options⟩]{⟨class-name⟩}[⟨release-info⟩]`  

  بارگذاری یک کلاس دیگر در فایل کلاس.  
   مشابه استفاده از `\documentclass` است.  
   فقط یک بار در هر فایل کلاس استفاده می‌شود.

`\LoadClassWithOptions{⟨class-name⟩}[⟨release-info⟩]`  

  همانند دستور قبل است اما تمام گزینه‌های فایل جاری را نیز به کلاس پایه منتقل می‌کند.

**مثال‌ها:**
```latex
\LoadClass{article}[2022-06-01]
\LoadClassWithOptions{article}[2022-06-01]
```
این دستورات امکان می‌دهند کلاس‌های جدید بر اساس کلاس‌های استاندارد ساخته شوند و فقط بخش‌های دلخواه تغییر کنند.

#### ایجاد و استفاده از گزینه‌های key–value در کلاس‌ها

گزینه‌های key–value در کلاس‌ها دو بخش دارند: **ایجاد** و **استفاده**. این گزینه‌ها می‌توانند در حین بارگذاری کلاس یا در پیش‌نویس استفاده شوند.

##### ایجاد گزینه‌ها
`\DeclareKeys[⟨family⟩]{⟨declarations⟩}`  

مجموعه‌ای از گزینه‌ها را بر اساس لیست ⟨declarations⟩ ایجاد می‌کند.  
هر گزینه دارای یک یا چند ویژگی (property) است.

##### ویژگی‌های اصلی

`.code` — اجرای کد دلخواه  
`.if` — تنظیم یک سوئیچ `\if…`  
`.ifnot` — تنظیم یک سوئیچ معکوس  
`.pass-to-packages` — مشخص می‌کند گزینه کلاس به‌صورت سراسری به بسته‌ها منتقل شود  
`.store` — ذخیره مقدار در یک ماکرو  
`.usage` — تعیین می‌کند که گزینه در کجا قابل استفاده باشد:  
  `load` (فقط هنگام بارگذاری کلاس)  
  `preamble` (در پیش‌نویس)  
  `general` (بدون محدودیت)  

##### مثال
```latex
\DeclareKeys[myclass]{
  draft.if = @myclass@draft,
  draft.usage = preamble,
  name.store = \@myclass@name,
  name.usage = load
}
```

درفت (draft) ← در پیش‌نویس داده می‌شود و سوئیچ `\if@myclass@draft` را تنظیم می‌کند.

نام (name) ← فقط هنگام بارگذاری کلاس داده می‌شود و مقدارش در `\@myclass@name` ذخیره می‌شود.

#### گزینه‌های ناشناخته

`\DeclareUnknownKeyHandler[⟨family⟩]{⟨code⟩}`

رفتار هنگام مواجهه با کلید ناشناخته را تعیین می‌کند.

نام کلید = `#1`

مقدار = `#2`

کل گزینه = `\CurrentOption`

##### مثال:
 ارسال گزینه ناشناخته به کلاس `article`

```latex
\DeclareUnknownKeyHandler{
  \PassOptionsToClass{\CurrentOption}{article}
}
```
#### پردازش گزینه‌ها

`\ProcessKeyOptions[⟨family⟩]`

همه گزینه‌های داده‌شده به کلاس جاری را بررسی و پردازش می‌کند.
نیازی به `\ProcessOptions` نیست.

#### تنظیم دستی 

`\SetKeys[⟨family⟩]{⟨keyvals⟩}`

تنظیم صریح مجموعه‌ای از گزینه‌ها برای کلاس.
اگر ⟨family⟩ مشخص نشود، مقدار `\@currname` استفاده می‌شود.


### جمع‌بندی

تا این مرحله، ما با مفاهیم پایه‌ای ساخت کلاس در LaTeX آشنا شدیم. یاد گرفتیم که:

- تفاوت کلاس و بسته چیست و چه زمانی باید از هر کدام استفاده کنیم.
- ساختار کلی یک کلاس شامل شناسایی، اعلامیه‌های مقدماتی، گزینه‌ها و بدنه کلاس است.
- چگونه کلاس‌ها می‌توانند کلاس‌های دیگر را بارگذاری کنند و گزینه‌ها را منتقل کنند.
- روش شناسایی کلاس با فرمان‌های `\NeedsTeXFormat` و `\ProvidesClass` و اهمیت تاریخ و توضیحات.
- چطور می‌توان فرمان‌های پایه مانند `\normalsize`، ابعاد صفحه و شماره‌گذاری را در کلاس تعریف کرد.
- با مثال‌های عملی مانند کلاس نامه محلی و کلاس خبرنامه، نحوه بازتعریف فرمان‌ها و تنظیم سبک‌های دلخواه را مشاهده کردیم.
- ایجاد و مدیریت گزینه‌های key–value برای کلاس‌ها با `\DeclareKeys` و پردازش آن‌ها با `\ProcessKeyOptions`.  
- نحوه مدیریت گزینه‌های ناشناخته با `\DeclareUnknownKeyHandler` و امکان انتقال آن‌ها به کلاس‌های دیگر.  


با این دانش، حالا می‌توانیم کلاس‌های اختصاصی برای انواع اسناد بسازیم و کنترل کامل ظاهر و رفتار سند LaTeX خود را در دست بگیریم.

نویسنده: [محمد طاها روشن بین](https://github.com/M-tahaRoshanbin)


راه‌های ارتباطی با انجمن علمی:

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=maildotru&logoColor=white)](mailto:kntu.physics.association@gmail.com)
[![Telegram](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/physicskntu)
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=data:image/svg%2bxml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiA/PjxzdmcgaGVpZ2h0PSI3MiIgdmlld0JveD0iMCAwIDcyIDcyIiB3aWR0aD0iNzIiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGcgZmlsbD0ibm9uZSIgZmlsbC1ydWxlPSJldmVub2RkIj48cGF0aCBkPSJNOCw3MiBMNjQsNzIgQzY4LjQxODI3OCw3MiA3Miw2OC40MTgyNzggNzIsNjQgTDcyLDggQzcyLDMuNTgxNzIyIDY4LjQxODI3OCwtOC4xMTYyNDUwMWUtMTYgNjQsMCBMOCwwIEMzLjU4MTcyMiw4LjExNjI0NTAxZS0xNiAtNS40MTA4MzAwMWUtMTYsMy41ODE3MjIgMCw4IEwwLDY0IEM1LjQxMDgzMDAxZS0xNiw2OC40MTgyNzggMy41ODE3MjIsNzIgOCw3MiBaIiBmaWxsPSIjMDA3RUJCIi8+PHBhdGggZD0iTTYyLDYyIEw1MS4zMTU2MjUsNjIgTDUxLjMxNTYyNSw0My44MDIxMTQ5IEM1MS4zMTU2MjUsMzguODEyNzU0MiA0OS40MTk3OTE3LDM2LjAyNDUzMjMgNDUuNDcwNzAzMSwzNi4wMjQ1MzIzIEM0MS4xNzQ2MDk0LDM2LjAyNDUzMjMgMzguOTMwMDc4MSwzOC45MjYxMTAzIDM4LjkzMDA3ODEsNDMuODAyMTE0OSBMMzguOTMwMDc4MSw2MiBMMjguNjMzMzMzMyw2MiBMMjguNjMzMzMzMywyNy4zMzMzMzMzIEwzOC45MzAwNzgxLDI3LjMzMzMzMzMgTDM4LjkzMDA3ODEsMzIuMDAyOTI4MyBDMzguOTMwMDc4MSwzMi4wMDI5MjgzIDQyLjAyNjA0MTcsMjYuMjc0MjE1MSA0OS4zODI1NTIxLDI2LjI3NDIxNTEgQzU2LjczNTY3NzEsMjYuMjc0MjE1MSA2MiwzMC43NjQ0NzA1IDYyLDQwLjA1MTIxMiBMNjIsNjIgWiBNMTYuMzQ5MzQ5LDIyLjc5NDAxMzMgQzEyLjg0MjA1NzMsMjIuNzk0MDEzMyAxMCwxOS45Mjk2NTY3IDEwLDE2LjM5NzAwNjcgQzEwLDEyLjg2NDM1NjYgMTIuODQyMDU3MywxMCAxNi4zNDkzNDksMTAgQzE5Ljg1NjY0MDYsMTAgMjIuNjk3MDA1MiwxMi44NjQzNTY2IDIyLjY5NzAwNTIsMTYuMzk3MDA2NyBDMjIuNjk3MDA1MiwxOS45Mjk2NTY3IDE5Ljg1NjY0MDYsMjIuNzk0MDEzMyAxNi4zNDkzNDksMjIuNzk0MDEzMyBaIE0xMS4wMzI1NTIxLDYyIEwyMS43Njk0MDEsNjIgTDIxLjc2OTQwMSwyNy4zMzMzMzMzIEwxMS4wMzI1NTIxLDI3LjMzMzMzMzMgTDExLjAzMjU1MjEsNjIgWiIgZmlsbD0iI0ZGRiIvPjwvZz48L3N2Zz4=&logoColor=white)](https://www.linkedin.com/company/physics-kntu)
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white)](https://www.instagram.com/kntuphysics)
