# SE_LAB_6
<h2>Implementation Instructions</h2>
لطفا برای اجرای برنامه، پروژه را از برنچ master گرفته و سپس اجرا کنید.
<h2>Implementation details</h2>
<h3>Facade Design Pattern</h3>
Facade is a structural design pattern that provides a simplified interface to a library, a framework, or any other complex set of classes. We have detected two parts of the code that could be refactored to use this pattern:

<h3>CodeGeneratorFacade</h3>
Before the refactoring, the Parser class was directly using the functionalities of the codeGenerator class. When refactored, we added a Facade for the CodeGenerator so that the Parser would only use the available functionality defined in the CodeGeneratorFacade class and so this way we limited and simplified the interface available. At last we also modified the usages to adapt the code with the refactor action taken.

<h3>ScannerFacade</h3>
Before the refactoring, the Parser class was directly using the functionalities of the lexicalAnalyzer. When refactored, we added a Facade for the scanner so that the Parser would only use the available functionality defined in the ScannerFacade class and so this way we limited and simplified the interface available. At last we also modified the usages to adapt the code with the refactor action taken.

<h3>Polymorphism:</h3>
In programming languages and type theory, polymorphism is the provision of a single interface to entities of different types, or the use of a single symbol to represent multiple different types.
One of the most common signs of refactoring using polymorphism is multiple switch case scenarios. Due to this explanation, we detected this antipattern in the Action class and so we refactored it. In this process, we created a unique class for each and every switch case available for the actions; we created the shift, accept, reduce class and moved all these action related functionalities to an actions package. At last we also modified the usages to adapt the code with the refactor action taken.

<h3>Separate Query From Modifier:</h3>
This factoring technique implements Command and Query Responsibility Segregation. This principle tells us to separate code responsible for getting data from code that changes something inside an object. One of the bad smells detected in the code according to this pattern was in the SymbolTable class in the getNextParameter function, where the previous parameter value is fetched and the next parameter is revised in the same function. To better this process, we have added another function getCurrentParamIndex to separate the Query from Modifier. 

<h3>Self Encapsulated Field</h3>
In this refactoring method and this part of refactoring the minijava project, we define the class properties as private and call them as private classes too. We use Getter and Setter methods to ensure that all operations on properties are done through methods instead of accessing the properties we have directly. We added getter and setter named getterMemory and setterMemory to the symbolTable class.

<h3>Remove Assignments to Parameters</h3>
The refactoring method is used to remove value assignment operations to parameters in the functions we have in the code. This refactoring will help you improve the piece of code that assigns values to parameters and make them more readable and modifiable. In the ParseTable.java file, instead of having to change the input of the function, which is jsonTable, we define a local variable and use the variable we created from now on in the code.

<h3>Extract Method</h3>
The last refactoring rule we used for this project is used to turn a part of repetitive code into a separate method to execute that part of the code. This refactoring trick helps developers to remove repetitive code to a separate method and use that method in different places of the program if needed so they would get rid of the duplicated parts of the code that already exists. In the codegenarator class, a piece of code was repeated 3 times, so instead of repeating it, we created a function and called the function whenever we needed that specific piece of code to execute.

# سوالات تشریحی
<h2>
  سوال ۱
</h2>
<h3>
  کد تمیز
</h3>
<p>
  کد تمیز بسیار خوانا و ساده است. در فهمیدن کد تمیز کسی به مشکل نمی‌خورد.کد تمیز همکاری توسعه دهندگان را بسیار راحت‌تر می‌کند. کد تمیز باعث می‌شود که توسعه دهندگان بیشتر سر کد با هم توافق نظر داشته باشند و دوباره کاری را به حداقل می‌رسانند. کد تمیز هدف توسعه دهندگانش را شفاف بیان می‌کند و این باعث می‌شود که که کد در نهایت بیشتر maintainable باشد و اررورها را به حداقل می‌رساند و تغییر در آن ساده تر است.
</p>
<h3>
  بدهی فنی
</h3>
<p>
  بدهی فنی، آسیب‌هایی است که از انتخاب کردن راه‌حل‌های ‌صرفا دم دستی و سریع و غیر بهینه برای صرفا رسیدن به ددلاین‌های نزدیک نتیجه می‌شود. هرجا که بدهی فنی داریم، در آینده refactoring و بهبود اوضاع نیاز است. در طولانی مدت، بدهی فنی منجر به کم کردن سرعت توسعه در تیم می‌شود و به به وجود آمدن باگ‌های بیشتر کمک می‌کند.
</p>
<h3>
  بوی بد
</h3>
<p>
  بوهای بد در مهندسی نرم‌افزار به معنای مشخصه‌های قابل توجهی هستند که بر کم بودن کیفیت کد و یا مشکلات دیزاینی دلالت می‌کنند. بوهای بد نشان‌دهنده مشکلات عمقی‌تر در سیستم هستند. برای مثال کد duplicate شده و یا ساختارهای بسیار پیچیده در دیزاین. بوهای بد این پیام را انتقال می‌دهند که به زودی باید در سیستم refactoring اتفاق بیوفتد تا این موارد مشکلات را بیش از این چیزی که هست نکنند.
</p>
<h2>
  سوال ۲
</h2>
<h3>
  1.Bloaters
</h3>
<p>
  در این بوی بد ما با کلاس‌ها و متدهایی روبه‌رو هستیم که بسیار بزرگ هستند و همین امر کار کردن با آنها و تغییرشان را سخت می‌کند. این کلاس‌ها و متدها در طولانی مدت به وجود می‌آیند و به سیستم آسیب می‌زنند.
</p>
<h3>
  2.Object Orientation Abusers
</h3>
<p>
  این بوی بد در اثر استفاده نادرست و ناقص از اصول برنامه نویسی شیئ گرا به وجود می‌آیند.این بوی بد به پیچیدگی در کد و ساختارهای اشتباه در کد منجر می‌شود که maintain کردن سیستم را سخت می‌کند.
</p>
<h3>
  3. Change Preventers
</h3>
<p>
  نتیجه این بوی بد ایجاد هر تغییری در کد را بسیار سخت می‌کند به نحوی که برای کوچکترین تغییر باید تغییرات خیلی زیاد و خیلی بزرگتری در کد ایجاد کنید. این سخت شدن هم به دلیل پیچیدگی‌ها و ساختارهای اشتباهی است که در لحظه در کد وجود دارند. این بوی بد توسعه سیستم‌ها را بسیار سخت تر می‌کند و هزینه و زمان زیادی را از توسعه‌دهندگان می‌گیرد.
</p>
<h3>
  4.Dispencables
</h3>
<p>
  این موارد، موارد بی‌مصرفی و غیر مهم و بی‌ استفاده‌ای هستند که صرفا کد را کثیف و شلوغ ‌میکنند و در واقع کاربردی ندارند. برای رفع این بوی بد باید این موارد را از کد حذف کرد و زدود.
</p>
<h3>
  5.Couplers
</h3>
<p>
  همه بوی‌های بد این گروه از جفت شدن زیاد کلاس ها به هم نتیجه ‌می‌شوند. برای راحت‌تر کردن ایجاد تغییر در کد و آسیب نزدن به منطق فعلی باید تا حد امکان coupling را در پروژه‌ها به حداقل رساند که تغییر دادن یک بخش منجر به از کار افتادن بخش‌های دیگر نشود.
</p>
<h2>
  سوال ۳
</h2>
<h3>
  این بوی بد در کدام یکی از دسته های پنج‌گانه قرار می‌گیرد؟
</h3>
<p>
  Dispencalbes
</p>
<h3>
  برای برطرف‌کردن این بو، استفاده از کدام بازآرایی‌ها پیشنهاد می‌شود؟
</h3>
<p>
  قطعه کدهایی که تقریبا استفاده ای ندارند باید با in-line class treatment فیکس شوند به علاوه این که برای subclass هایی که فانکشن‌های زیادی ندارند باید از collapsed hierarchy استفاده کرد.
</p>
<h3>
  در چه مواقعی باید این بو را نادیده گرفت؟
</h3>
<p>
  گاهی اوقات یک lazy class به منظور ترسیم اهداف توسعه آینده برای تیم توسعه ایجاد می شود، در این مورد، باید تلاش بر این باشد که تعادلی بین وضوحو شفافیت و سادگی در کد خود برقرار شود.
</p>
