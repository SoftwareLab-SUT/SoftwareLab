# آزمایش چهارم
مهرانه نجفی (۹۷۱۰۴۷۰۷)، رستا روغنی(۹۷۱۰۵۹۶۳) 

**مراحل انجام پروژه**  
۱- برنامه‌ای نوشتیم که با داشتن طول و عرض یک مستظیل، مساحت آن را حساب کند.
<img width="970" alt="1" src="https://user-images.githubusercontent.com/45355352/205282277-bcd98828-6720-4341-ac24-8bacc02c552d.png">

۲- برای گرفتن و ست کردن طول و عرض مستطیل به کلاس آن getter و setter اضافه کردیم.
<img width="600" alt="2" src="https://user-images.githubusercontent.com/45355352/205282756-c59a1d41-8e36-4793-8255-fec547a35c18.png">

۳- درنهایت کد را به گونه‌ای تغییر دادیم که یک کلاس مربع از کلاس مستطیل ارث‌بری کند و توابع لازم را override کند.
<img width="600" alt="3" src="https://user-images.githubusercontent.com/45355352/205283177-714eed23-6160-47c0-adab-b7b3ee3c740f.png">

۴- کدی که در مرحله‌ی قبلی نوشته‌شد، از اصول SOLID پیروی نمی‌کرد بنابراین باید در آن تغییراتی به نحوه‌ی زیر می‌دادیم:


**مراحل تست برنامه** 



**سوالات دستورکار**

۱. هر یک از اصول SOLID را در دو الی سه خط توضیح دهید.

۲. اصول SOLID درکدام یک از گام‌های اصلی ایجاد نرم‌افزار (تحلیل نیازمندی‌ها، طراحی، پیاده‌سازی، تست و اسقرار) استفاده می‌شوند؟ توضح دهید. 

۳. معمولا گام تست درپایان روند ایجاد نرم‌افزار انجام می‌شود، اما در روش TDD تست‌نویسی پیش از پیاده‌سازی شروع می‌شود. آیا این دو مورد با هم تناقضی دارند؟ توضیح دهید.

خیر تناقضی ندارند چراکه روش TDD یک روش برای پیاده‌سازی نرم‌افزار است و نه برای تست آن و unit-testهایی که درطول آن نوشته می‌شوند مستقل‌اند از تست‌های نهایی برای چک نرم‌افزار و هدف متفاوتی دارند. بنابراین همانطور که در عکس زیر هم مشاهده می‌کنید، بعد از خروج از مرحله‌ی implementation (یا همان development) نرم‌افزار وارد مرحله‌ی testing می‌شود.   

![image](https://user-images.githubusercontent.com/45355352/205320489-5ca509e7-85cf-4912-af5a-ef2ee6022157.png)


۴. فرض کنید در آزمایش بالا نیازی به تغییر ابعاد مستطیل نداشتیم. در این حالت طراحی مدلها چه تفاوتی می‌کند؟