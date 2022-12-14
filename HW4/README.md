# آزمایش چهارم
مهرانه نجفی (۹۷۱۰۴۷۰۷)، رستا روغنی(۹۷۱۰۵۹۶۳) 

**نکات انجام آزمایش**

۱- در بخش اول انتظارات خود از برنامه را به صورت تست‌هایی در قالب junit درمی‌آوریم. در این روش از Maven استفاده می‌کنیم و در pom.xml مشخصات مربوط به org.junit.jupiter:junit-jupiter را اضافه می‌کنیم. در تست‌های عادی انتظار داریم وقتی طول و عرض اشکال را مشخص می‌کنیم به درستی ذخیره شوند یا اگر آن‌ها را تغییر می‌دهیم به درستی اعمال شوند. به علاوه انتظار داریم که مساحت اشکال درست محاسبه شود. تست‌های اولیه به شکل زیر هستند.

![image](https://user-images.githubusercontent.com/56794518/205360732-95798114-808b-4f70-ad70-f355f7d3327a.png)

![image](https://user-images.githubusercontent.com/56794518/205361922-5dff3312-9df7-4899-8899-f01116b0d568.png)

![image](https://user-images.githubusercontent.com/56794518/205362511-f8367122-1f49-412f-bc14-345a937547dd.png)

۲- پس از اجرای تست‌ها به خطای کامپایل می‌خوریم:

![image](https://user-images.githubusercontent.com/56794518/205362856-0e5c6e49-c5c5-43d6-9f96-fb467188940c.png)

۳- پس از اصلاح خطای کامپایل(جا ماندن یک سمیکالن) و اجرای دوباره تست‌ها نتیجه به شکل زیر خواهد بود:

![image](https://user-images.githubusercontent.com/56794518/205363125-b91e2e34-959b-4282-9813-8477a44587e3.png)

۴- تست‌هایی که با خطا مواجه شدند یکی setWidthOrLength است که در آن چون یک مستطیل به یک مربع اشاره می‌کند و سپس با استفاده از قابلیت‌های مستطیل طول شکل را عوض می‌کنیم دیگر این شکل مربع نخواهد بود. یکی دیگر از تست‌ها testInheritance در تست‌های مربع است. در این تست اصل Liskov که می‌گوید باید بتوانیم آبجکت‌های پدر را با پسر بدون خطا جابجا کنیم، زیر پا می‌رود. پس این کد نیاز به تغییراتی دارد. کد را به صورتی تغییر می‌دهیم که هر دو شکل از یک اینترفیس به نام Shape استفاده کنند تا این خطاهای مربوط به ارث‌بری پیش نیایند. تست‌هایی که برای ارزیابی این روش تولید کردیم به شکل زیر هستند:

![image](https://user-images.githubusercontent.com/56794518/205363882-f82897f6-8a4c-4b4a-986f-3bc16ecf9edf.png)

![image](https://user-images.githubusercontent.com/56794518/205363924-8d546204-04f8-4d4d-8507-9da34c664b99.png)

۵- پس از تغییرات کد به صورتی که تمایل داشتیم، تست‌ها را اجرا می‌کنیم و نتیجه‌ی زیر به دست می‌آید:

![image](https://user-images.githubusercontent.com/56794518/205364069-b055e466-a8f0-40b5-9123-e1f0c0c34731.png)

**مراحل انجام پروژه**  
۱- برنامه‌ای نوشتیم که با داشتن طول و عرض یک مستطیل، مساحت آن را حساب کند.

<img width="970" alt="1" src="https://user-images.githubusercontent.com/45355352/205282277-bcd98828-6720-4341-ac24-8bacc02c552d.png">

۲- برای دریافت کردن و تغییر دادن طول و عرض مستطیل به کلاس آن متدهای getter و setter اضافه کردیم.

<img width="600" alt="2" src="https://user-images.githubusercontent.com/45355352/205282756-c59a1d41-8e36-4793-8255-fec547a35c18.png">

۳- درنهایت کد را به گونه‌ای تغییر دادیم که یک کلاس مربع از کلاس مستطیل ارث‌بری کند و توابع لازم را override کند.

<img width="600" alt="3" src="https://user-images.githubusercontent.com/45355352/205283177-714eed23-6160-47c0-adab-b7b3ee3c740f.png">

کد این بخش در پوشه با نام Rectangle همراه با فایل‌های تستش قرار داده‌شده‌است.

۴- کدی که در مرحله‌ی قبلی نوشته‌شد، از اصول SOLID پیروی نمی‌کرد بنابراین باید در آن تغییراتی می‌دادیم:

- اصل Single responsibility principle (SRP): این اصل بطور کلی در کد ما برقرار است و می‌بینیم که هر دو کلاس مربع و مستطیل فقط یک Actor دارند و تنها از طریق کلاس main می‌توان در آن تغییر ایجاد کرد.
- اصل Open-closed principle: این اصل درابتدا برقرار نیست چرا که در کلاس مربع باید بعضی از توابع مستطیل را override می‌کردیم و اگر بخواهیم هر شکل دیگری را نیز اضافه کنیم که از مستطیل ارث می‌برد، این کار را برای آن نیز باید تکرار کنیم (درواقع کد را modify کنیم). برای برقرار کردن این اصل، همانطور که در ویدئوی آموزشی نیز گفته‌شد اصل پنجم را برقرار می‌کنیم که در ادامه درمورد آن توضیح خواهیم داد. علاوه‌بر این، در ابتدا متد computeArea ما به این صورت بود که حتما ورودی‌اش را مستطیل می‌گرفت و تابع area آن را اجرا می‌کرد ولی الآن آن را به گونه‌ای تغییر دادیم که shape را ورودی بگیرد و تابع area مختص به خودش را صدا کند.
- اصل Liskov substitution principle: این اصل می‌گوید که ما باید بتوانیم کلاس بچه را جایگزین کلاس والد کنیم بدون این‌که رفتار غیرقابل‌ پیش‌بینی از آن دریافت کنیم. در مرحله‌ی تست کردن دیدیم زمانی‌ که مربع از کلاس مستطیل ارث‌بری می‌کند، گاها رفتاری که ما انتظار داریم را نشان نمی‌دهد. بطور مثال اگر طول و عرض یک مستطیل را به‌ترتیب به دو و سه تغییر بدهیم، مساحت آن ۶ می‌شود اما اگر همین‌کار را برای مربع انجام دهیم، مساحت آن ۹ می‌شود. یعنی با یک سناریوی یکسان، جواب‌های متفاوتی گرفتیم. همچنین کلاس مربع preconditionهای قوی‌تری از کلاس مستطیل دارد (شرط برابری طول و عرض در مربع افزون بر مستطیل است). برای حل این مشکل، کلاس مربع را به‌گونه‌ای نوشتیم که دیگر از کلاس مستطیل ارث‌بری نکند و جداگانه getter و setter و تابع محاسبه‌ی مساحت داشته‌باشد.
- اصل Interface segregation principle: این اصل می‌گوید که بهره‌بردن از چند اینترفیس کوچک و باجزئیات، بهتر از بهره‌بردن از یک اینترفیس کلی است چراکه بعضی از کلاس‌ها ممکن است نیازی به استفاده از همه‌ی فیلدها و متدهای موجود در یک اینترفیس کلی نداشته‌باشند. این مشکل در کد ما از اول وجود نداشته‌است.
- اصل Dependency inversion principle: به‌جای تکیه کردن بر پیاده‌سازی concrete، بهتر است از abstraction استفاده کنیم. به همین منظور ما هم یک interface به نام shape تعریف کردیم که متد area دارد و کلاس‌های مستطیل و مربع آن را implement می‌‌کنند و مطابق با فرمول خودشان، متد area را تعریف می‌کنند. این کار ما همچنان اصل چهارم را نقض نمی‌کند چون مساحت ویژگی‌ای است که تمامی اشکال دارند.

درنهایت پس از دادن تغییراتی که گفته‌شد، کد ما به شکل زیر درآمد:

  <img width="600" alt="4" src="https://user-images.githubusercontent.com/45355352/205327905-5cee9b76-2c30-4b8a-bf09-086b03839b07.png">
<img width="600" alt="5" src="https://user-images.githubusercontent.com/45355352/205327961-eeeb54c3-964a-4510-ba97-4cebff969bf3.png">
<img width="600" alt="6" src="https://user-images.githubusercontent.com/45355352/205332103-0667c557-7fb1-4ca1-8de8-845419cf4efa.png">

کد این بخش در پوشه با نام RectangleFinal همراه با فایل‌های تستش قرار داده‌شده‌است.

**سوالات دستورکار**

۱. هر یک از اصول SOLID را در دو الی سه خط توضیح دهید.

اصل اول (Single Responsibility):

این اصل بیان می‌کند هر کلاس در کد باید تنها یک کار انجام دهد پس تنها یک دلیل برای تغییر آن باید وجود داشته باشد. اینطوری تعداد تست‌های بسیار کمتری برای هر کلاس نیاز است. علاوه بر آن هرچه کاربرد یک کلاس محدودتر باشد coupling کاهش می‌یابد. و در آخر باعث سردرگمی کمتر هنگامی که دنبال مقصود خاصی می‌گردیم می‌شود.

اصل دوم (Open-Closed):

در این اصل بیان می‌شود که هر کلاس باید برای پذیرای گسترش باشد اما نباید بازبینی و اصلاحی در آن صورت گیرد. این اصل برای جلوگیری از ایجاد باگ‌های جدید هنگامی که به کارایی‌ای که همین حالا هم داریم، دست می‌زنیم است. بدیهتا این اصل هنگامی که به اصلاح کدی که مشکل دارد می‌پردازیم مربوط نمی‌شود.

اصل سوم (Liskov Substitution):

این اصل بیان می‌دارد اگر کلاس a زیرمجموعه‌ی کلاس b است، باید بتوانیم بدون اینکه خدشه‌ای به کارایی کد وارد شود جای b را با a عوض کنیم. به بیانی دیگر، می‌خواهیم شی‌های یک زیرکلاس، مانند شی‌های کلاس پدر خود رفتار کنند. این اصل کمک می‌کنند مدل سلسله‌مراتبی درستی از ارث‌بری داشته باشیم و از تولد باگ‌هایی که سال‌های سال در سیستم کشف نشده باقی می‌مانند ولی تاثیر منفی خود را روی سیستم می‌گذارند جلوگیری کنیم.

اصل چهارم (Interface Segregation):

اصل آخر بر این نکته اهتمام دارد که اینترفیس‌های بزرگتر باید به اینترفیس‌های کوچکتر تقسیم شوند. با اینکار هنگامی که یک کلاس را از روی یک اینترفیس می‌سازیم مطمئن هستیم تمامی کارایی‌هایی که صرفا به این کلاس مرتبط هستند را پیاده‌سازی می‌کنیم و از قرار دادن کاربرد‌های اضافه و بی‌ربط در آن کلاس خودداری می‌شود.

اصل پنجم (Dependency Inversion):

این اصل مربوط به جداسازی ماژول‌های نرم‌افزاری است. در این صورت، به جای ماژول‌های سطح بالای وابسته به ماژول‌های سطح پایین، هر دو به abstractها بستگی خواهند داشت. همچنین abstractionها نباید به جزئیات وابسته باشند، بلکه جزئیات باید به آن‌ها متکی باشند. این اصل برخلاف اسمش وابستگی‌ها را کاملا برعکس نمی‌کند بلکه مثلا در رابطه با وابستگی ماژول‌های سطح بالا به سطح پایینی‌ها، سطح وابستگی بین این دو را با موجودیتی به نام ابسترکت می‌شکند. 

۲. اصول SOLID درکدام یک از گام‌های اصلی ایجاد نرم‌افزار (تحلیل نیازمندی‌ها، طراحی، پیاده‌سازی، تست و اسقرار) استفاده می‌شوند؟ توضح دهید.

*گام طراحی*. هنگامی که توسعه یک نرم‌افزار را شروع می‌کنیم ممکن است از تجربیات شخصی گذشته استفاده کنیم و اصول را در نظر نگیریم. اما پس از گذر زمان، مشکلاتی در کد پیش خواهند آمد، نیاز به تغییراتی خواهیم داشت و همچنین فیچر‌های جدید خواهند رسید. و پس از گذشت زمان متوجه می‌شوید زمان بسیاری درگیر تصحیح کدهای گذشته بودید. مشکل اصلی شما نیستید بلکه راه‌حل بدیهی، طراحی درست نرم‌افزار است. تمیز نگه‌داری طراحی سیستم تا حد امکان یکی از مهم‌ترین مواردیست که هر توسعه‌دهنده باید برای آن زمان بگذارد و اینجاست که اصول طراحی SOLID وارد عمل می شود. این اصول به توسعه‌دهندگان کمک می‌کنند بهترین طرح‌ها را برای فیچرهایی که باید پیاده‌سازی شوند بسازند. 

۳. معمولا گام تست درپایان روند ایجاد نرم‌افزار انجام می‌شود، اما در روش TDD تست‌نویسی پیش از پیاده‌سازی شروع می‌شود. آیا این دو مورد با هم تناقضی دارند؟ توضیح دهید.

خیر تناقضی ندارند چراکه روش TDD یک روش برای پیاده‌سازی نرم‌افزار است و نه برای تست آن و unit-testهایی که درطول آن نوشته می‌شوند جدا‌ هستند از تست‌های نهایی برای چک نرم‌افزار و هدف متفاوتی دارند. بنابراین همانطور که در عکس زیر هم مشاهده می‌کنید، در روش TDD هم بعد از خروج از مرحله‌ی implementation (یا همان development) نرم‌افزار وارد مرحله‌ی testing خواهد شد.   

![image](https://user-images.githubusercontent.com/45355352/205320489-5ca509e7-85cf-4912-af5a-ef2ee6022157.png)


۴. فرض کنید در آزمایش بالا نیازی به تغییر ابعاد مستطیل نداشتیم. در این حالت طراحی مدلها چه تفاوتی می‌کند؟

درصورتی‌که نیازی به تغییر ابعاد مستطیل نبود و می‌شد آن را immutable درنظر گرفت، دیگر در طراحی مدل‌ها نیازی به تعریف getter و setter نبود و می‌شد کد را به این‌صورت نوشت که کلاس مربع از کلاس مستطیل ارث‌بری کند. دراین حالت Liskov Substitution principle نیز برقرار خواهد بود و باگی وارد کد ما نمی‌شود چرا که دیگر حالتی پیش نمی‌آمد که بشود به تنهایی طول یا عرض مستطیل را تغییر داد (در مربع این کار قابل انجام نیست و حتما طول و عرض آن با هم تغییر می‌کنند که به همین حالت دچار باگ می‌شویم چون اگر این شرط را رعایت نکنیم شکل‌مان دیگر مربع نیست و اگر هم رعایت کنیم، برای سناریوهای یکسان شکل مربع رفتار مشابهی با مستطیل نشان نمی‌دهد ). حال اگر هم بخواهیم طول و عرض یک مستطیل را عوض کنیم، باید یک مستطیل جدید بسازیم چون هویت آن(طول و عرض) با هویت مستطیل قبلی متفاوت است. 
