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

This may sound like a strange concept at first, so take a moment to ponder it. Not only can you pass a value (argument) *to* a function, but *a function itself can be a value* that's assigned to variables, or passed to or returned from other functions.

As such, a function value should be thought of as an expression, much like any other value or expression.

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

### Immediately Invoked Function Expressions (IIFEs)

In the previous snippet, neither of the function expressions are executed -- we could if we had included `foo()` or `x()`, for instance.

There's another way to execute a function expression, which is typically referred to as an *immediately invoked function expression* (IIFE):

```js
(function IIFE(){
	console.log( "Hello!" );
})();
// "Hello!"
```

The outer `( .. )` that surrounds the `(function IIFE(){ .. })` function expression is just a nuance of JS grammar needed to prevent it from being treated as a normal function declaration.

The final `()` on the end of the expression -- the `})();` line -- is what actually executes the function expression referenced immediately before it.

That may seem strange, but it's not as foreign as first glance. Consider the similarities between `foo` and `IIFE` here:

```js
function foo() { .. }

// `foo` function reference expression,
// then `()` executes it
foo();

// `IIFE` function expression,
// then `()` executes it
(function IIFE(){ .. })();
```

As you can see, listing the `(function IIFE(){ .. })` before its executing `()` is essentially the same as including `foo` before its executing `()`; in both cases, the function reference is executed with `()` immediately after it.

Because an IIFE is just a function, and functions create variable *scope*, using an IIFE in this fashion is often used to declare variables that won't affect the surrounding code outside the IIFE:

```js
var a = 42;

(function IIFE(){
	var a = 10;
	console.log( a );	// 10
})();

console.log( a );		// 42
```

IIFEs can also have return values:

```js
var x = (function IIFE(){
	return 42;
})();

x;	// 42
```

The `42` value gets `return`ed from the `IIFE`-named function being executed, and is then assigned to `x`.

### Closure

*Closure* is one of the most important, and often least understood, concepts in JavaScript. I won't cover it in deep detail here, and instead refer you to the *Scope & Closures* title of this series. But I want to say a few things about it so you understand the general concept. It will be one of the most important techniques in your JS skillset.

You can think of closure as a way to "remember" and continue to access a function's scope (its variables) even once the function has finished running.

Consider:

```js
function makeAdder(x) {
	// parameter `x` is an inner variable

	// inner function `add()` uses `x`, so
	// it has a "closure" over it
	function add(y) {
		return y + x;
	};

	return add;
}
```

The reference to the inner `add(..)` function that gets returned with each call to the outer `makeAdder(..)` is able to remember whatever `x` value was passed in to `makeAdder(..)`. Now, let's use `makeAdder(..)`:

```js
// `plusOne` gets a reference to the inner `add(..)`
// function with closure over the `x` parameter of
// the outer `makeAdder(..)`
var plusOne = makeAdder( 1 );

// `plusTen` gets a reference to the inner `add(..)`
// function with closure over the `x` parameter of
// the outer `makeAdder(..)`
var plusTen = makeAdder( 10 );

plusOne( 3 );		// 4  <-- 1 + 3
plusOne( 41 );		// 42 <-- 1 + 41

plusTen( 13 );		// 23 <-- 10 + 13
```

More on how this code works:

1. When we call `makeAdder(1)`, we get back a reference to its inner `add(..)` that remembers `x` as `1`. We call this function reference `plusOne(..)`.
2. When we call `makeAdder(10)`, we get back another reference to its inner `add(..)` that remembers `x` as `10`. We call this function reference `plusTen(..)`.
3. When we call `plusOne(3)`, it adds `3` (its inner `y`) to the `1` (remembered by `x`), and we get `4` as the result.
4. When we call `plusTen(13)`, it adds `13` (its inner `y`) to the `10` (remembered by `x`), and we get `23` as the result.

Don't worry if this seems strange and confusing at first -- it can be! It'll take lots of practice to understand it fully.

But trust me, once you do, it's one of the most powerful and useful techniques in all of programming. It's definitely worth the effort to let your brain simmer on closures for a bit. In the next section, we'll get a little more practice with closure.

#### Modules

The most common usage of closure in JavaScript is the module pattern. Modules let you define private implementation details (variables, functions) that are hidden from the outside world, as well as a public API that *is* accessible from the outside.

Consider:

```js
function User(){
	var username, password;

	function doLogin(user,pw) {
		username = user;
		password = pw;

		// do the rest of the login work
	}

	var publicAPI = {
		login: doLogin
	};

	return publicAPI;
}

// create a `User` module instance
var fred = User();

fred.login( "fred", "12Battery34!" );
```

The `User()` function serves as an outer scope that holds the variables `username` and `password`, as well as the inner `doLogin()` function; these are all private inner details of this `User` module that cannot be accessed from the outside world.

**Warning:** We are not calling `new User()` here, on purpose, despite the fact that probably seems more common to most readers. `User()` is just a function, not a class to be instantiated, so it's just called normally. Using `new` would be inappropriate and actually waste resources.

Executing `User()` creates an *instance* of the `User` module -- a whole new scope is created, and thus a whole new copy of each of these inner variables/functions. We assign this instance to `fred`. If we run `User()` again, we'd get a new instance entirely separate from `fred`.

The inner `doLogin()` function has a closure over `username` and `password`, meaning it will retain its access to them even after the `User()` function finishes running.

`publicAPI` is an object with one property/method on it, `login`, which is a reference to the inner `doLogin()` function. When we return `publicAPI` from `User()`, it becomes the instance we call `fred`.

At this point, the outer `User()` function has finished executing. Normally, you'd think the inner variables like `username` and `password` have gone away. But here they have not, because there's a closure in the `login()` function keeping them alive.

That's why we can call `fred.login(..)` -- the same as calling the inner `doLogin(..)` -- and it can still access `username` and `password` inner variables.

There's a good chance that with just this brief glimpse at closure and the module pattern, some of it is still a bit confusing. That's OK! It takes some work to wrap your brain around it.

From here, go read the *Scope & Closures* title of this series for a much more in-depth exploration.

## `this` Identifier

Another very commonly misunderstood concept in JavaScript is the `this` identifier. Again, there's a couple of chapters on it in the *this & Object Prototypes* title of this series, so here we'll just briefly introduce the concept.

While it may often seem that `this` is related to "object-oriented patterns," in JS `this` is a different mechanism.

If a function has a `this` reference inside it, that `this` reference usually points to an `object`. But which `object` it points to depends on how the function was called.

It's important to realize that `this` *does not* refer to the function itself, as is the most common misconception.

Here's a quick illustration:

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

There are four rules for how `this` gets set, and they're shown in those last four lines of that snippet.

1. `foo()` ends up setting `this` to the global object in non-strict mode -- in strict mode, `this` would be `undefined` and you'd get an error in accessing the `bar` property -- so `"global"` is the value found for `this.bar`.
2. `obj1.foo()` sets `this` to the `obj1` object.
3. `foo.call(obj2)` sets `this` to the `obj2` object.
4. `new foo()` sets `this` to a brand new empty object.

Bottom line: to understand what `this` points to, you have to examine how the function in question was called. It will be one of those four ways just shown, and that will then answer what `this` is.

**Note:** For more information about `this`, see Chapters 1 and 2 of the *this & Object Prototypes* title of this series.

## Prototypes

The prototype mechanism in JavaScript is quite complicated. We will only glance at it here. You will want to spend plenty of time reviewing Chapters 4-6 of the *this & Object Prototypes* title of this series for all the details.

When you reference a property on an object, if that property doesn't exist, JavaScript will automatically use that object's internal prototype reference to find another object to look for the property on. You could think of this almost as a fallback if the property is missing.

The internal prototype reference linkage from one object to its fallback happens at the time the object is created. The simplest way to illustrate it is with a built-in utility called `Object.create(..)`.

Consider:

```js
var foo = {
	a: 42
};

// create `bar` and link it to `foo`
var bar = Object.create( foo );

bar.b = "hello world";

bar.b;		// "hello world"
bar.a;		// 42 <-- delegated to `foo`
```

It may help to visualize the `foo` and `bar` objects and their relationship:

<img src="fig6.png">

The `a` property doesn't actually exist on the `bar` object, but because `bar` is prototype-linked to `foo`, JavaScript automatically falls back to looking for `a` on the `foo` object, where it's found.

This linkage may seem like a strange feature of the language. The most common way this feature is used -- and I would argue, abused -- is to try to emulate/fake a "class" mechanism with "inheritance."

But a more natural way of applying prototypes is a pattern called "behavior delegation," where you intentionally design your linked objects to be able to *delegate* from one to the other for parts of the needed behavior.

**Note:** For more information about prototypes and behavior delegation, see Chapters 4-6 of the *this & Object Prototypes* title of this series.

## Old & New

Some of the JS features we've already covered, and certainly many of the features covered in the rest of this series, are newer additions and will not necessarily be available in older browsers. In fact, some of the newest features in the specification aren't even implemented in any stable browsers yet.

So, what do you do with the new stuff? Do you just have to wait around for years or decades for all the old browsers to fade into obscurity?

That's how many people think about the situation, but it's really not a healthy approach to JS.

There are two main techniques you can use to "bring" the newer JavaScript stuff to the older browsers: polyfilling and transpiling.

### Polyfilling

The word "polyfill" is an invented term (by Remy Sharp) (https://remysharp.com/2010/10/08/what-is-a-polyfill) used to refer to taking the definition of a newer feature and producing a piece of code that's equivalent to the behavior, but is able to run in older JS environments.

For example, ES6 defines a utility called `Number.isNaN(..)` to provide an accurate non-buggy check for `NaN` values, deprecating the original `isNaN(..)` utility. But it's easy to polyfill that utility so that you can start using it in your code regardless of whether the end user is in an ES6 browser or not.

Consider:

```js
if (!Number.isNaN) {
	Number.isNaN = function isNaN(x) {
		return x !== x;
	};
}
```

The `if` statement guards against applying the polyfill definition in ES6 browsers where it will already exist. If it's not already present, we define `Number.isNaN(..)`.

**Note:** The check we do here takes advantage of a quirk with `NaN` values, which is that they're the only value in the whole language that is not equal to itself. So the `NaN` value is the only one that would make `x !== x` be `true`.

Not all new features are fully polyfillable. Sometimes most of the behavior can be polyfilled, but there are still small deviations. You should be really, really careful in implementing a polyfill yourself, to make sure you are adhering to the specification as strictly as possible.

Or better yet, use an already vetted set of polyfills that you can trust, such as those provided by ES5-Shim (https://github.com/es-shims/es5-shim) and ES6-Shim (https://github.com/es-shims/es6-shim).

### Transpiling

There's no way to polyfill new syntax that has been added to the language. The new syntax would throw an error in the old JS engine as unrecognized/invalid.

So the better option is to use a tool that converts your newer code into older code equivalents. This process is commonly called "transpiling," a term for transforming + compiling.

Essentially, your source code is authored in the new syntax form, but what you deploy to the browser is the transpiled code in old syntax form. You typically insert the transpiler into your build process, similar to your code linter or your minifier.

You might wonder why you'd go to the trouble to write new syntax only to have it transpiled away to older code -- why not just write the older code directly?

There are several important reasons you should care about transpiling:

* The new syntax added to the language is designed to make your code more readable and maintainable. The older equivalents are often much more convoluted. You should prefer writing newer and cleaner syntax, not only for yourself but for all other members of the development team.
* If you transpile only for older browsers, but serve the new syntax to the newest browsers, you get to take advantage of browser performance optimizations with the new syntax. This also lets browser makers have more real-world code to test their implementations and optimizations on.
* Using the new syntax earlier allows it to be tested more robustly in the real world, which provides earlier feedback to the JavaScript committee (TC39). If issues are found early enough, they can be changed/fixed before those language design mistakes become permanent.

Here's a quick example of transpiling. ES6 adds a feature called "default parameter values." It looks like this:

```js
function foo(a = 2) {
	console.log( a );
}

foo();		// 2
foo( 42 );	// 42
```

Simple, right? Helpful, too! But it's new syntax that's invalid in pre-ES6 engines. So what will a transpiler do with that code to make it run in older environments?

```js
function foo() {
	var a = arguments[0] !== (void 0) ? arguments[0] : 2;
	console.log( a );
}
```

As you can see, it checks to see if the `arguments[0]` value is `void 0` (aka `undefined`), and if so provides the `2` default value; otherwise, it assigns whatever was passed.

In addition to being able to now use the nicer syntax even in older browsers, looking at the transpiled code actually explains the intended behavior more clearly.

You may not have realized just from looking at the ES6 version that `undefined` is the only value that can't get explicitly passed in for a default-value parameter, but the transpiled code makes that much more clear.

The last important detail to emphasize about transpilers is that they should now be thought of as a standard part of the JS development ecosystem and process. JS is going to continue to evolve, much more quickly than before, so every few months new syntax and new features will be added.

If you use a transpiler by default, you'll always be able to make that switch to newer syntax whenever you find it useful, rather than always waiting for years for today's browsers to phase out.

There are quite a few great transpilers for you to choose from. Here are some good options at the time of this writing:

* Babel (https://babeljs.io) (formerly 6to5): Transpiles ES6+ into ES5
* Traceur (https://github.com/google/traceur-compiler): Transpiles ES6, ES7, and beyond into ES5

## Non-JavaScript

So far, the only things we've covered are in the JS language itself. The reality is that most JS is written to run in and interact with environments like browsers. A good chunk of the stuff that you write in your code is, strictly speaking, not directly controlled by JavaScript. That probably sounds a little strange.

The most common non-JavaScript JavaScript you'll encounter is the DOM API. For example:

```js
var el = document.getElementById( "foo" );
```

The `document` variable exists as a global variable when your code is running in a browser. It's not provided by the JS engine, nor is it particularly controlled by the JavaScript specification. It takes the form of something that looks an awful lot like a normal JS `object`, but it's not really exactly that. It's a special `object,` often called a "host object."

Moreover, the `getElementById(..)` method on `document` looks like a normal JS function, but it's just a thinly exposed interface to a built-in method provided by the DOM from your browser. In some (newer-generation) browsers, this layer may also be in JS, but traditionally the DOM and its behavior is implemented in something more like C/C++.

Another example is with input/output (I/O).

Everyone's favorite `alert(..)` pops up a message box in the user's browser window. `alert(..)` is provided to your JS program by the browser, not by the JS engine itself. The call you make sends the message to the browser internals and it handles drawing and displaying the message box.

The same goes with `console.log(..)`; your browser provides such mechanisms and hooks them up to the developer tools.

This book, and this whole series, focuses on JavaScript the language. That's why you don't see any substantial coverage of these non-JavaScript JavaScript mechanisms. Nevertheless, you need to be aware of them, as they'll be in every JS program you write!

## Review

The first step to learning JavaScript's flavor of programming is to get a basic understanding of its core mechanisms like values, types, function closures, `this`, and prototypes.

Of course, each of these topics deserves much greater coverage than you've seen here, but that's why they have chapters and books dedicated to them throughout the rest of this series. After you feel pretty comfortable with the concepts and code samples in this chapter, the rest of the series awaits you to really dig in and get to know the language deeply.

The final chapter of this book will briefly summarize each of the other titles in the series and the other concepts they cover besides what we've already explored.
