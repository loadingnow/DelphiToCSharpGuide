Delphi to C#
=================


##首先 C# 中
---

## 1. 沒有全域變數，使用 `Class Function`

## 2. 區分大小寫

## 3. `string 是 "" , char 是 ''`

## 4. Unicode


##然後
---

## 1. 今天不講理論

## 2. 今天不講為什麼

## 3. 今天講什麼?


# Programer 用 Code 說話


##Class , 繼承, private, public
---

## `Delphi `
``` pascal
  TMyClass = class(TObject)
  private
  public
  end;
```
## `C#`
``` c
    public class Class1
    {
    }
    public class Class2 : Class1
    {
    }
```


##class(static) function, procedure
---

## `Delphi `
``` pascal
class procedure ClassProcedure(Aint: Integer);
class function ClassFunction(Aint: Integer): boolean;
```
## `C#`
``` c
public static bool ClassFunction(int aint)
{
    return true;
}
```


##變數型態, Nullable
---

## `Delphi `
``` pascal
private
    FintVar: Integer;
    FcharVar: Char;
    FstringVar: String;
    FdobuleVar: Double;
    FdatetimeVar: TDateTime;
```
## `C#`
``` c
    private int _intVar;
    private char _charVar;
    private string _stringVar;
    private double _doubleVar;
    private DateTime _datetimeVar;
    private Guid _guidVar;

    private int? _intVarN;
    private char? _charVarN;
    private string _stringVarN;
    private double? _doubleVarN;
    private DateTime? _datetimeVarN;
    private Guid? _guidVarN;
```


##property
---

## `Delphi `
``` pascal
public
    property IntVar: Integer read FintVar write FintVar;
    property charVar: Char read FcharVar write FcharVar;
    property stringVar: String read FstringVar write FstringVar;
    property dobuleVar: Double read FdobuleVar write FdobuleVar;
    property datetimeVar: TDateTime read FdatetimeVar write FdatetimeVar;
```
## `C#`
``` c
    public int IntVar { get; set; }
    public string StringVar
    {
        get { return _stringVar;  }
        set { _stringVar = value; }
    }
```


## Function 內部變數宣告跟賦值
---

## `Delphi `
``` pascal
var
   vInt: Integer;
begin
   vInt := 0;
end;
```
## `C#`
``` c
    int vInt0;
    int vInt1 = 0;
```


## 使用 C# Var 的時機點
---

## `C#`
``` c
var vInt2 = 0;          
//var some = CallFunction -> no, 因為看不出回傳值的型態，增加閱讀困難
//var some = new KnownClass
//var some = 0; -> knownType
```


## List, Array
---

## `Delphi `
``` pascal
var
   list: TStringList;
   arr1: Array[0..2] of Integer;
begin
   list := TStringList.Create;
```
## `C#`
``` c
    IList<string> list1;
    List<string> list2;
    var list3 = new List<string>();
    int[] arra1;
    int[] array2 = new[] {1, 2, 3};
    var array3 = new[] {1, 2, 3};
```


## Attribute(only c#)
---

## `C#`
``` c
    [Serializable]
    public class Class2 : Class1
```


## if , And , Or, else
---

## `Delphi `
``` pascal
   if vInt = 0 then
   begin

   end else if (vInt = 0) and (vInt = 1) or (vInt = 2) then
   begin

   end;
```
## `C#`
``` c
    if (vInt1 == 0)
    {
  
    } else if ((vInt1 == 0 && vInt1 == 1) || vInt1 == 2)
    {
      
    }
```


## 迴圈
---

## `Delphi `
``` pascal
   for vI := 0 to list.Count - 1 do
   begin
  
   end;
   vI := 0;
   while not vi <> list.count - 1 do
   begin
  
   end;
```
## `C#`
``` c
    for (int i = 0; i < list3.Count; i++)
    {          
    }
    foreach (var data in list3)
    {  
    }
    while (vInt1 == 0)
    {
    }
```


## Linq(only c#)
---

## `C#`
``` c
    public class Model
    {
        public string Id { get; set; }
        public string Name { get; set; }
    }
    var list4 = new List<Model>();
    var list5 = list4.Where(c => c.Name.StartsWith("A"));
    var list6 = list5.OrderBy(c => c.Id).ThenByDescending(c => c.Name).ToList();
    var list7 = from c in list4
                where c.Id == "AAAA"
                select c;
```


# 還有更多的語言特性


# 但運用這些就能寫出你原本能寫出的程式碼


# 前提是你在 Delphi 就有清楚的邏輯觀念


# 很複雜 ? 其實不


## 進化的 Delphi
---

## XE5(not only XE5, 更早的版本)
``` pascal
  TComponent = class(TPersistent, IInterface, IInterfaceComponentReference)
  private
    [Weak] FOwner: TComponent;
    FName: TComponentName;
    FTag: NativeInt;
    FComponents: TList<TComponent>;
    FFreeNotifies: TList<TComponent>;
```
``` pascal
  [RootDesignerSerializerAttribute('', '', False)]
  TApplication = class(TComponent)
  private type
    TBiDiKeyboard = record
      private
        BiDiKeyboard, NonBiDiKeyboard: string;
        BiDiKeyboardHKL, NonBiDiKeyboardHKL: HKL;
      public
        procedure SetBiDiKeyboard(const Value: string);
        procedure SetNonBiDiKeyboard(const Value: string);
        function GetBidiKeyboard: string; inline;
        function GetNonBidiKeyboard: string; inline;
        procedure ApplyBiDiKeyboardLayout;
        procedure ApplyNonBiDiKeyboardLayout;
    end;
  private
```


#還好，D4,5,7 的基礎觀念還是可以用


#但是，身為 Programer


#你的宿命是追逐不停向前的進步


#而程式語言只是工具


#侷限你的從來只是觀念而非語言


## 工具 (C#)
---

## ReSharp
   
###    更多的語法提示
###    建議的語法


## 作業 (C#)
---


#KISS(Keep it simple, stupid)


#百分之80 的時間，你都在維護現有程式 


#所以讓程式碼簡單到笨，讓人看得懂，而非簡潔到讓人看不懂 


#因為人看得懂才能改的動
