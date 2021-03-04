<div dir="rtl">

# POCO-VS-DTO

در این مخزن دو مفهوم DTO و POCO توضیح داده می شود

دو اصطلاح که مکررادر  توسعه نرم افزار .NET و C# بحث می شود DTO و POCO است و برخی از توسعه دهندگان اشتباها این دو اصلاح را به جای هم به کار می برند.بنابرین تفاوت اساسی DTO و POCO چیه؟بیاید اول این دو تا اصطلاح تعریف کنیم.

# Data Transfer Object (DTO)

DTO مخفف Data Transfer Object است و هدف نهایی آن انتقال داده است. و تنها باید داده داشته باشد ن منطق و رفتار اگر یک DTO منطق داشته باشد در اصل DTO نیست.اما منطق چیه؟
به طور کلی منطق یعنی یعنی عملیات و متد ها در یک نوع در حالی که DTO فقط شامل پراپرتی ه ها است و فقط باید داده ها را Get یا Set کند و هیچ ارزش یابی یا عملیاتی روی آن انجام  ندهد.

# تکلیف Attribute ها و Data Annotaion ها چیه؟

به طور کلی غیر معمول نیست که از فرا داده ها یا metadata ها در DTO به جای به منظور  تایید اعتبار مدل یا اهداف مشابه استفاده شود.برخی از attribute ها رفتاری به DTO اضافه نمی کنند بلکه رفتاری را در جای دیگری از سیستم تسهیل می کنند.اما قانون اضافه نکردن رفتار به DTO را نقض نمی کنند.

# تکلیف ViewModels و API models و ... چیه؟

اصطلاح DTO بسیار مبهم است.تمام منظور آن است که شی شامل فقط دیتا است ن رفتار.هیچ اطلاعاتی راجع به مورد استفاده نمی دهد.در بسیاری از معماری ها DTO ها می تواند تعداد زیادی از نقش ها خدمت کند.برای نمونه در بسیاری از معماری های MVC با ویو ها که از نوع داده ای پشتیبانی می کند.DTO ها برای ارسال و Bind  به ویو استفاده می شود.
دیتا
این DTO ها به طور کلی ViewModels نامیده می شود و به طور ایده آی نباید رفتار فقط نوع های داده ای دی ویو ها انتظار را برآورده می کند.بنابرین در این سناریو یک ViewModel یک نوع خاص از DTO است در حالی که معماری MVVM , ViewModel ها به طور معمول تعداد زیادی 
از رفتار ها را شامل می شود.بنارین مهم است که محتوا را قبل از فرضیات در نظر بگیریم
و در بعضی از برنامه های MVC گاهی اوقات منطق به ViewModels ها اضافه می شوند که دیگر DTO نیستند.


تاجایی که ممکنه نام DTO ها بر اساس مورد استفاده انتخاب کنید.مثلا نام FooDTO ایده ای  .از مورد استفاده این کلاس نمی دهد
اما نام FooViewModel نیت را بیان می کند.

به طور کلی DTO ها فقط داده دارند ن رفتار و منطق در حالی که POCO ها منطف هم دارند بنابرین DTO زیر مجموعه POCO است در زیر دو نمونه کد بیانگر DTO و POCO نمایش داده شده است.

</div>

```csharp
// DTO
public class ProductViewModel
{
  public int ProductId { get; set; }
  public string Name { get; set; }
  public string Description { get; set; }
  public string ImageUrl { get; set; }
  public decimal UnitPrice { get; set; }
}

public record ProductDTO
{
  public int Id { get; init; }
  public string Name { get; init; }
}

// usage
var dto = new ProductDTO { Id = 1, Name = "some name" };

//POCO

public class Product
{
  public Product(int id)
  {
    Id = id;
  }

  private Product()
  {
    // required for EF
  }

  public int Id { get; private set; }
  // other properties and methods
}

```

https://ardalis.com/dto-or-poco/

</div>
