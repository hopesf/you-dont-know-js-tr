# You Don't Know JS: Up & Going
# Bölüm 2: JavaScript'e Giriş

Önceki bölümde, programlamanın temel yapı taşlarını, değişkenler, döngüler, koşullu ifadeler ve fonksiyonlar gibi tanıttım. Tabii ki, gösterilen tüm kodlar JavaScript'te oldu. Ancak bu bölümde, bir JS developer olarak başlamak için bilmeniz gereken özelliklere odaklanmak istiyoruz.

Bu bölümde ilerleyen YDKJS kitaplarına kadar tam olarak keşfedilmeyecek birçok kavramı tanıtacağız. Bu bölümü, serinin geri kalanında detaylı olarak ele alınan konuların bir genel bakışı olarak düşünebilirsiniz.

Özellikle JavaScript'e yeni başlıyorsanız, buradaki kavramları ve kod örneklerini birkaç kez inceleyebilirsiniz. İyi bir temel tuğla tuğla döşenir, bu yüzden her şeyi ilk seferde hemen anlayacağınızı beklemeyin.

JavaScript'i derinlemesine öğrenme yolculuğunuz burada başlıyor.

**Not:** Birinci Bölümde belirttiğim gibi, bu bölümü okurken ve çalışırken kesinlikle bu kodları kendiniz denemelisiniz. Bu kodlardan bazıları, bu yazının yazıldığı sırada en yeni JavaScript sürümünde tanıtılan yetenekleri varsaymaktadır (genellikle "ES6" olarak adlandırılan ECMAScript'in 6. sürümü için -- JS spesifikasyonunun resmi adı). Eğer daha eski bir, ES6 öncesi bir tarayıcı kullanıyorsanız, kod işe yaramayabilir. Güncel ve modern bir tarayıcının (örneğin Chrome, Firefox veya IE) son sürümünü kullanmanız gerekmektedir.

## Değerler & Türler

Birinci Bölümde belirttiğimiz gibi, JavaScript'in tip değerleri vardır, tip belirli değişkenleri değil. Aşağıda yer alan yerleşik tipler mevcuttur:

* `string`
* `number`
* `boolean`
* `null`
* `undefined`
* `object`
* `symbol` (ES6 sürümüyle birlikte gelen tür)

JavaScript, bir değeri inceleyebilen ve size ne türde olduğunu söyleyebilen bir `typeof` operatörü sağlar:

```js
var a;
typeof a;				// "undefined"

a = "hello world";
typeof a;				// "string"

a = 42;
typeof a;				// "number"

a = true;
typeof a;				// "boolean"

a = null;
typeof a;				// "object" -- JavaScript dilinde bulunan ilginç bir bug

a = undefined;
typeof a;				// "undefined"

a = { b: "c" };
typeof a;				// "object"
```

`typeof` operatörünün dönüş değeri her zaman altı (ES6 ile yedi! - "symbol" türü eklenmiştir) dize değerinden biridir. Yani, typeof "abc" "string" olarak döner, "string" değil.

Bu parçada dikkatinizi çekmek istediğim şey, a değişkeninin her türlü farklı değeri tuttuğu ve görünüşe bakılırsa `typeof a`'nın "a'nın türü"nü sormadığınızı, aslında "şu an a içinde bulunan değerin türünü" sorduğunuzu görmektir. JavaScript'te yalnızca değerlerin türleri vardır; değişkenler sadece bu değerler için basit konteynerlerdir.

`typeof null`, ilginç bir durumdur, çünkü yanlışlıkla `"object"` olarak döner, oysa `"null"` olarak dönmesini beklersiniz.

**Uyarı:** Bu, JS'deki uzun süredir devam eden bir hata olup muhtemelen hiçbir zaman düzeltilmeyecek bir hata çünkü web üzerindeki çok fazla kod, bu hataya dayandığı için düzeltilmesi daha fazla hataya neden olur!

Ayrıca, `a = undefined` ifadesine dikkat edin. Açıkça `a`'yı `undefined` değerine ayarlıyoruz, ancak bu, `var a;` ifadesi ile baştaki örnekte olduğu gibi henüz değer atanmamış bir değişkenden farklı bir davranış göstermez. Bir değişken, fonksiyonların değer döndürmediği ve `void` operatörünün kullanımı dahil olmak üzere birkaç farklı şekilde bu "undefined" değerine ulaşabilir.

### Objects

`object` türü, her biri kendi türünde değerler tutan özellikleri (isimlendirilmiş konumlar) ayarlayabileceğiniz bileşik bir değeri ifade eder. Bu, muhtemelen JavaScript'in tüm değer türleri arasında en kullanışlı olanlarından biridir.

```js
var obj = {
	a: "hello world",
	b: 42,
	c: true
};

obj.a;		// "hello world"
obj.b;		// 42
obj.c;		// true

obj["a"];	// "hello world"
obj["b"];	// 42
obj["c"];	// true
```

Bu 'obj' değerini görsel olarak düşünmek faydalı olabilir:

<img src="fig4.png">

Objects'lerdeki değerlere ya nokta notasyonu kullanılarak (örneğin, `obj.a`) ya da köşeli parantez notasyonu kullanılarak (örneğin, `obj["a"]`) erişilebilir. Nokta notasyonu daha kısa ve genellikle daha okunaklıdır.

Köşeli parantez notasyonu, içinde özel karakterler bulunan bir özellik adınız varsa kullanışlıdır, örneğin `obj["hello world!"]` -- bu tür özelliklere, köşeli parantez notasyonuyla erişildiğinde genellikle *keys* denir. `[ ]` notasyonu ya bir değişken gerektirir (aşağıda açıklanmıştır) ya da bir `string` *literal* (ki `" .. "` veya `' .. '` ile çevrelenmelidir).

Elbette, köşeli parantez notasyonu, bir özellik/anahtar erişmek isterseniz, ancak adı başka bir değişkenin içinde saklanıyorsa da kullanışlıdır, örneğin:

```js
var obj = {
	a: "hello world",
	b: 42
};

var b = "a";

obj[b];			// "hello world"
obj["b"];		// 42
```

**Not:** JavaScript `object`'leri hakkında daha fazla bilgi için bu serinin *this & Object Prototypes* başlığını incelemeyi düşünebilirsiniz, özellikle 3. Bölümüne odaklanabilirsiniz.

JavaScript programlarında sıkça etkileşimde bulunacağınız birkaç başka değer türü daha vardır: *dizi (array)* ve *fonksiyon (function)*. Ancak bunlar kesin yerleşik türler olmaktan ziyade, daha çok `object` türünün özelleşmiş sürümleri olarak düşünülmelidir.

#### Arrays (Diziler)

Bir Array, adlandırılmış key/value yerine sayısal indeksli pozisyonlarda değerleri (herhangi bir türde) tutan bir `object`'dir. Örneğin:

```js
const arr = [
	"hello world",
	42,
	true
];

arr[0];			// "hello world"
arr[1];			// 42
arr[2];			// true
arr.length;		// 3

typeof arr;		// "object"
```

**Not:** JS array'deki ilk öğenin indeksini `0` olarak kullanırlar.

Görsel olarak `arr`ı düşünmek faydalı olabilir:

<img src="fig5.png">

Because arrays are special objects (as `typeof` implies), they can also have properties, including the automatically updated `length` property.

You theoretically could use an array as a normal object with your own named properties, or you could use an `object` but only give it numeric properties (`0`, `1`, etc.) similar to an array. However, this would generally be considered improper usage of the respective types.

The best and most natural approach is to use arrays for numerically positioned values and use `object`s for named properties.

Çünkü array'ler özel object'lerdir (bu, `typeof` tarafından belirtilir), bu nedenle otomatik olarak güncellenen `length` özelliği dahil olmak üzere built-in özelliklere sahip olabilirler.

Teorik olarak, bir `array`'i kendi adlandırılmış özellikleri olan normal bir object olarak kullanabilirsiniz veya bir `object` kullanabilirsiniz.

En iyi ve en doğal yaklaşım, sayısal pozisyondaki değerler için `array`'leri ve adlandırılmış özellikler için `object`'leri kullanmaktır.

#### Functions (Fonksiyonlar)

JS programlarınızın tamamında kullanacağınız diğer `object` alt türü, fonksiyonlar:

```js
function foo() {
	return 42;
}

foo.bar = "hello world";

typeof foo;			// "function"
typeof foo();		// "number"
typeof foo.bar;		// "string"
```

Fonksiyonlar `object`'lerin bir alt türüdür -- `typeof` "function" olarak döner, bu da bir `function`'ın ana tür olduğunu ima eder -- ve bu nedenle özelliklere sahip olabilir, ancak genellikle fonksiyon nesne özelliklerini (örneğin `foo.bar`) sınırlı durumlarda kullanırsınız.

**Not:** JS değerleri ve türleri hakkında daha fazla bilgi için bu serinin *Types & Grammar* başlığının ilk iki bölümünü incelemeyi düşünebilirsiniz.

### Built-In Type Methods (Yerleşik Tür Methodları)

Built-in types oldukça güçlü ve faydalı olan özellikler ve yöntemler olarak açığa çıkan davranışlara sahiptir.

Örnek olarak:

```js
var a = "hello world";
var b = 3.14159;

a.length;				// 11
a.toUpperCase();		// "HELLO WORLD"
b.toFixed(4);			// "3.1416"
```

`a.toUpperCase()` çağrısını bir string değeri tutan değişken üzerinde yapabilmenin arkasındaki "nasıl" daha karmaşıktır, yalnızca bu yöntemin değer üzerinde mevcut olmasıyla sınırlı değildir.

Kısaca, tip olarak "native" olarak adlandırılan, birincil `string` türü ile eşleşen bir `String` (büyük "S") türünde nesne sarmalayıcı form vardır; `toUpperCase()` yöntemini prototype'ında tanımlayan da bu nesne sarmalayıcıdır.

Bir `object` olarak `"hello world"` gibi ilkel değeri bir özelliğe veya yönteme referansla kullandığınızda (örneğin, önceki örnekteki gibi `a.toUpperCase()`), JS, değeri otomatik olarak ilgili nesne sarmalayıcı karşılığına ("boxed") dönüştürür (kapakların altında gizlenir).

Bir `string` değeri bir `String` nesnesi tarafından sarmalanabilir, bir `number` bir `Number` nesnesi tarafından sarmalanabilir ve bir `boolean` bir `Boolean` nesnesi tarafından sarmalanabilir. Çoğu durumda, bu değerlerin nesne sarmalayıcı formlarıyla ilgilenmenize veya doğrudan kullanmanıza gerek yoktur -- neredeyse tüm durumlarda ilkel değer formlarını tercih edin ve JavaScript gerisini sizin için halledecektir.

**Not:** JS native türleri ve "boxing" hakkında daha fazla bilgi için bu serinin *Types & Grammar* başlığının 3. Bölümünü incelemeyi düşünebilirsiniz. Bir nesnenin prototype'ını daha iyi anlamak için bu serinin *this & Object Prototypes* başlığının 5. Bölümüne göz atabilirsiniz.

### Değerleri Karşılaştırma (Comparing Values)

JavaScript programlarınızda yapmanız gereken iki temel değer karşılaştırma türü vardır: *eşitlik* ve *eşitsizlik* (*equality* and *inequality*). Herhangi bir karşılaştırmanın sonucu, karşılaştırılan değer türleri ne olursa olsun katı bir `boolean` değeri (`true` veya `false`) döner.

#### Type Coercion (Tür Dönüşümü)

Bölüm 1'de coercion'dan kısaca bahsetmiştik ama gelin burada tekrar ele alalım.

JavaScript'te, Coercion (dönüşüm), iki türde gelir: *açık* (explicit) ve *kapalı* (implicit). Açık dönüşüm, bir türden diğerine dönüşümün koddan açıkça görülebildiği durumlarda gerçekleşirken, kapalı dönüşüm, tür dönüşümünün diğer işlemlerin daha az açık bir yan etkisi olarak gerçekleşebileceği durumları ifade eder.

Belki de dönüşümün bazı şaşırtıcı sonuçlar üretebileceği yerler açısından "dönüşüm kötüdür" gibi ifadeleri duymuşsunuzdur.

Dönüşüm kötü değildir ve şaşırtıcı olmak zorunda değildir. Aslında, tür dönüşümü ile oluşturabileceğiniz çoğu durum oldukça mantıklı ve anlaşılabilir ve kodunuzu daha okunaklı hale getirmenize bile yardımcı olabilir. Ancak bu konudaki tartışmaya çok fazla girmeyeceğiz - bu serinin *Types & Grammar* başlığının 4. Bölümü tüm yönleri ele alır.

*explicit* coercion için bir örnek:

```js
var a = "42";

var b = Number( a );

a;				// "42"
b;				// 42 -- the number!
```

*implicit* coercion için bir örnek

```js
var a = "42";

var b = a * 1;	// "42" implicitly coerced to 42 here

a;				// "42"
b;				// 42 -- the number!
```

#### Truthy & Falsy 

Birinci Bölümde, değerlerin "truthy" ve "falsy" özelliklerinden kısaca bahsettik: `boolean` olmayan değer `boolean` türüne dönüştürüldüğünde sırasıyla `true` veya `false` olur mu?

JavaScript'teki "falsy" değerlerin belirli listesi şu şekildedir:

* `""` (empty string)
* `0`, `-0`, `NaN` (invalid `number`)
* `null`, `undefined`
* `false`

Bu "falsy" listesinde olmayan herhangi bir değer "truthy" olarak kabul edilir. İşte bu "truthy" değerlere örnekler:

* `"hello"`
* `42`
* `true`
* `[ ]`, `[ 1, "2", 3 ]` (arrays)
* `{ }`, `{ a: 42 }` (objects)
* `function foo() { .. }` (functions)

It's important to remember that a non-`boolean` value only follows this "truthy"/"falsy" coercion if it's actually coerced to a `boolean`. It's not all that difficult to confuse yourself with a situation that seems like it's coercing a value to a `boolean` when it's not.

Önemli olan, `boolean` olmayan bir değerin yalnızca `boolean` türüne dönüştürüldüğünde "truthy"/"falsy" dönüşümü izlediğini hatırlamaktır. Bir değeri `boolean` türüne dönüştürüyormuş gibi görünen ancak gerçekte dönüştürmeyen bir durumla karşılaşabiliriz.

#### Eşitlik (Equality)

JavaScript'te dört adet eşitlik operatörü bulunur: `==`, `===`, `!=` ve `!==`. `!` biçimleri, elbette karşıtları olan simetrik "eşit değil" versiyonlarıdır; *non-equality* ile *inequality* karıştırılmamalıdır.

`==` ile `===` arasındaki fark genellikle şu şekilde tanımlanır: `==`, değer eşitliğini kontrol ederken `===`, hem değer hem de tür eşitliğini kontrol eder. Onları doğru bir şekilde tanımlamanın yolu, `==`'in dönüşüme izin veren değer eşitliğini kontrol ettiği, `===`'in ise dönüşüme izin vermeden değer eşitliğini kontrol ettiği şeklinde olmalıdır; bu nedenle `===` genellikle "katı eşitlik" olarak adlandırılır.

`==` gevşek-eşitlik karşılaştırmasına izin verilen dolaylı dönüşümü düşünün ve `===` katı-eşitlik ile izin verilmeyen dönüşümü düşünün:

```js
var a = "42";
var b = 42;

a == b;			// true
a === b;		// false
```

`a == b` karşılaştırmasında, JavaScript türlerin uyuşmadığını fark eder, bu nedenle türleri eşleşene kadar bir veya her iki değeri farklı bir türe dönüştürmek için sıralı bir dizi adıma geçer ve ardından basit bir değer eşitliği kontrol edilebilir.

Düşünün ki, `a == b` ifadesi, dönüşüm yoluyla `true` sonucunu verebilecek iki olası yolu vardır. Ya karşılaştırma sonucu `42 == 42` olur ya da `"42" == "42"` olabilir. Hangisi doğru?

Cevap: `"42"`, karşılaştırmayı `42 == 42` yapmak için `42`'ye dönüşür. Bu kadar basit bir örnekte, bu sürecin hangi yönde gittiği gerçekten önemli gibi görünmez, çünkü sonuç aynıdır. Ancak sonuçtan daha da önemli olan, karşılaştırmanın sonucu değil, o sonuca nasıl ulaşıldığıdır, bu gibi durumlarda daha karmaşık durumlar vardır.

`a === b`, dönüşüme izin verilmediği için, basit değer karşılaştırması açıkça başarısız olur ve `false` üretir. Birçok geliştirici, `===`'ın daha tahmin edilebilir olduğunu düşünür ve her zaman bu operatörü kullanmayı ve `==`'den kaçınmayı savunur. Bu görüşün çok dar bir bakış açısı olduğuna inanıyorum. `==`, programınıza yardımcı olan güçlü bir araç olduğuna inanıyorum, *nasıl çalıştığını öğrenmeye zaman ayırırsanız*.

`==` karşılaştırmalarındaki dönüşümün tüm ayrıntılarını burada kapsamayacağız. Çoğu mantıklı olsa da, dikkatli olunması gereken bazı önemli noktalar vardır. Tam kuralları görmek için ES5 özelliklerinin 11.9.3 bölümünü (http://www.ecma-international.org/ecma-262/5.1/) okuyabilirsiniz ve bu mekanizmanın, etrafındaki olumsuz eleştirilere göre ne kadar basit olduğuna şaşıracaksınız.

Birçok ayrıntıyı birkaç basit öğrenmeye dökmek ve çeşitli durumlarda `==` veya `===` kullanmanız gerekip gerekmediğini bilmek ve size yardımcı olmak için işte basit kurallarım:

* Bir karşılaştırmadaki herhangi bir değer (yani taraf), `true` veya `false` değeri olabilirse, `==` yerine `===` kullanın.
* Bir karşılaştırmadaki herhangi bir değer, belirli değerlerden biri (`0`, `""` veya `[]` - boş dizi) olabilirse, `==` yerine `===` kullanın
* *Tüm diğer durumlarda*, `==` kullanmak güvenlidir. Aynı zamanda birçok durumda kodunuzu okunabilirliği artıran bir şekilde basitleştirir.

What these rules boil down to is requiring you to think critically about your code and about what kinds of values can come through variables that get compared for equality. If you can be certain about the values, and `==` is safe, use it! If you can't be certain about the values, use `===`. It's that simple.

Bu kuralların temelinde, kodunuzu eleştirel bir şekilde düşünmenizi ve eşitlik için karşılaştırılan değişkenler aracılığıyla hangi türden değerlerin gelebileceğini düşünmenizi gerektirir. Değerler hakkında kesin olabiliyorsanız ve `==` güvenliyse, onu kullanın! Değerler hakkında kesin olamıyorsanız, `===` kullanın. Bu kadar basit.

`!=` eşit olmayan biçimi `==` ile eşleşirken, `!==` biçimi `===` ile eşleşir. Şimdi tartıştığımız tüm kurallar ve gözlemler, bu eşit olmayan karşılaştırmalar için de simetrik olarak geçerlidir.

Eğer iki temel olmayan değeri, yani `object`leri (bu arada `function` ve `array`leri) karşılaştırıyorsanız, `==` ve `===` karşılaştırma kurallarına özel bir şekilde dikkat etmelisiniz. Çünkü bu değerler aslında referans tarafından tutulur ve hem `==` hem de `===` karşılaştırmaları sadece referansların eşleşip eşleşmediğini kontrol eder, altındaki değerler hakkında herhangi bir şeyi kontrol etmez.

Örneğin, `array`lar varsayılan olarak virgüllerle (`,`) arasına eklenerek `string`lere dönüştürülür. Aynı içeriğe sahip iki `array`ın `==` olarak eşit olacağını düşünebilirsiniz, ancak eşit değillerdir:

```js
var a = [1,2,3];
var b = [1,2,3];
var c = "1,2,3";

a == c;		// true
b == c;		// true
a == b;		// false
```

**Not:** `==` eşitlik karşılaştırma kuralları hakkında daha fazla bilgi için ES5 özelliklerinin 11.9.3 bölümünü inceleyebilirsiniz ve bu seriye ait *Types & Grammar* başlığının 4. bölümünü de incelemek isteyebilirsiniz; değerlerin referanslara karşı ne anlama geldiği hakkında daha fazla bilgi için 2. bölüme başvurun.

#### Eşitsizlik (Inequality)

`<`, `>`, `<=` ve `>=` operatörleri, "ilişkisel karşılaştırma" olarak belirtilen eşitsizlik için kullanılır. Genellikle sayılar gibi sıralanabilir değerlerle kullanılırlar. Örneğin `3 < 4` kolayca anlaşılabilir.

Ancak JavaScript `string` değerleri de tipik alfabeye göre eşitsizlik karşılaştırması için kullanılabilir, `"bar" < "foo"` gibi.

Dönüşüm konusunda ne oluyor? Eşitsizlik operatörleri için `==` karşılaştırma ile benzer kurallar (tam olarak aynı olmasa da) uygulanır. Özellikle, dönüşümü engelleyen "katı eşitsizlik" operatörleri `===` ile aynı şekilde çalışmayan "katı eşitsizlik" operatörleri yoktur.

Örnek olarak:

```js
var a = 41;
var b = "42";
var c = "43";

a < b;		// true
b < c;		// true
```

What happens here? In section 11.8.5 of the ES5 specification, it says that if both values in the `<` comparison are `string`s, as it is with `b < c`, the comparison is made lexicographically (aka alphabetically like a dictionary). But if one or both is not a `string`, as it is with `a < b`, then both values are coerced to be `number`s, and a typical numeric comparison occurs.

The biggest gotcha you may run into here with comparisons between potentially different value types -- remember, there are no "strict inequality" forms to use -- is when one of the values cannot be made into a valid number, such as:

Burada ne olur? ES5 özelliklerinin 11.8.5 bölümünde, `<` karşılaştırmasındaki her iki değer de `string` ise, örneğin `b < c` gibi, karşılaştırmanın leksikografik olarak (sözlük gibi alfabetik olarak) yapıldığı belirtilir. Ancak biri veya her ikisi de `string` değilse, örneğin `a < b` gibi, her iki değer de `number` olacak şekilde dönüştürülür ve tipik bir sayı karşılaştırması gerçekleşir.

Potansiyel olarak farklı değer türleri arasındaki karşılaştırmalarda dikkat etmeniz gereken nokta, "katı eşitsizlik" biçimlerinin olmamasıdır. Özellikle, değerlerden birinin geçerli bir sayıya dönüştürülemeyeceği durumlar gibi:

```js
var a = 42;
var b = "foo";

a < b;		// false
a > b;		// false
a == b;		// false
```

Wait, how can all three of those comparisons be `false`? Because the `b` value is being coerced to the "invalid number value" `NaN` in the `<` and `>` comparisons, and the specification says that `NaN` is neither greater-than nor less-than any other value.

The `==` comparison fails for a different reason. `a == b` could fail if it's interpreted either as `42 == NaN` or `"42" == "foo"` -- as we explained earlier, the former is the case.

🚨 Bu üç karşılaştırma nasıl tamamıyla `false` olabilir? Çünkü `<` ve `>` karşılaştırmalarında `b` değeri "geçersiz sayı değeri" olan `NaN`'a dönüştürülüyor ve belirtilene göre `NaN`, diğer herhangi bir değerden büyük veya küçük değildir.

`==` karşılaştırması ise farklı bir nedenle başarısız olur. `a == b`, ya `42 == NaN` olarak yorumlanabilir ya da `"42" == "foo"` olarak yorumlanabilir. Daha önce açıkladığımız gibi, ilk durum böyledir.

**Not:** Eşitsizlik karşılaştırma kuralları hakkında daha fazla bilgi için ES5 özelliklerinin 11.8.5 bölümünü inceleyebilirsiniz ve ayrıca bu serinin *Types & Grammar* başlığının 4. bölümünü incelemek isteyebilirsiniz. Bu kaynaklar, JavaScript'te eşitsizlik karşılaştırmalarının nasıl çalıştığını daha ayrıntılı bir şekilde açıklayacaktır.

## (Değişkenler) Variables

JavaScript'de, değişken adları (fonksiyon adları dahil) geçerli tanımlayıcılar (identifiers) olmalıdır. Geçerli tanımlayıcılar için katı ve tam kurallar, Unicode gibi geleneksel olmayan karakterleri düşündüğünüzde biraz karmaşık olabilir. Ancak yalnızca tipik ASCII alfasayısal karakterleri düşünüyorsanız, kurallar basittir.

Bir tanımlayıcı (`identifier`), `a`-`z`, `A`-`Z`, `$` veya `_` ile başlamalıdır. Daha sonra başlangıç karakteri, harf (`0`-`9`), alt çizgi veya dolar işareti gibi karakterleri içerebilir.

Genellikle, bir özellik adına uygulanan kurallar, bir değişken tanımlayıcısına uygulanan kurallarla aynıdır. Ancak bazı kelimeler değişken olarak kullanılamaz, ancak özellik adları olarak kullanılabilir. Bu kelimeler "rezerve edilmiş kelimeler" (reserved words) olarak adlandırılır ve bunlar JavaScript anahtar kelimeleri (`for`, `in`, `if`, vb.) ile birlikte `null`, `true` ve `false` gibi değerleri içerir.

Bu kurallar, JavaScript'te değişkenler oluştururken ve nesne özellik adları belirlerken takip edilmesi gereken önemli kurallardır.

**Not:** Daha fazla bilgi için, bu serinin *Types & Grammar* başlığının Ek A bölümüne başvurabilirsiniz. Bu bölüm, rezerve edilmiş kelimeler(reserved words) hakkında daha fazla ayrıntı içerir.

### (Fonksiyon Kapsamları) Function Scopes

`var` anahtar kelimesini kullanarak bir değişkeni mevcut işlev kapsamına veya herhangi bir işlevin dışında, en üst düzeyde global kapsama ait olarak tanımlayabilirsiniz.

#### Hoisting

Herhangi bir kapsam içinde bir `var` göründüğünde, bu bildiri, tüm kapsama ait kabul edilir ve her yerden erişilebilir.

Benzetme olarak, bu davranışa *yukarı taşıma (hoisting)* denir; bir `var` bildirimi kavramsal olarak çevresel kapsamının en üstüne "taşındığında". Teknik olarak, bu süreç, kodun nasıl derlendiğinin daha kesin bir açıklaması ile açıklanır, ancak şu an için bu ayrıntıları atlayabiliriz.

Örnek olarak:

```js
var a = 2;

foo();					// works because `foo()`
						// declaration is "hoisted"

function foo() {
	a = 3;

	console.log( a );	// 3

	var a;				// declaration is "hoisted"
						// to the top of `foo()`
}

console.log( a );	// 2
```

**Uyarı ⚠️:** It's not common or a good idea to rely on variable *hoisting* to use a variable earlier in its scope than its `var` declaration appears; it can be quite confusing. It's much more common and accepted to use *hoisted* function declarations, as we do with the `foo()` call appearing before its formal declaration.

Değişken *yukarı taşıma (hoisting)*ya güvenmek, bir değişkenin `var` bildirimi görünmeden önce kapsamında kullanılması yaygın veya iyi bir fikir değildir; oldukça kafa karıştırıcı olabilir. *Yukarı taşınmış (hoisted)* işlev bildirimlerini kullanmak, resmi bildiriminden önce görünen `foo()` çağrısında olduğu gibi, çok daha yaygın ve kabul edilir bir yaklaşımdır.

#### Nested Scopes (İç içe kapsamlar)

Bir değişkeni tanımladığınızda, o kapsam içinde olduğu gibi, daha düşük/dahil kapsamlarda da herhangi bir yerde kullanılabilir. Örneğin:

```js
function foo() {
	var a = 1;

	function bar() {
		var b = 2;

		function baz() {
			var c = 3;

			console.log( a, b, c );	// 1 2 3
		}

		baz();
		console.log( a, b );		// 1 2
	}

	bar();
	console.log( a );				// 1
}

foo();
```

`c`'nin, yalnızca iç içe geçmiş `baz()` kapsamında tanımlandığı için `bar()` içinde kullanılamadığını ve `b`'nin de aynı nedenle `foo()` için kullanılamadığına dikkat edelim ✅.

If you try to access a variable's value in a scope where it's not available, you'll get a `ReferenceError` thrown. If you try to set a variable that hasn't been declared, you'll either end up creating a variable in the top-level global scope (bad!) or getting an error, depending on "strict mode" (see "Strict Mode"). Let's take a look:

Bir değişkenin değerine, mevcut olmadığı bir kapsamda (scope'da) erişmeye çalışırsanız, bir `ReferenceError` hatası alırsınız. Tanımlanmamış bir değişkeni ayarlamaya çalışırsanız, ya en üst düzey global kapsamda bir değişken oluşturursunuz (kötü bir uygulama!) ya da bir hata alırsınız; bu, "Strict Mode"a (Bkz. "Strict Mode") bağlıdır. İşte bir örnek:

```js
function foo() {
	a = 1;	// `a` not formally declared
}

foo();
a;			// 1 -- oops, auto global variable :(
```

Bu kötü bir uygulamadır. Her zaman değişkenlerinizi resmi olarak tanımlayın.

ES6, değişkenleri bağımsız bloklara (`{ .. }` çiftleri) ait olacak şekilde `let` anahtar kelimesini kullanarak tanımlamanıza olanak tanır. Bazı ince ayrıntılar haricinde, kapsam kuralları, işlevlerle gördüğümüz gibi yaklaşık olarak aynı şekilde davranacaktır: 💯

```js
function foo() {
	var a = 1;

	if (a >= 1) {
		let b = 2;

		while (b < 5) {
			let c = b * 2;
			b++;

			console.log( a + c );
		}
	}
}

foo();
// 5 7 9
```

`var` yerine `let` kullanmanız nedeniyle, `b` yalnızca `if` ifadesine ait olacak ve bu nedenle `foo()` işlevinin genel kapsamına ait olmayacaktır. Benzer şekilde, `c` yalnızca `while` döngüsüne ait olur. Blok kapsama, değişken kapsamlarını daha ince bir şekilde yönetmek için çok kullanışlıdır ve bu, kodunuzu zaman içinde daha kolay bakım yapılabilir hale getirebilir. ✨

**Not:** Kapsam hakkında daha fazla bilgi için, bu seri içindeki *Scope & Closures* başlığını inceleyebilirsiniz. `let` blok kapsama hakkında daha fazla bilgi için ise bu seri içindeki *ES6 & Beyond* başlığını inceleyebilirsiniz. Bu kaynaklar, kapsam ve `let` kullanımı hakkında daha fazla ayrıntı sunacaktır.

## Conditionals (Koşullu Durumlar)

Bölüm 1'de kısaca tanıttığımız `if` ifadesine ek olarak, JavaScript'te göz atmanız gereken birkaç başka koşullu mekanizma bulunmaktadır.

Bazen kendinizi aşağıdaki gibi bir dizi `if..else..if` ifadesi yazarken bulabilirsiniz:

```js
if (a == 2) {
	// do something
}
else if (a == 10) {
	// do another thing
}
else if (a == 42) {
	// do yet another thing
}
else {
	// fallback to here
}
```

Bu yapı işe yarar, ancak her durum için `a` testini belirtmeniz gerektiği için biraz kod kalabalığı oluşturur. İşte başka bir seçenek, `switch` ifadesi:

```js
switch (a) {
	case 2:
		// do something
		break;
	case 10:
		// do another thing
		break;
	case 42:
		// do yet another thing
		break;
	default:
		// fallback to here
}
```

`break`, yalnızca bir `case` içindeki ifadelerin çalışmasını istiyorsanız önemlidir. Bir `case` içinde `break`'i atladıysanız ve bu `case` eşleşirse veya çalışırsa, çalışma, eşleşip eşleşmemesine bakılmaksızın bir sonraki `case`'in ifadeleriyle devam eder. Bu duruma "düşme (fall)" denir ve bazen kullanışlı veya istenir:

```js
switch (a) {
	case 2:
	case 10:
		// some cool stuff
		break;
	case 42:
		// other stuff
		break;
	default:
		// fallback
}
```

Burada, eğer `a`, `2` veya `10` ise, "some cool stuff" kod ifadelesini çalıştıracaktır.

JavaScript'te başka bir koşullu ifade türü, genellikle "ternary operatör" olarak adlandırılan "koşullu operatördür". Bu, tek bir `if..else` ifadesinin daha özgün bir biçimidir ve şu şekildedir: 🎉

```js
var a = 42;

var b = (a > 41) ? "hello" : "world";

// similar to:

// if (a > 41) {
//    b = "hello";
// }
// else {
//    b = "world";
// }
```

Test ifadesi (`a > 41` burada) "true" olarak değerlendirilirse, ilk ifade (`"hello"`) sonuçlanır; aksi takdirde ikinci ifade (`"world"`) sonuçlanır ve sonuç `b`'ye atanır.

Koşullu operatör bir atama işleminde kullanılması gerekmez, ancak bu kesinlikle en yaygın kullanım şeklidir.

**Not:** Koşullu ifadeleri ve `switch` ile `? :` için diğer yapılar hakkında daha fazla bilgi için, bu seri içindeki *Types & Grammar* başlığını inceleyebilirsiniz. Bu kaynaklar, koşullu ifadelerin ve kontrol yapılarının daha fazla ayrıntısını sunacaktır.

## Strict Mode

ES5 added a "strict mode" to the language, which tightens the rules for certain behaviors. Generally, these restrictions are seen as keeping the code to a safer and more appropriate set of guidelines. Also, adhering to strict mode makes your code generally more optimizable by the engine. Strict mode is a big win for code, and you should use it for all your programs.

You can opt in to strict mode for an individual function, or an entire file, depending on where you put the strict mode pragma:

ES5, dil için bazı davranışlar için kuralları sıkılaştıran "strict mode" adını verdiği bir özellik ekledi. Genellikle, bu kısıtlamalar, kodun daha güvenli ve uygun bir dizi kılavuza uymasını sağlamak olarak görülür. Ayrıca, strict mode kurallarına uymak, kodunuzu genellikle motor tarafından daha iyi optimize edilebilir kılar. Strict mode, kod için büyük bir kazançtır ve tüm programlarınız için kullanmalısınız.

Strict mode'u, strict mode belirleyicisini nereye koyduğunuza bağlı olarak, bireysel bir işlev veya tüm bir dosya için etkinleştirebilirsiniz:

```js
function foo() {
	"use strict";

	// burası strict mode'da çalışır

	function bar() {
		// burası strict mode'da çalışır
	}
}

// burası strict mode'da çalışmaz
```

Compare that to:

```js
"use strict";

function foo() {
	// burası strict mode'da çalışır

	function bar() {
		// burası strict mode'da çalışır
	}
}

// burası strict mode'da çalışır
```

Strict mode ile önemli bir fark (iyileşme!), `var` anahtar kelimesini kullanmadan otomatik global değişken bildirimini engellemesidir. Bu, değişkenlerin açık bir şekilde `var`, `let` veya `const` ile tanımlandığında tanınması ve beklenmeyen global değişkenlerin oluşturulmasını engeller. Bu, kodun daha güvenli ve öngörülebilir olmasına yardımcı olur.


```js
function foo() {
	"use strict";	// strict mode'u aktif hale getirme
	a = 1;			// `var` missing, ReferenceError  (vereceği hata)
}

foo();
```

Kodunuzda strict mode'u etkinleştirirseniz ve hatalar alırsanız veya kodunuzun beklenmedik davranışlar sergilemeye başladığını fark ederseniz, bu durumda strict mode'tan kaçınma eğiliminde olabilirsiniz. Ancak bu içgüdüyü tatmin etmek kötü bir fikir olurdu. Strict mode, programınızda sorunlara yol açıyorsa, neredeyse kesinlikle programınızda düzeltmeniz gereken şeyler olduğunun bir işaretidir.

Strict mode, yalnızca kodunuzu daha güvenli bir yolda tutmaz ve yalnızca kodunuzu daha iyi optimize edebilir, aynı zamanda dilin gelecekteki yönelimini temsil eder. Katı kipi şimdi kullanmaya alışmak, daha sonra ertelemeye devam etmekten daha kolay olacaktır.

**Note:** Strict mode hakkında daha fazla bilgi için, bu seri içindeki *Types & Grammar* başlığının 5. bölümüne başvurabilirsiniz. Bu kaynak, katı kipin detaylarını daha ayrıntılı bir şekilde açıklayacaktır.

## Functions As Values (Değer olarak Fonksiyonlar)

Şu ana kadar, JavaScript'te *kapsamın (scope)* temel mekanizması olarak fonksiyonları tartıştık. Tipik `function` bildirimi sözdizimini aşağıdaki gibi hatırlıyorsunuz:


```js
function foo() {
	// ..
}
```

Bu kod bloğunda açıkça görünmese de, `foo` aslında sadece dış kapsamda bir değişken olarak düşünülür ve bu değişkene bildirilen `function`a bir başvuru verilir. Yani, `function` kendisi bir değerdir, `42` veya `[1,2,3]` gibi.

Bu başlangıçta garip bir kavram gibi gelebilir, bu nedenle bir an düşünün. Bir fonksiyona bir değeri (argüman) iletebilirsiniz, ancak *bir fonksiyon kendisi de bir değer olabilir* ve değişkenlere atanabilir veya başka fonksiyonlara iletilip döndürülebilir.

Bu nedenle, bir fonksiyon değeri, diğer herhangi bir değer veya ifade gibi bir ifade olarak düşünülmelidir.

Örnek olarak:

```js
var foo = function() {
	// ..
};

var x = function bar(){
	// ..
};
```

`foo` değişkenine atanmış olan ilk fonksiyon ifadesine, adı olmadığı için *anonim (anonymous)* denir.

İkinci fonksiyon ifadesi *isimli (named)* (`bar`) olarak adlandırılır, aynı zamanda bir referansı da `x` değişkenine atanır. *İsimli fonskiyon ifadeleri (Named function expressions)* genellikle tercih edilir, ancak *anonim fonksiyon ifadeleri (anonymous function expressions)* hala oldukça yaygındır.

Daha fazla bilgi için bu serinin *Scope & Closures* başlığına bakabilirsiniz.

### Immediately Invoked Function Expressions (IIFEs) (Hemen Çağrılan Fonksiyon İfadeleri)

Önceki örnekte, hiçbir fonksiyon ifadesi çalıştırılmaz -- örneğin `foo()` veya `x()` dahil etmiş olsaydık çalıştırabilirdik.

Bir fonksiyon ifadesini çalıştırmanın başka bir yolu vardır, bu genellikle *hemen çağrılan fonksiyon ifadesi* (IIFE) olarak adlandırılır:

```js
(function IIFE(){
	console.log( "Hello!" );
})();
// "Hello!"
```

Dışarıdaki `( .. )`, `(function IIFE(){ .. })` fonksiyon ifadesinin normal bir fonksiyon bildirimi olarak ele alınmasını önlemek için gereken bir JS dil ayrıntısıdır.

İfade sonundaki `()` -- `})();` satırı -- gerçekte hemen öncesinde başvurulan fonksiyon ifadesini çalıştıran şeydir.

Bu garip gelebilir, ancak ilk bakışta olduğu kadar yabancı değildir. Buradaki `foo` ve `IIFE` arasındaki benzerlikleri düşünün:

```js
function foo() { .. }

// `foo` fonksiyon referans ifadesi,
// `()` fonksiyonu çalıştırır
foo();

// `IIFE` fonksiyon ifadesi,
// `()` fonksiyonu çalıştırır
(function IIFE(){ .. })();
```

Gördüğünüz gibi, `(function IIFE(){ .. })`'yi çalıştırmadan önce listelemek, `()`'yi çalıştırmadan önce `foo`'yu eklemekle temelde aynıdır; her iki durumda da fonksiyon başvurusu, hemen ardından `()` ile çalıştırılır.

Bir IIFE yalnızca bir fonksiyon olduğundan ve fonksiyonlar da değişken *kapsamı* oluşturduğundan, bu şekilde bir IIFE kullanmak, IIFE dışındaki çevre kodu etkilemeyen değişkenlerin bildirildiği sıkça kullanılır:

```js
var a = 42;

(function IIFE(){
	var a = 10;
	console.log( a );	// 10
})();

console.log( a );		// 42
```

IIFEs bir değer de döndürebilir:

```js
var x = (function IIFE(){
	return 42;
})();

x;	// 42
```

Çalıştırılan `IIFE` adlı fonksiyondan `42` değeri `return` edilir ve ardından `x` değişkenine atanır.

### Closure

*Closure*, JavaScript'te en önemli ve genellikle en az anlaşılan kavramlardan biridir. Burada derinlemesine detayına girmeyeceğim ve sizi bu serinin *Scope & Closures* başlığına yönlendireceğim. Ancak genel kavramı anlamanız için birkaç şey söylemek istiyorum. JavaScript beceri setinizde en önemli tekniklerden biri olacak.

Closure, bir işlevin çalışması bittikten sonra bile işlevin kapsamını (değişkenlerini) "hatırlama" ve erişme yolu olarak düşünebilirsiniz.

Örnek olarak:

```js
function makeAdder(x) {
    // Parametre `x`, iç değişken

    // İç fonksiyon `add()`, `x`'i kullanır, bu yüzden
    // üzerinde bir "closure" bulunur.
    function add(y) {
        return y + x;
    }

    return add;
}
```

Her çağrıda dıştaki `makeAdder(..)` fonksiyonuna dönen iç `add(..)` fonksiyonuna yapılan referans, `makeAdder(..)`'a geçirilen herhangi bir `x` değerini hatırlayabilir. Şimdi `makeAdder(..)`'ı kullanalım:

```js
// `plusOne`, dıştaki `makeAdder(..)`'ın `x` parametresi üzerinde closure'a sahip iç `add(..)` fonksiyonu referans alır
var plusOne = makeAdder(1);

// `plusTen`, dıştaki `makeAdder(..)`'ın `x` parametresi üzerinde closure'a sahip iç `add(..)` fonksiyonu referans alır
var plusTen = makeAdder(10);

plusOne(3);     // 4  <-- 1 + 3
plusOne(41);    // 42 <-- 1 + 41

plusTen(13);    // 23 <-- 10 + 13
```

Bu kodun nasıl çalıştığına dair daha fazla açıklama:

1. `makeAdder(1)`'i çağırdığımızda, iç `add(..)` fonksiyonu `x` değerini `1` olarak hatırlayan bir referansla geri alırız. Bu işlev referansına `plusOne(..)` adını veririz.
2. `makeAdder(10)`'u çağırdığımızda, iç `add(..)` fonksiyonu `x` değerini `10` olarak hatırlayan başka bir referansla geri alırız. Bu işlev referansına `plusTen(..)` adını veririz.
3. `plusOne(3)`'ü çağırdığımızda, `3` (iç `y`) ile `1` (hatırlanan `x`) ekler ve sonuç olarak `4` elde ederiz.
4. `plusTen(13)`'ü çağırdığımızda, `13` (iç `y`) ile `10` (hatırlanan `x`) ekler ve sonuç olarak `23` elde ederiz.

Başlangıçta bu size garip ve kafa karıştırıcı gelebilir, endişelenmeyin - öyle olabilir! Tam olarak anlamak için biraz pratiğe ihtiyacımız var.

Ancak bana güvenin, bir kez anladığınızda, bu programlamanın en güçlü ve kullanışlı tekniklerinden biridir. Closures üzerinde biraz düşünmek için emek harcamaya değer. Bir sonraki bölümde, closure üzerinde biraz daha pratiğe sahip olacağız.

#### Modules

JavaScript'te closure'un en yaygın kullanımı, modül desenidir (module pattern). Modüller, dış dünyadan gizlenen özel uygulama ayrıntılarını (değişkenler, işlevler) tanımlamanıza ve dışarıdan erişilebilir bir genel API oluşturmanıza olanak tanır.

Örnek olarak:

```js
function User(){
	var username, password;

	function doLogin(user,pw) {
		username = user;
		password = pw;

		// ve geri kalan login işlemleri buraya gelecek
	}

	var publicAPI = {
		login: doLogin
	};

	return publicAPI;
}

// bir `User` modül örneği oluşturma (module instance)
var fred = User();

fred.login( "fred", "12Battery34!" );
```

`User()` fonksiyonu, dış dünyadan erişilemeyen `username` ve `password` değişkenlerini ve iç `doLogin()` işlemini tutan dış bir kapsam olarak hizmet eder; bunlar `User` modülünün özel iç ayrıntılarıdır.

**Uyarı:** Burada `new User()`'ı bilerek çağırmıyoruz, bu, muhtemelen çoğu okuyucu için daha yaygın gibi görünse de. `User()` sadece bir fonksiyondur ve örneklenmesi gereken bir sınıf (class) değildir, bu nedenle normal bir şekilde çağrılır. `new` kullanmak uygun değil ve kaynakları gereksiz yere tüketebilir.

`User()`'ı çalıştırdığımızda, `User` modülünün bir *örneği (instance)* oluşturulur - tamamen yeni bir kapsam (scope) oluşturulur ve bu nedenle iç değişken/fonksiyonların tamamen yeni bir kopyası oluşturulur. Bu örneği `fred` değişkenine atarız. Eğer `User()`'ı tekrar çalıştırırsak, `fred` ile tamamen ayrı bir yeni örnek elde ederiz.

İç `doLogin()` işlevi, `username` ve `password` üzerinde bir closure'a sahiptir, bu da demek oluyor ki `User()` işlemi çalışmayı tamamladıktan sonra bile erişimini sürdürecektir.

`publicAPI`, üzerinde `login` adında bir özelliğe/metoda sahip bir nesnedir ve bu özellik, iç `doLogin()` işlevine bir referanstır. `User()` işleminde `publicAPI`'yi döndüğümüzde, onu `fred` olarak adlandırırız.

Bu noktada, dıştaki `User()` fonksiyonu çalışmayı tamamlamıştır. Normalde, `username` ve `password` gibi iç değişkenlerin işlemi sona erdiğini düşünürdünüz. Ancak burada, iç `login()` işlevinde onları canlı tutan bir closure olduğundan, bu değişkenler hala mevcuttur.

Bu nedenle `fred.login(..)`'ı çağırabiliriz - iç `doLogin(..)`'ı çağırmak gibi - ve hala `username` ve `password` iç değişkenlerine erişebiliriz.

Closure ve modül deseni (module pattern) hakkında bu kısa bakıştan sonra, hala bazı kavramların karmaşık gelebileceğini düşünüyorum. Bu sorun değil! Bu konuyu tam olarak anlamak için bazı çalışmalar yapmanız gerekebilir.

Buradan, bu konuyu daha ayrıntılı bir şekilde incelemek için bu serinin *Scope & Closures* başlığını okuyabilirsiniz.

## `this` Identifier (`this` tanımlayıcısı )

JavaScript'te çok yaygın olarak yanlış anlaşılan bir diğer kavram ise `this` tanımlayıcısıdır. Yine de bu konu hakkında serinin *this & Object Prototypes* başlığında birkaç bölüm bulunmaktadır, bu yüzden burada kavramı kısaca tanıtacağız.

Çoğu zaman `this`, "nesne yönelimli desenler" (object-oriented patterns) ile ilişkilendiriliyormuş gibi görünse de, JS'de `this` farklı bir mekanizmadır.

Bir fonksiyon içinde bir `this` referansı varsa, bu `this` referansı genellikle bir `nesneye` işaret eder. Ancak fonksiyonun nasıl çağrıldığına bağlı olarak bir `nesne`ye işaret eder.

`this`'in en yaygın yanlış anlamalarından biri, `this`'in fonksiyonun kendisine işaret ettiğini düşünmektir.

İşte hızlı bir örnek:

```js
function foo() {
	console.log( this.bar );
}

var bar = "global";

var obj1 = {
	bar: "obj1",
	foo: foo
};

var obj2 = {
	bar: "obj2"
};

// --------

foo();				// "global"
obj1.foo();			// "obj1"
foo.call( obj2 );		// "obj2"
new foo();			// undefined
```

`this`'in nasıl ayarlandığını belirleyen dört kural bulunur ve bu kurallar, bu örnekten sonraki dört satırda gösterilmiştir.

1. `foo()`, non-strict modda `this`'i genel nesneye ayarlar - strict mode'da, `this` `undefined` olur ve `bar` özelliğine erişmeye çalışırken bir hata alırsınız, bu nedenle `this.bar` için bulunan değer `"global"` olur.
2. `obj1.foo()`, `this`'i `obj1` nesnesine ayarlar.
3. `foo.call(obj2)`, `this`'i `obj2` nesnesine ayarlar.
4. `new foo()`, `this`'i tamamen yeni bir boş nesneye ayarlar.

Sonuç olarak, `this`'in neye işaret ettiğini anlamak için ilgili işlemin nasıl çağrıldığını incelemeniz gerekir. Bu, gösterilen dört yolun biri olacaktır ve bu da `this`'in ne olduğunu yanıtlayacaktır.

**Not:** `this` hakkında daha fazla bilgi için, bu serinin *this & Object Prototypes* başlığının 1. ve 2. bölümlerine bakabilirsiniz.

## Prototypes

JavaScript'deki prototype mekanizması oldukça karmaşıktır. Bu konuya burada sadece göz atacağız. Tüm ayrıntıları öğrenmek için bu serinin *this & Object Prototypes* başlığının 4-6. bölümlerini detaylıca incelemeniz gerekecektir.

Bir objectte bir özelliği başvurduğunuzda, eğer bu özellik mevcut değilse, JavaScript otomatik olarak bu objectin iç prototype'ın referansını kullanarak özelliği aramak için başka bir objecti bulacaktır. Bu, özelliğin eksik olduğu durumda neredeyse bir yedek olarak düşünülebilir.

Bir objectin iç prototip referans bağlantısı, obejectin oluşturulduğu zamanda gerçekleşir. Bu mekanizmayı en basit şekilde açıklamak için `Object.create(..)` adlı bir yerleşik yardımcı kullanabiliriz.

Örnek olarak:

```js
var foo = {
	a: 42
};

// `bar` değişkeni oluştur ve `foo` object'ini bu değişkene atama yap
var bar = Object.create( foo );

bar.b = "hello world";

bar.b;		// "hello world"
bar.a;		// 42 <-- `foo`'dan atanan değer
```

`foo` ve `bar` objectlerini ve ilişkilerini görselleştirmek işinizi kolaylaştırabilir:

<img src="fig6.png">

`bar` objectinde `a` özelliği aslında mevcut değil, ancak `bar`, `foo` ile prototype bağlantılı olduğu için JavaScript otomatik olarak `a` özelliğini `foo` nesnesinde arar ve burada bulur.

Bu bağlantı, dilin tuhaf bir özelliği gibi görünebilir. Bu özellik en yaygın olarak kullanılan - ve bence kötüye kullanılan - yol, "miras (inheritance)" ile bir "sınıf (class)" mekanizması oluşturmaya çalışmaktır.

Ancak prototype'ları daha doğal bir şekilde uygulamanın bir yolu, "davranış iletme (behavior delegation)" olarak adlandırılan bir desendir, burada bağlı object'lerin belirli davranışların bir kısmını birinden diğerine *iletebilecek* şekilde tasarlandığı bir desen olarak düşünülür.

**Not:** Prototype'lar ve davranış iletme hakkında daha fazla bilgi için, bu serinin *this & Object Prototypes* başlığının 4-6. bölümlerine başvurabilirsiniz.

## Old & New

Zaten kapsadığımız JS özelliklerinin bazıları ve kesinlikle bu serinin geri kalanındaki özelliklerin birçoğu, eski tarayıcılarda her zaman bulunmayabilir. Aslında, belgenin en yeni özelliklerinin bazıları henüz hiçbir stabil tarayıcıda uygulanmamış olabilir.

Peki, yeni özelliklerle ne yapmalısınız? Eski tarayıcıların yıllar veya onyıllar boyunca unutulmalarını beklemek mi gerekiyor?

Bu, birçok insanın bu durumu nasıl düşündüğüdür, ancak JS için sağlıklı bir yaklaşım değildir.

Daha yeni JavaScript özelliklerini eski tarayıcılara "getirmek" için kullanabileceğiniz iki temel teknik bulunur: polyfilling ve transpiling.

### Polyfilling

"Polyfill" kelimesi, daha yeni bir özelliğin tanımını alıp, davranışına eşdeğer olan ancak daha eski JS ortamlarında çalışabilen bir kod parçası üretmek için kullanılan uydurulmuş bir terimdir (Remy Sharp tarafından icat edilmiştir). Örneğin, ES6, `NaN` değerleri için doğru ve hata olmayan bir kontrol sağlamak için `Number.isNaN(..)` adlı bir yardımcı tanımlar ve orijinal `isNaN(..)` yardımcısını kullanım dışı bırakır. Ancak bu yardımcıyı polyfill etmek kolaydır, böylece kullanıcıların tarayıcılarının ES6 olup olmadığına bakılmaksızın kodunuzda kullanmaya başlayabilirsiniz.

Örnek olarak:

```js
if (!Number.isNaN) {
	Number.isNaN = function isNaN(x) {
		return x !== x;
	};
}
```

`if` ifadesi, polyfill tanımını zaten mevcut olan ES6 tarayıcılarında uygulamamızı engeller. Eğer zaten varsa, `Number.isNaN(..)`'yi tanımlarız.

**Not:** Burada yaptığımız kontrol, `NaN` değerleriyle ilgili bir ilginçliği kullanır, yani dilin genelinde kendine eşit olmayan tek değer `NaN`'dir. Bu nedenle `NaN` değeri, `x !== x` ifadesini `true` yapacak tek değerdir.

Tüm yeni özellikler tamamen polyfill edilemez. Bazen davranışın çoğu polyfill edilebilir, ancak hala küçük sapmalar olabilir. Kendiniz bir polyfill uygularken, mümkün olan en sıkı şekilde özelliklere uymak için gerçekten çok dikkatli olmalısınız.

Daha iyi olası, zaten güvenebileceğiniz, ES5-Shim (https://github.com/es-shims/es5-shim) ve ES6-Shim (https://github.com/es-shims/es6-shim) gibi bir dizi önceden test edilmiş polyfill kullanmaktır.

### Transpiling (transpile etme)

JavaScript'te eklenen yeni sözdizimini polyfill (uyarlama) yapmanın bir yolu yoktur. Yeni sözdizimi, eski JS motorunda tanınmayan/geçersiz olarak bir hata alır.

Bu yüzden daha iyi bir seçenek, daha yeni kodunuzu daha eski kod karşılıklarına dönüştüren bir araç kullanmaktır. Bu süreç genellikle "transpile etme" olarak adlandırılır, yani dönüştürme + derleme işlemi.

Temelde, kaynak kodunuz yeni sözdizimi biçiminde yazılır, ancak tarayıcıya dağıttığınız şey eski sözdizim biçiminde transpile edilen koddur. Genellikle transpiler'ı kod denetleyici veya kod küçültücü gibi oluşturma sürecinize eklersiniz.

Yeni bir sözdizini yazıp sadece onu eski bir koda çevirtmeye niçin uğraşmanız gerektiğini merak edebilirsiniz, neden doğrudan eski kodu yazmıyorsunuz?

Transpile etmeyi neden önemsemeniz gerektiğine dair birkaç önemli neden vardır:

* Dilin eklenen yeni sözdizimi, kodunuzu daha okunaklı ve sürdürülebilir hale getirmek için tasarlanmıştır. Eski karşılıklar genellikle çok daha karmaşıktır. Yeniden ve daha temiz sözdizisi yazmayı tercih etmelisiniz, sadece kendiniz için değil, geliştirme ekibinin diğer üyeleri için de.
* Sadece eski tarayıcılara transpile ederseniz, ancak en yeni tarayıcılara yeni sözdizim sunarsanız, yeni sözdizimi ile tarayıcı performans optimizasyonlarından yararlanabilirsiniz. Ayrıca tarayıcı üreticilerine uygulamalarını ve optimizasyonlarını test etmek için daha fazla gerçek dünya koduna sahip olma imkanı sağlar.
* Yeni sözdizimini daha erken kullanmak, onun gerçek dünyada daha sağlam bir şekilde test edilmesine izin verir, bu da JavaScript komitesine (TC39) daha erken geri bildirim sağlar. Sorunlar yeterince erken bulunursa, dil tasarım hataları kalıcı hale gelmeden değiştirilebilir/onarıabilir.

İşte transpile etmenin kısa bir örneği. ES6, "varsayılan parametre değerleri" adlı bir özellik ekler. Şu şekilde görünüyor:

```js
function foo(a = 2) {
	console.log( a );
}

foo();		// 2
foo( 42 );	// 42
```

Basit, değil mi? Ayrıca oldukça faydalı! Ancak bu, ES6 öncesindeki motorlarda geçersiz olan yeni bir sözdizimidir. Peki, bir transpiler bu kodu eski ortamlarda çalıştırmak için ne yapar?

```js
function foo() {
	var a = arguments[0] !== (void 0) ? arguments[0] : 2;
	console.log( a );
}
```

Gördüğünüz gibi, kod `arguments[0]` değerini `void 0` (yani `undefined`) ile karşılaştırır ve eğer öyleyse varsayılan değeri `2` olarak belirler; aksi halde geçirilen değeri atar.

Daha güzel sözdizimini eski tarayıcılarda kullanabilmenin yanı sıra, transpile edilen kodu incelediğinizde aslında beklenen davranışı daha net bir şekilde anlarsınız.

ES6 sürümünü inceleyerek, varsayılan bir değer parametresi için açıkça `undefined` dışındaki başka bir değerin belirtilmeyeceğini anlayamamış olabilirsiniz, ancak transpile edilen kod bu konuyu çok daha net bir şekilde açıklar.

Transpilerlar hakkında vurgulanması gereken son önemli detay, artık bunların JS geliştirme ekosistemi ve sürecinin standart bir parçası olarak düşünülmesi gerektiğidir. JS, daha öncekinden çok daha hızlı bir şekilde evrilmeye devam edecek, bu yüzden her birkaç ayda bir yeni sözdizimi ve yeni özellikler ekleyecektir.

Varsayılan olarak bir transpiler kullanırsanız, yeni sözdizimini kullanmaya her zaman ihtiyaç duyduğunuzda geçiş yapabilirsiniz, bu yüzden her zaman bugünün tarayıcılarının kullanımını sonlandırmasını beklemek zorunda kalmazsınız.

Kullanabileceğiniz birçok harika transpiler seçeneği bulunmaktadır. İşte bu yazının yazıldığı sırada bazı iyi seçenekler:

* Babel (https://babeljs.io) (önceden 6to5 olarak bilinirdi): ES6+'yı ES5'e transpile eder.
* Traceur (https://github.com/google/traceur-compiler): ES6, ES7 ve ötesini ES5'e transpile eder.

## Non-JavaScript

Şimdiye kadar, ele aldığımız konular sadece JavaScript dilindeki konulardı. Gerçeklik şu ki, çoğu JS kodu tarayıcılar gibi ortamlarda çalışması ve etkileşimde bulunması için yazılır. Kodunuzda yazdığınız şeylerin büyük bir kısmı, katı olarak düşünüldüğünde doğrudan JavaScript tarafından kontrol edilmeyen şeylerdir. Bu belki biraz garip gelebilir.

Karşılaşacağınız en yaygın olmayan JavaScript, DOM API'si gibi JavaScript'ten farklı olan şeylerdir. Örneğin:

```js
var el = document.getElementById( "foo" );
```

`document` değişkeni, kodunuz bir tarayıcıda çalıştığında global bir değişken olarak mevcuttur. Bu, JS motoru tarafından sağlanmaz ve JavaScript belgesi tarafından özellikle kontrol edilmez. Normal bir JS `object` gibi görünen bir şeye benzer bir form alır, ancak tam olarak o değildir. Bu özel bir `object`tir ve genellikle bir "ana obje" olarak adlandırılır.

Ayrıca, `document` üzerindeki `getElementById(..)` yöntemi normal bir JS işlevine benzese de, aslında tarayıcınızın DOM'dan sağladığı yerleşik bir yönteme aittir. Bazı (yeni nesil) tarayıcılarda, bu katman da JS'de olabilir, ancak geleneksel olarak DOM ve davranışları daha çok C/C++ gibi bir şeyde uygulanır.

Başka bir örnek giriş/çıkış (I/O) ile ilgilidir.

Herkesin sevdiği `alert(..)`, kullanıcının tarayıcı penceresinde bir ileti kutusu görüntüler. `alert(..)`, JS programınıza tarayıcı tarafından sağlanır, JS motoru tarafından değil. Yaptığınız çağrı, iletiyi tarayıcı iç yapısına gönderir ve ileti kutusunu çizip görüntülemeyi yönetir.

Aynı şey `console.log(..)` için de geçerlidir; tarayıcınız bu mekanizmaları sağlar ve bunları geliştirici araçlarına bağlar.

Bu kitap ve bu seri, JavaScript dili üzerine odaklanmaktadır. Bu yüzden bu tür JavaScript ile ilgili olmayan mekanizmalarının büyük bir kapsama alanı yok. Bununla birlikte, bu mekanizmalar hakkında bilgi sahibi olmanız gerekmektedir, çünkü yazdığınız her JS programında karşınıza çıkacaktır!

## Gözden Geçirme

JavaScript programlama dilinin özelliklerini öğrenmenin ilk adımı, değerler (values), tipler (types), fonksiyon kapanışları, `this` ve prototipler gibi temel mekanizmalarını temel bir anlayışla kavramaktır.

Tabii ki, bu konuların her biri burada gördüğünüzden çok daha fazla kapsama alanına sahiptir, ancak bu konulara ayrılmış bölümler ve kitaplar, bu serinin geri kalanında sizi bekliyor. Bu bölümdeki kavramlar ve kod örnekleri hakkında oldukça rahat hissettikten sonra, geri kalan seriyi keşfetmek ve dili derinlemesine tanımak için sizi bekliyor olacak.

Bu kitabın son bölümü, serinin diğer başlıklarını ve zaten keşfettiğimiz konuların dışında kapsadığı diğer kavramları kısaca özetleyecektir.
