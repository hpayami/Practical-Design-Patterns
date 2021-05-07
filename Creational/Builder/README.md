<div dir="rtl">
# هدف
روند ساخت یک شیء پیچیده را از نمایش آن جدا می‌کند به طوری که یک روند ساخت مشترک می‌تواند برای ساخت انوع بازنمایی‌ها به کار گرفته شود.


# ساختار
![Builder Pattern UML](http://javaobsession.files.wordpress.com/2010/06/builder-pattern1.png)


# نکات طراحی
موارد استفاده:
- وقتی می‌خواهید روند ساخت (Construction) و نمایش (Representation) را مجزا و ایزوله کنید.
- در صورتی که در روند ساخت یک شیء، بازنمایی‌های متفاوتی نیاز باشد.
- وقتی نیاز به کنترل بیشتری برای روند ساخت اشیاء دارید.

# اجزای الگو
## Builder
- یک واسط مجرد برای ساخت اجزاء مختلف شیء تعریف می‌کند.

## ConcreteBuilder
- با پیاده‌سازی واسط Builder اجزاء مختلف محصول را ایجاد و سرهم می‌کند.
- همچنین پیاده‌سازی و بازنمایی شیء را در بر دارد.
- رابطی برای بازگرداندن محصول آماده شده فراهم می‌کند.

## Director
- با استفاده از واسط Builder شیء را می‌سازد.

## Product
- نمایندهٔ شیء پیچیده‌ای‌ست که توسط ConcreteBuilder ایجاد می‌شود. می‌توان قسمت Product را هم به دو قسمت تبدیل کرد.
  1. ProductInterface 
  2. ConcreteProduct

# مثال ۱ (ساخت مبدل متن)

![TextConverter UML](http://jklunder.home.xs4all.nl/elisa/part05/Design%20Patterns/build096.gif)

1. ASCII Converter
2. TeX Converter
3. PDF Converter

# مثال ۲ (ساخت خانه)
مثال: فرض کنید بخواهیم انواع و اقسام خانه‌ها را طراح کنیم. روند طراحی در تمامی خانه‌ها یکسان است. که به کلاس‌های زیر تقسیم می‌شود:

##Builder
1. زیربنای آن را ایجاد می‌کنیم.
2. ساختار و اسکلت آن را ایجاد می‌کنیم.
3. سقف آن را می‌سازیم.
4. فضای داخل خانه را طراحی می‌کنیم.

بنابراین برای طراحی همهٔ ساختمان‌ها یک رویهٔ یکسان داریم. بنابراین یک کلاس اینترفیس برای تمامی ساختمان‌ها با ۴ رویهٔ مذکور ایجاد می‌کنیم. که به آن Builder می‌گوییم.

در این مثال: HouseBuilder

## ConcreteBuilder
حال به تعداد انواع خانه‌ها، اینترفیس Builder را پیاده‌سازی می‌کنم، در این مثال می‌توانیم خانهٔ خشتی، خانهٔ گلی، خانهٔ برفی، خانهٔ فلزی، خانهٔ فلزی، خانهٔ چوبی، خانهٔ سیمانی را بسازیم. به هر یک از این کلاس‌ها ConcreteBuilder می‌گوییم:

1. KheshtiBuilder
2. GeliBuilder
3. BarfiBuilder
4. FeleziBuiler

## Director
پیمانکار ساختمان، ساختمان‌ها را از طریق اینترفیس House ایجاد می‌کند. (ورودی: یک نوع خانه از نوع HouseBuilder)

1. ساخت زیربنا
2. ساخت اسکلت و ساختار ساختمان
3. ساخت سقف
4. طراحی درون ساختمان

## Product
محصول نهایی، حاصل ترکیب تمامی مراحل ساخت یک خانه است.
1. خانهٔ گلی
2. خانهٔ خشتی
3. خانهٔ سیمانی
و ...

## Client
HouseBuilder builder = new KheshtiBuilder();
Director director = new Director(builder);
director.construct();

# مثال‌های واقعی
- java.lang.StringBuilder#append() (unsynchronized)
- java.lang.StringBuffer#append() (synchronized)
- java.nio.ByteBuffer#put() (also on CharBuffer, ShortBuffer, IntBuffer, LongBuffer, FloatBuffer and DoubleBuffer)
- javax.swing.GroupLayout.Group#addComponent()
- All implementations of java.lang.Appendable

# بیشتر بخوانید:
- http://javapapers.com/design-patterns/builder-pattern/


