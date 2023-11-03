# You Don't Know JS: Up & Going
# Bölüm 1: Programlamaya Giriş

*You Dont know JS* (*YDKJS*) serisine hoş geldiniz.

*Up & Going* programlamanın bazı temel kavramlarına giriş niteliğindedir - elbette özellikle JavaScript'e (genellikle JS olarak kısaltılır) yöneliyoruz - ve bu serideki diğer başlıklara nasıl yaklaşılacağı ve anlaşılacağı. Özellikle programlamaya ve/veya JavaScript'e yeni başlıyorsanız, bu kitap *başlamak* için neye ihtiyacınız olduğunu kısaca keşfedecektir.

Bu kitap, programlamanın temel ilkelerini çok yüksek düzeyde açıklayarak başlıyor. Çoğunlukla *YDKJS*'ye önceden çok az programlama deneyimiyle veya hiç programlama deneyimi olmadan başlıyorsanız ve programlamayı JavaScript merceğinden anlama yolunda başlamanıza yardımcı olacak bu kitaplara bakıyorsanız amaçlanır.

Bölüm 1'e, hakkında daha fazla bilgi edinmek isteyeceğiniz ve *programlamaya* girmek için pratik yapmak isteyeceğiniz şeylere hızlı bir genel bakış olarak yaklaşılmalıdır. Ayrıca, bu konuları daha derinlemesine incelemenize yardımcı olabilecek başka pek çok harika programlamaya giriş kaynağı da mevcut ve bu bölüme ek olarak onlardan da bir şeyler öğrenmenizi tavsiye ediyorum.

Genel programlama temelleri konusunda kendinizi rahat hissettiğinizde, Bölüm 2, JavaScript'in programlama tarzına aşina olmanıza yardımcı olacaktır. 2. Bölümde JavaScript'in neyle ilgili olduğu anlatılıyor ancak yine de kapsamlı bir rehber değil -- geri kalan *YDKJS* kitaplarının amacı da bu!

JavaScript konusunda zaten yeterince bilginiz varsa, öncelikle *YDKJS*'den neler beklenebileceğine dair kısa bir bakış için Bölüm 3'e göz atın, ardından hemen başlayın!

## Kodlama

Hadi baştan başlayalım.

Genellikle *kaynak kodu* veya yalnızca *kod* olarak anılan program, bilgisayara hangi görevleri gerçekleştireceğini söyleyen bir dizi özel talimattır. Kod genellikle bir metin dosyasına kaydedilir, ancak JavaScript ile kodu doğrudan bir tarayıcıdaki geliştirici konsoluna da yazabilirsiniz; buna kısaca değineceğiz.

Geçerli format ve talimat kombinasyonlarına ilişkin kurallara *bilgisayar dili* adı verilir ve bazen *sözdizimi* olarak da anılır; tıpkı İngilizce'nin size kelimeleri nasıl yazacağınızı ve kelimeleri ve noktalama işaretlerini kullanarak nasıl geçerli cümleler oluşturacağınızı söylemesi gibi.

### İfadeler (Statements)

Bir bilgisayar dilinde, belirli bir görevi yerine getiren bir grup kelime, sayı ve operatör bir *ifadedir*. JavaScript'te bir ifade aşağıdaki gibi görünebilir:

```js
a = b * 2;
```

`a` ve `b` karakterleri *değişkenler* olarak adlandırılır ("Değişkenler"e bakın), bunlar herhangi bir öğenizi saklayabileceğiniz basit kutular gibidir. Programlarda değişkenler, değerleri ('42' sayısı gibi) tutar. program tarafından kullanılacaktır. Bunları değerlerin sembolik yer tutucuları olarak düşünün.

Bunun tersine, "2" yalnızca bir değerdir ve *gerçek değer* olarak adlandırılır, çünkü bir değişkende saklanmadan tek başına durur.

`=` ve `*` karakterleri *operatörlerdir* (bkz. "Operatörler") - atama ve matematiksel çarpma gibi değerler ve değişkenlerle eylemler gerçekleştirirler.

JavaScript'teki çoğu ifadenin sonunda noktalı virgül (`;`) bulunur.

'a = b * 2;' ifadesi, bilgisayara kabaca, 'b' değişkeninde saklanan geçerli değeri almasını, bu değeri '2' ile çarpmasını ve ardından sonucu 'a' adını verdiğimiz başka bir değişkene geri saklamasını söyler.

Programlar, programınızın amacını gerçekleştirmek için gereken tüm adımları birlikte açıklayan bu tür birçok ifadenin yalnızca bir derlemesidir.

### İfadeler (Expressions)

İfadeler bir veya daha fazla *ifadeden* oluşur. İfade, bir değişkene veya değere veya operatörlerle birleştirilmiş değişken(ler) ve değer(ler) kümesine yapılan herhangi bir başvurudur.

örnek olarak:

```js
a = b * 2;
```

Bu ifadenin içinde dört ifade bulunmaktadır:

* `2` bir *gerçek değer ifadesidir*
* `b` bir *değişken ifadesidir*, yani mevcut değerini almak anlamına gelir
* `b * 2` bir *aritmetik ifadedir*, yani çarpma işlemi yapmak anlamına gelir
* `a = b * 2` bir *atama ifadesidir*; bu, `b * 2` ifadesinin sonucunu `a` değişkenine atamak anlamına gelir (daha sonra atamalarla ilgili daha fazla bilgi verilecektir)

Tek başına duran genel bir ifadeye aynı zamanda *ifade ifadesi* de denir, örneğin:

```js
b * 2;
```

İfade ifadesinin bu çeşidi çok yaygın veya kullanışlı değildir, çünkü genellikle programın çalışması üzerinde herhangi bir etkisi olmaz - 'b' değerini alır ve onu '2' ile çarpar, ancak daha sonra' Bu sonuçla hiçbir şey yapmayın.

Daha yaygın bir ifade ifadesi *çağrı ifadesi* ifadesidir (bkz. "İşlevler"), çünkü ifadenin tamamı işlev çağrısı ifadesinin kendisidir:

```js
alert( a );
```

### Bir Programın Yürütülmesi

Bu programlama ifadeleri koleksiyonları bilgisayara ne yapması gerektiğini nasıl söylüyor? Programın *yürütülmesi* gerekir; buna aynı zamanda *programın çalıştırılması* da denir.

'a = b * 2' gibi ifadeler geliştiricilere okuma ve yazma sırasında yardımcı olur ancak aslında bilgisayarın doğrudan anlayabileceği bir biçimde değildir. Bu nedenle, bilgisayardaki özel bir yardımcı program (bir *yorumlayıcı* veya *derleyici*) yazdığınız kodu bilgisayarın anlayabileceği komutlara çevirmek için kullanılır.

Bazı bilgisayar dilleri için, komutların bu çevirisi genellikle program her çalıştırıldığında yukarıdan aşağıya, satır satır yapılır; buna genellikle kodun *yorumlanması* denir.

Diğer diller için çeviri, kodun *derlenmesi* adı verilen önceden yapılır; dolayısıyla program daha sonra *çalıştığında*, çalışan şey aslında önceden derlenmiş, kullanıma hazır bilgisayar talimatlarıdır.

JavaScript kaynak kodunuz her çalıştırıldığında işlendiğinden, genellikle JavaScript'in *yorumlandığı* iddia edilir. Ancak bu tamamen doğru değil. JavaScript motoru aslında programı anında *derler* ve derlenen kodu hemen çalıştırır.

**Not:** JavaScript derlemesi hakkında daha fazla bilgi için bu serinin *Kapsam ve Kapanışlar* başlığının ilk iki bölümüne bakın.

## Kendiniz De Deneyin

Bu bölümde her programlama konseptini tamamı JavaScript ile yazılmış (tabii ki!) basit kod parçacıklarıyla tanıtacağız.

Ne kadar vurgulansa azdır: Bu bölümü incelerken - ki bunun üzerinden birkaç kez geçmek için zaman harcamanız gerekebilir - kodu kendiniz yazarak bu kavramların her birini pratik etmelisiniz. Bunu yapmanın en kolay yolu geliştirici araçları konsolunu en yakın tarayıcınızda (Firefox, Chrome, IE vb.) açmaktır.

**İpucu:** Genellikle geliştirici konsolunu klavye kısayoluyla veya bir menü öğesinden başlatabilirsiniz. Konsolu favori tarayıcınızda başlatma ve kullanma hakkında daha ayrıntılı bilgi için bkz. "Geliştirici Araçları Konsolunda Uzmanlaşma" (http://blog.teamtreehouse.com/mastering-developer-tools-console). Konsola aynı anda birden fazla satır yazmak için bir sonraki yeni satıra geçmek üzere `<shift> + <enter>` tuşlarını kullanın. Tek başına "<enter>" tuşuna bastığınızda, konsol az önce yazdığınız her şeyi çalıştıracaktır.

Konsolda kod çalıştırma sürecini tanıyalım. Öncelikle tarayıcınızda boş bir sekme açmanızı öneririm. Bunu adres çubuğuna "about:blank" yazarak yapmayı tercih ediyorum. Daha sonra az önce de belirttiğimiz gibi geliştirici konsolunuzun açık olduğundan emin olun.

Şimdi bu kodu yazın ve nasıl çalıştığını görün:

```js
a = 21;

b = a * 2;

console.log( b );
```

Önceki kodu Chrome'daki konsola yazmak aşağıdakine benzer bir şey üretmelidir:

<img src="fig1.png" width="500">

Haydi, dene. Programlamayı öğrenmenin en iyi yolu kodlamaya başlamaktır!

### Çıktı (Output)

Önceki kod parçacığında `console.log(..)` kullanmıştık. Kısaca bu kod satırının neyle ilgili olduğuna bakalım.

Tahmin etmiş olabilirsiniz, ancak geliştirici konsolunda metni (diğer adıyla kullanıcıya *çıktı*) bu şekilde yazdırırız. Bu ifadenin açıklamamız gereken iki özelliği var.

İlk olarak, 'log(b)' kısmına işlev çağrısı denir (bkz. "İşlevler"). Olan şu ki, biz 'b' değişkenini bu fonksiyona veriyoruz, bu da ondan 'b' değerini alıp konsola yazdırmasını istiyor.

İkincisi, 'console.' kısmı 'log(..)' fonksiyonunun bulunduğu bir nesne referansıdır. Nesneleri ve onların özelliklerini Bölüm 2'de daha ayrıntılı olarak ele alacağız.

Çıktı oluşturmanın görebileceğiniz başka bir yolu da 'alert(..)' ifadesini çalıştırmaktır. Örneğin:

```js
alert( b );
```

Bunu çalıştırırsanız, çıktıyı konsola yazdırmak yerine, 'b' değişkeninin içeriğini içeren açılır bir "Tamam" kutusu gösterdiğini fark edeceksiniz. Ancak, "console.log(..)" kullanmak genellikle kodlamayı öğrenmenizi ve programlarınızı konsolda çalıştırmayı "alert(..)" kullanmaktan daha kolay hale getirir, çünkü tarayıcıyı kesintiye uğratmadan aynı anda birçok değerin çıktısını alabilirsiniz arayüz.

Bu kitapta çıktı olarak `console.log(..)` kullanacağız.

### Girdi (Input)

Çıktıyı tartışırken, *giriş* (yani kullanıcıdan bilgi almak) konusunu da merak edebilirsiniz.

Bunun en yaygın yolu, HTML sayfasının kullanıcıya yazı yazabileceği form öğelerini (metin kutuları gibi) göstermesi ve ardından bu değerleri programınızın değişkenlerine okumak için JS'yi kullanmasıdır.

Ancak bu kitap boyunca yapacaklarınız gibi basit öğrenme ve gösterme amaçları için girdi almanın daha kolay bir yolu var. 'Prompt(..)' işlevini kullanın:

```js
age = prompt( "Please tell me your age:" );

console.log( age );
```

Tahmin edebileceğiniz gibi, 'prompt(..)''a ilettiğiniz mesaj -- bu durumda, ''Lütfen bana yaşınızı söyleyin:'' -- açılır pencerede yazdırılır.

Bu, aşağıdakine benzer görünmelidir:

<img src="fig2.png" width="500">

"Tamam"ı tıklayarak giriş metnini gönderdiğinizde, yazdığınız değerin "yaş" değişkeninde saklandığını göreceksiniz, ardından bunu "console.log(..)" ile *çıkartıyoruz*:

<img src="fig3.png" width="500">

Temel programlama kavramlarını öğrenirken işleri basit tutmak için bu kitaptaki örnekler girdi gerektirmeyecektir. Ancak artık “prompt(..)”ın nasıl kullanılacağını gördüğünüze göre, kendinize meydan okumak istiyorsanız örnekleri incelerken girdileri kullanmayı deneyebilirsiniz.

## Operatörler (Operators)

Operatörler, değişkenler ve değerler üzerinde eylemleri nasıl gerçekleştirdiğimizdir. Zaten iki JavaScript operatörü gördük, `=` ve `*`.

'*' operatörü matematiksel çarpma işlemini gerçekleştirir. Yeterince basit, değil mi?

`=` eşittir operatörü *atama* için kullanılır - önce `=`nin *sağ tarafındaki* (kaynak değeri) değeri hesaplarız ve sonra onu *sol tarafta belirttiğimiz değişkene koyarız -el tarafı* (hedef değişken).

**Uyarı:** Bu, atamayı belirtmek için garip bir ters sıra gibi görünebilir. Bazıları 'a = 42' yerine, kaynak değeri solda ve hedef değişkeni sağda olacak şekilde, '42 -> a' gibi sırayı değiştirmeyi tercih edebilir (bu geçerli bir JavaScript değil!). Ne yazık ki, 'a = 42' sıralı formu ve benzer varyasyonları modern programlama dillerinde oldukça yaygındır. Eğer doğal görünmüyorsa, alışmak için bu sıralamayı zihninizde prova etmek için biraz zaman ayırın.

Dikkate almak:

```js
a = 2;
b = a + 1;
```

Burada `a` değişkenine `2` değerini atadık. Daha sonra, "a" değişkeninin değerini (hala "2") alıyoruz, buna "1" ekleyerek "3" değerini elde ediyoruz ve ardından bu değeri "b" değişkeninde saklıyoruz.

Teknik olarak bir operatör olmasa da, her programda `var` anahtar kelimesine ihtiyacınız olacak, çünkü bu anahtar kelimeyi *bildirmenin* (diğer adıyla *oluşturma*) *değişkenleri*iables (bkz. "Değişkenler").

Değişkeni kullanmadan önce daima ismine göre bildirmelisiniz. Ancak her *kapsam* için bir değişkeni yalnızca bir kez bildirmeniz gerekir (bkz. "Kapsam"); bundan sonra gerektiği kadar kullanılabilir. Örneğin:

```js
var a = 20;

a = a + 1;
a = a * 2;

console.log( a );	// 42
```

JavaScript'te en yaygın kullanılan operatörlerden bazıları şunlardır:

* Atama: `=`, `a = 2`de olduğu gibi.
* Matematik: `+` (toplama), `-` (çıkarma), `*` (çarpma) ve `/` (bölme), `a * 3`te olduğu gibi.
* Bileşik Atama: `+=`, `-=`, `*=` ve `/=`, `a += 2`de olduğu gibi bir matematik işlemini atamayla birleştiren bileşik operatörlerdir (`a = a ile aynı) + 2`).
* Artış/Azalış: `++` (artırma), `--' (azalma), 'a++'da olduğu gibi ('a = a + 1'e benzer).
* Nesne Özelliği Erişimi: `.`, `console.log()`daki gibi.

   Nesneler, özellikler adı verilen belirli adlandırılmış konumlarda diğer değerleri tutan değerlerdir. 'obj.a', 'a' adındaki bir özelliğe sahip, 'obj' adı verilen bir nesne değeri anlamına gelir. Özelliklere alternatif olarak `obj["a"]` olarak erişilebilir. 2. Bölüme bakın.
* Eşitlik: `==` (gevşek eşit olmayanlar), `===` (katı eşit olanlar), `!=` (gevşek eşit olmayanlar), `!==` (katı eşit olmayanlar), `'da olduğu gibi a == b`.

   Bkz. "Değerler ve Türler" ve Bölüm 2.
* Karşılaştırma: `<` (küçüktür), `>` (büyüktür), `<=` (küçüktür veya gevşek eşittir), `>=` (büyüktür veya gevşek eşittir), `a <'de olduğu gibi = b`.

   Bkz. "Değerler ve Türler" ve Bölüm 2.
* Mantıksal: `&&` (ve), `||` (veya), `a || `a` *veya* `b`yi seçen b`.

   Bu operatörler, örneğin "a" *veya* "b"nin doğru olması gibi bileşik koşulları ifade etmek için kullanılır ("Koşullular"a bakın).

**Not:** Daha fazla ayrıntı ve burada belirtilmeyen operatörlerin kapsamı için Mozilla Geliştirici Ağı'nın (MDN) "İfadeler ve Operatörler" (https://developer.mozilla.org/en-US/docs) sayfasına bakın. /Web/JavaScript/Guide/Expressions_and_Operators).

## Değerler ve Türler (Values & Types)

Bir telefon mağazasındaki bir çalışana belirli bir telefonun fiyatını sorarsanız ve "doksan dokuz, doksan dokuz" (yani 99,99 dolar) derlerse, size ne kadar alacağınızı temsil eden gerçek bir sayısal dolar rakamı vermiş olurlar. satın almak için (artı vergiler) ödeme yapmanız gerekir. Bu telefonlardan ikisini satın almak istiyorsanız, zihinsel matematiği kolayca yaparak bu değeri iki katına çıkararak temel maliyetiniz için 199,98 ABD doları elde edebilirsiniz.

Aynı çalışan başka bir benzer telefon alır ve bunun "ücretsiz" olduğunu söylerse (belki de uçak tarifeleriyle), size bir numara vermez, bunun yerine beklenen maliyetinizin (0,00 $) başka bir temsilini veriyordur - "ücretsiz" kelimesi "

Daha sonra telefonun şarj cihazının olup olmadığını sorduğunuzda bu yanıt yalnızca "evet" veya "hayır" olabilir.

Benzer şekilde, bir programda değerleri ifade ettiğinizde, onlarla yapmayı planladığınız şeye bağlı olarak bu değerler için farklı gösterimler seçersiniz.

Değerlerin bu farklı temsillerine programlama terminolojisinde *tipler* adı verilir. JavaScript, *ilkel* değerler olarak adlandırılan bu değerlerin her biri için yerleşik türlere sahiptir:

* Matematik yapmanız gerektiğinde bir 'sayı' istersiniz.
* Ekrana bir değer yazdırmak istediğinizde bir 'string'e (bir veya daha fazla karakter, kelime, cümle) ihtiyacınız vardır.
* Programınızda bir karar vermeniz gerektiğinde, bir "boolean"a ("doğru" veya "yanlış") ihtiyacınız vardır.

Doğrudan kaynak koduna dahil edilen değerlere *literaller* adı verilir. 'string' değişmezleri çift tırnak `"..."` veya tek tırnak (`'...'`) ile çevrelenir; tek fark stil tercihidir. 'sayı' ve 'boolean' sabit değerleri olduğu gibi sunulur (ör. '42', 'true' vb.).

Dikkate almak:

```js
"I am a string";
'I am also a string';

42;

true;
false;
```

"Dize"/"sayı"/"boolean" değer türlerinin ötesinde, programlama dillerinin *diziler*, *nesneler*, *işlevler* ve daha fazlasını sağlaması yaygındır. Bu ve sonraki bölümde değerler ve türler hakkında çok daha fazlasını ele alacağız.

### Türler Arasında Dönüştürme (Converting Between Types)

Bir "sayı"nız varsa ancak bunu ekrana yazdırmanız gerekiyorsa, değeri bir "dize"ye dönüştürmeniz gerekir ve JavaScript'te bu dönüşüme "zorlama" adı verilir. Benzer şekilde, birisi bir e-ticaret sayfasındaki bir forma bir dizi sayısal karakter girerse, bu bir "dize"dir, ancak daha sonra bu değeri matematik işlemleri yapmak için kullanmanız gerekirse, onu bir "sayıya" *zorlamanız* gerekir .

JavaScript, *türler* arasında zorla zorlama için birkaç farklı olanak sağlar. Örneğin:

```js
var a = "42";
var b = Number( a );

console.log( a );	// "42"
console.log( b );	// 42
```

Gösterildiği gibi 'Number(..)' (yerleşik bir işlev) kullanmak, herhangi bir türden 'sayı' türüne *açık* bir zorlamadır. Bu oldukça basit olmalı.

Ancak tartışmalı bir konu, halihazırda aynı türde olmayan iki değeri karşılaştırmaya çalıştığınızda ne olacağıdır, bu da *örtük* zorlama gerektirir.

"99,99" dizesini "99,99" sayısıyla karşılaştırırken çoğu kişi bunların eşdeğer olduğunu kabul eder. Ama tam olarak aynı değiller, değil mi? İki farklı gösterimde, iki farklı *türde* aynı değerdir. Bunların "genel olarak eşit" olduğunu söyleyebilirsin, değil mi?

Bu yaygın durumlarda size yardımcı olmak için, JavaScript bazen devreye girer ve eşleşen türlere değerleri *örtük olarak* zorlar.

Eğer `"99.99"` ile 99.99'u karşılaştırmak için `==` gevşek eşit operatörünü kullanırsanız, JavaScript sol tarafındaki `"99.99"`'u onun `number` karşılığı olan `99.99`'a dönüştürecektir. Karşılaştırma daha sonra `99.99 == 99.99` halini alır, ki bu tabii ki `true` (doğru) olur.

Size yardımcı olmak amacıyla tasarlanmış bir mekanizma olsa da, belirli davranışlarını yönlendiren kuralları öğrenme zamanını ayırmadıysanız, zımni tip dönüşüm kafa karışıklığına neden olabilir. Birçok JS geliştiricisi bu kuralları öğrenmemiştir, bu nedenle yaygın bir düşünce, zımni tip dönüşümün kafa karıştırıcı olduğu ve beklenmeyen hatalarla programlara zarar verdiği ve bu nedenle kaçınılması gerektiğidir. Hatta bazen dilin tasarımındaki bir kusur olarak adlandırılır.

Ancak zımni tip dönüşüm, öğrenilebilecek ve üst düzeyde JavaScript programlamak isteyen herkesin öğrenmesi gereken bir mekanizmadır. Kuralları öğrendikten sonra kafa karıştırıcı olmadığı gibi, aslında programlarınızı daha iyi hale getirebilir! Bu çaba kesinlikle buna değer.

Not: Daha fazla dönüşüm hakkında bilgi için bu başlığın 2. Bölümüne ve bu serinin Türler ve Dil başlığının 4. Bölümüne bakınız.

## Yorum Satırları (Code Comments)

Telefon mağazası çalışanı, yeni çıkan bir telefonun özellikleri veya şirketinin sunduğu yeni planlar hakkında bazı notlar alabilir. Bu notlar sadece çalışan içindir - müşterilerin okuması için değil. Bununla birlikte, bu notlar, çalışanın işini müşterilere ne söylemesi gerektiğinin nasıl ve neden belgelendiği konusunda daha iyi yapmasına yardımcı olur.

Kod yazma konusunda öğrenebileceğiniz en önemli derslerden biri, kodun sadece bilgisayara yönelik olmadığıdır. Kod, geliştirici için derleyiciden daha fazla, eğer öyleyse, gibidir.

Bilgisayarınız sadece makine koduyla ilgilenir, derlemelerden gelen bir dizi ikili 0 ve 1'den oluşur. Aynı 0'lar ve 1'ler serisini veren yazabileceğiniz neredeyse sonsuz sayıda program vardır. Programınızı nasıl yazmanız gerektiğine dair yaptığınız seçimler önemlidir - sadece sizin için değil, aynı zamanda diğer takım üyeleriniz ve hatta gelecekteki kendiniz için de önemlidir.

Sadece doğru çalışan programlar yazmaya değil, incelendiğinde anlamlı olan programlar yazmaya çalışmalısınız. Bu çaba ile değişkenleriniz için iyi isimler seçerek (bkz. "Değişkenler") ve işlevleriniz için (bkz. "Fonksiyonlar") iyi isimler seçerek çok yol kat edebilirsiniz.

Ancak başka bir önemli kısım da kod açıklamalarıdır. Bunlar, programınızın içine yerleştirilen ve yalnızca bir insanın anlaması için olan metin parçalarıdır. Yorumlar her zaman yorumlayıcı/derleyici tarafından görmezden gelinir.

İyi açıklamalı kod yapmanın neyin iyi olduğu hakkında birçok görüş vardır; gerçekten mutlak evrensel kuralları tanımlayamayız. Ancak bazı gözlemler ve yönergeler oldukça kullanışlıdır:

Açıklama içermeyen kod altoptimaldir.
Çok fazla açıklama (örneğin her satır için bir açıklama) muhtemelen kötü yazılmış kodun bir işareti olabilir.
Açıklamalar ne değil, neden açıklamalıdır. Özellikle karışık bir durumsa, nasıl açıklayabilirler.
JavaScript'te iki tür açıklama mümkündür: tek satırlık açıklama ve çok satırlık açıklama.

Düşünün:

```js
// This is a single-line comment

/* But this is
       a multiline
             comment.
                      */
```

`//` tek satırlık yorum, bir ifadenin hemen üstüne veya hatta bir satırın sonuna bir yorum eklemeyi düşünüyorsanız uygundur. `//`'den sonraki satırın sonuna kadar olan her şey yorum olarak kabul edilir (ve bu nedenle derleyici tarafından görmezden gelinir). Tek satırlık yorumun içine neyin yerleştirilebileceğine dair bir kısıtlama yoktur.

Düşünün:

```js
var a = 42;		// 42 is the meaning of life
```

`/* .. */` çok satırlı yorum, yorumunuzda açıklamanız gereken birkaç satır varsa uygun bir seçenektir.

İşte çok satırlı yorumların yaygın bir kullanımı:

```js
/* The following value is used because
   it has been shown that it answers
   every question in the universe. */
var a = 42;
```

Ayrıca satırın herhangi bir yerinde, hatta ortasında bile görünebilir, çünkü `*/` onu bitirir. Örneğin:

```js
var a = /* arbitrary value */ 42;

console.log( a );	// 42
```

Çok satırlı bir yorumun içinde görünemeyen tek şey `*/` işaretidir çünkü bu, yorumu sonlandırmak için yorumlanır.

Programlama öğreniminize kesinlikle kod yorumlama alışkanlığıyla başlamak isteyeceksiniz. Bu bölümün geri kalanında, bazı şeyleri açıklamak için yorumları kullandığımı göreceksiniz, o yüzden aynısını kendi uygulamalarınızda da yapın. İnanın bana, kodunuzu okuyan herkes size teşekkür edecek!

## Değişkenler (Variables)

Çoğu kullanışlı program, programın amaçladığı görevlere göre gerektiğinde farklı işlemlerden geçerek, programın ilerleyişi boyunca bir değeri takip etmesi gerekmektedir.

Programınızda bunu yapmanın en kolay yolu, sembolik bir kap içine bir değer atamaktır ve bu kap bir *değişken* olarak adlandırılır - çünkü bu kap içindeki değer, ihtiyaca göre zaman içinde *değişebilir*.

Bazı programlama dillerinde, `number` veya `string` gibi belirli bir değeri tutmak için bir değişken (kap) tanımlarsınız. *Statik yazma*, aksi halde *tip zorunluluğu* olarak da bilinir, genellikle istenmeyen değer dönüşümlerini önleyerek program doğruluğu için bir fayda olarak belirtilir.

Diğer diller, değişkenler yerine değerler için türleri vurgular. *Zayıf yazma*, aksi halde *dinamik yazma* olarak bilinir, bir değişkenin herhangi bir zamanda herhangi bir türde bir değeri tutmasına olanak tanır. Genellikle program esnekliği için bir fayda olarak belirtilir, çünkü tek bir değişkenin bir değeri temsil etmesine izin verir, bu değerin programın mantık akışındaki herhangi bir anında hangi tür formunu alabileceğine bakılmaksızın.

JavaScript, *dinamik yazma* yaklaşımını kullanır, bu da değişkenlerin herhangi bir *tür* değerini herhangi bir *tür* zorunluluğu olmadan tutabilmesi anlamına gelir.

Daha önce belirtildiği gibi, bir değişkeni `var` ifadesini kullanarak tanımlarız - dikkatinizi çekeceği üzere tanımda başka bir *tür* bilgisi yoktur. Bu basit bir programı düşünün:

```js
var amount = 99.99;

amount = amount * 2;

console.log( amount );		// 199.98

// convert `amount` to a string, and
// add "$" on the beginning
amount = "$" + String( amount );

console.log( amount );		// "$199.98"
```

`amount` değişkeni başlangıçta `99.99` sayısını tutar ve ardından `amount * 2` işleminin sonucu olan `number` değeri olan `199.98`'i tutar.

İlk `console.log(..)` komutu, bu `number` değerini yazdırmak için *zımni olarak* `string`e dönüştürmek zorundadır.

Ardından `amount = "$" + String(amount)` ifadesi, `199.98` değerini *açıkça* `string`e dönüştürür ve başına bir `"$"` karakteri ekler. Bu noktada `amount` artık `string` değer olan `"$199.98"` değerini tutar, bu yüzden ikinci `console.log(..)` ifadesinin onu yazdırmak için herhangi bir dönüşüm yapmasına gerek yoktur.

JavaScript geliştiricileri, `amount` değişkenini `99.99`, `199.98` ve `"$199.98"` değerlerinin her biri için kullanma esnekliğini görecektir. Statik yazma tutkunları, farklı bir tür olduğu için son `"$199.98"` temsilini tutmak için ayrı bir değişken olan `amountStr` tercih ederler.

Her durumda, `amount`'un programın çalışması boyunca değişen bir değeri tuttuğunu göreceksiniz, bu da değişkenlerin temel amacını gösterir: program *durumu* yönetmek.

Diğer bir deyişle, *durum*, programınız çalıştıkça değerlerin değişikliklerini takip etmektir.

Değişkenlerin yaygın bir başka kullanımı, değer ayarlamanın merkezileştirilmesi içindir. Bu genellikle bir değişkeni bir değerle birlikte bildirdiğinizde *sabitler* olarak adlandırılır ve bu değerin programın tüm süresi boyunca *değişmemesi* ni amaçladığınızda kullanılır.

Bu *sabitleri*, genellikle bir programın en üstünde bildirirsiniz, böylece bir değeri değiştirmeniz gerektiğinde kolaylıkla gidilecek bir yeriniz olur. Geleneksel olarak, JavaScript değişkenleri sabitler olarak adlandırılır ve genellikle büyük harfle yazılır, birden çok kelimenin arasına alt çizgi `_` eklenir.

İşte saçma bir örnek:

```js
var TAX_RATE = 0.08;	// 8% sales tax

var amount = 99.99;

amount = amount * 2;

amount = amount + (amount * TAX_RATE);

console.log( amount );				// 215.9784
console.log( amount.toFixed( 2 ) );	// "215.98"
```

**Not:** `console.log(..)`'ın `console` değeri üzerinde bir nesne özelliği olarak erişilen bir işlev olduğu gibi, burada `toFixed(..)` bir `number` değeri üzerinde erişilen bir işlemdir. JavaScript `number`'ları otomatik olarak dolar formatına dönüştürülmez - motorun ne amaçladığınızı bilme yeteneği yoktur ve bir para birimi türü yoktur. `toFixed(..)` bize `number`'ın kaç ondalık basamağa yuvarlanacağını belirlememize olanak tanır ve gerekli olduğunda `string`i üretir.

`TAX_RATE` değişkeni sadece bir gelenek olarak *sabit* olarak kabul edilir - bu programda değiştirilmesini engelleyen özel bir şey yoktur. Ancak şehir satış vergi oranını %9'a yükseltirse, programımızı hala `TAX_RATE` atanmış değeri programın her yerine yayılmış `0.08` değerinin çoklu örneklerini bulmak ve hepsini güncellemek yerine bir yerde `0.09` olarak ayarlayarak kolayca güncelleyebiliriz.

Bu yazının yazıldığı sırada JavaScript'in en son sürümü (genellikle "ES6" olarak adlandırılır) `var` yerine `const` kullanarak *sabitleri* bildirmek için yeni bir yol içerir:

```js
// as of ES6:
const TAX_RATE = 0.08;

var amount = 99.99;

// ..
```

Sabitler, değişmeyen değerlere sahip değişkenler gibi kullanışlıdır, ancak sabitler ayrıca başlangıçtan sonra başka bir yerde değerin yanlışlıkla değiştirilmesini önler. İlk bildirimin ardından `TAX_RATE`'e farklı bir değer atamayı denerseniz, programınız değişikliği reddeder (ve sıkı modda hata ile başarısız olur - bkz. "Sıkı Mod" Bölüm 2'de).

Bu arada, bu tür hatalara karşı "koruma", hatalara karşı koruma anlamına geldiğinden, neden diğer dillerdeki statik yazma türü zorunluluğun cazip olabileceğini görebilirsiniz!

**Not:** Değişkenlerdeki farklı değerlerin programlarınızda nasıl kullanılabileceği hakkında daha fazla bilgi için bu serinin *Türler ve Dil* başlığını inceleyin.

## Bloklar (Blocks)

Telefon mağazası çalışanı, yeni telefonunuzu satın aldığınızda ödeme işlemini tamamlamak için bir dizi adımı tamamlamak zorundadır.

Benzer şekilde, kod içinde sıklıkla bir dizi ifadeyi bir araya getirmemiz gerekebilir, bu da genellikle bir *blok* olarak adlandırılır. JavaScript'te bir blok, bir veya daha fazla ifadeyi bir süslü parantez çifti `{ .. }` içine alarak tanımlanır. Düşünün:

```js
var amount = 99.99;

// a general block
{
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

Bu tür bağımsız `{ .. }` genel blok geçerlidir, ancak JS programlarında genellikle görülmez. Genellikle bloklar, bir `if` ifadesi (bkz. "Koşullar") veya bir döngü (bkz. "Döngüler") gibi diğer kontrol ifadesine bağlanır. Örneğin:

```js
var amount = 99.99;

// is amount big enough?
if (amount > 10) {			// <-- block attached to `if`
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

`if` ifadelerini bir sonraki bölümde açıklayacağız, ancak gördüğünüz gibi, `{ .. }` blok, iki ifade ile `if (amount > 10)`'a bağlanmıştır; blok içindeki ifadeler, koşul geçerliyse yalnızca işlenir.

**Not:** `console.log(amount);` gibi çoğu diğer ifadeye benzemez, bir blok ifadesinin sona erdirmek için bir noktalı virgül (`;`) gerektirmez.

## Şartlar (Conditionals)

"Ekstra ekran koruyucularını satın almak ister misiniz, fiyatı 9.99 dolar?" Yardımsever telefon mağazası çalışanı size bir karar vermenizi istedi. Ve bu soruya cevap vermek için önce cüzdanınızın veya banka hesabınızın mevcut *durumunu* danışmanız gerekebilir. Ancak açıkçası, bu sadece basit bir "evet veya hayır" sorusudur.

Programlarımızda *koşullu ifadeleri* (kararlar olarak da adlandırılır) ifade etmenin birkaç yolunu kullanabiliriz.

En yaygın olanı `if` ifadesidir. Temelde, "*Eğer* bu koşul doğruysa, aşağıdakileri yap..." diyorsunuz. Örneğin:

```js
var bank_balance = 302.13;
var amount = 99.99;

if (amount < bank_balance) {
	console.log( "I want to buy this phone!" );
}
```

`if` ifadesi, `true` veya `false` olarak işlem görebilen parantezler `( )` arasında bir ifade gerektirir. Bu programda, gerçekten de `bank_balance` değişkenindeki miktarına bağlı olarak `true` veya `false` değerine değerlendirilebilecek olan `amount < bank_balance` ifadesini sağladık.

Koşul doğru değilse bir alternatif bile sağlayabilirsiniz, bu da bir `else` ifadesi olarak adlandırılır.

Düşünün:

```js
const ACCESSORY_PRICE = 9.99;

var bank_balance = 302.13;
var amount = 99.99;

amount = amount * 2;

// can we afford the extra purchase?
if ( amount < bank_balance ) {
	console.log( "I'll take the accessory!" );
	amount = amount + ACCESSORY_PRICE;
}
// otherwise:
else {
	console.log( "No, thanks." );
}
```

Burada, `amount < bank_balance` `true` ise, `"Aksesuarı alacağım!"` yazdıracağız ve `9.99`'u `amount` değişkenimize ekleyeceğiz. Aksi takdirde, `else` ifadesi, yalnızca nazikçe `"Hayır, teşekkürler."` cevabı vereceğimizi ve `amount`'un değişmeden kalacağını belirtir.

Daha önce "Değerler ve Türler" başlığında tartıştığımız gibi, beklenen bir türün dışında olan değerler genellikle bu türe zorlanır. `if` ifadesi bir `boolean` bekler, ancak ona zaten bir `boolean` olmayan bir şey geçirirseniz, zorlama gerçekleşir.

JavaScript, bir `boolean` yapılınca `false` haline gelen belirli değerlerin bir listesini tanımlar ve bu değerler "yanıltıcı" olarak kabul edilir - bunlar `0` ve `""` gibi değerleri içerir. "Yanıltıcı" listesinde bulunmayan diğer herhangi bir değer otomatik olarak "doğru" olarak kabul edilir - bir `boolean` haline getirildiğinde `true` olurlar. Doğru değerler, `99.99` ve `"ücretsiz"` gibi şeyleri içerir. Daha fazla bilgi için "Doğru ve Yanıltıcı"ya bakın.

*Koşullular*, `if` dışında başka biçimlerde de bulunur. Örneğin, `switch` ifadesi, bir dizi `if..else` ifadesi için bir kısaltma olarak kullanılabilir (Bkz. Bölüm 2). Döngüler (Bkz. "Döngüler"), döngünün devam etmesi veya durması gerekip gerekmediğini belirlemek için bir *koşullu* kullanır.

**Not:** *Koşulluların* test ifadelerinde örtülü olarak gerçekleşebilecek dönüşümler hakkında daha fazla bilgi için bu serinin *Türler ve Dil* başlığının Bölüm 4'üne bakın.

## Döngüler (Loops)

Yoğun saatlerde, telefon mağazası çalışanıyla konuşmaya ihtiyaç duyan müşteriler için bir bekleme listesi vardır. Liste üzerinde hala insanlar olduğunda, sadece bir sonraki müşteriye hizmet etmeye devam etmesi gerekir.

Belirli bir koşul başarısız olana kadar belirli bir işlem kümesini tekrar etmek - yani koşul geçerli olduğu sürece tekrarlamak - programlama döngülerinin görevidir; döngüler farklı biçimler alabilir, ancak hepsi bu temel davranışı karşılar.

Bir döngü, test koşulunu ve bir bloğu (genellikle `{ .. }`) içerir. Döngü bloğu her çalıştığında, bu bir *yineleme* olarak adlandırılır.

Örneğin, `while` döngüsü ve `do..while` döngüsü biçimleri, bir bloğu bir koşul artık `true` olarak değerlendirilmediği sürece tekrar etme kavramını göstermektedir:

```js
while (numOfCustomers > 0) {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
}

// versus:

do {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
} while (numOfCustomers > 0);
```

Bu döngüler arasındaki tek pratik fark, koşulun ilk yinelemeden önce mi (`while`) yoksa ilk yinelemeden sonra mı (`do..while`) test edildiğidir.

Her iki biçimde de, koşul `false` olarak test edilirse bir sonraki yineleme çalışmayacaktır. Bu, koşulun başlangıçta `false` ise, bir `while` döngüsünün hiç çalışmayacağı, ancak bir `do..while` döngüsünün yalnızca ilk kez çalışacağı anlamına gelir.

Bazen belirli bir dizi sayıyı sayma amacıyla döngü yapıyor olabilirsiniz, örneğin `0` ile `9` arasındaki (on sayı). Bunu, bir döngü yineleme değişkenini `i` gibi `0` değerinde ayarlayarak ve her yineleme de `1` artırarak yapabilirsiniz.

**Uyarı:** Tarihsel nedenlerden dolayı, programlama dilleri neredeyse her zaman şeyleri sıfırdan başlayarak sayarlar, yani `1` yerine `0` ile başlarlar. Bu düşünme biçimini bilmiyorsanız, başta oldukça kafa karıştırıcı olabilir. Daha rahat hissetmek için `0` ile başlayarak saymayı uygulamak için biraz zaman ayırın!

Koşul her yinelemede test edilir, sanki döngü içinde bir anlamda bir `if` ifadesi varmış gibi.

Bir döngüyü durdurmak için JavaScript'in `break` ifadesini kullanabiliriz. Ayrıca, aksi takdirde sonsuz bir şekilde çalışacak bir döngü oluşturmanın kolay olduğunu gözlemleyebiliriz.

İllüstre edelim:

```js
var i = 0;

// a `while..true` loop would run forever, right?
while (true) {
	// stop the loop?
	if ((i <= 9) === false) {
		break;
	}

	console.log( i );
	i = i + 1;
}
// 0 1 2 3 4 5 6 7 8 9
```

**Uyarı:** Bu mutlaka döngüleriniz için kullanmak isteyeceğiniz pratik bir form değildir. Burada yalnızca örnekleme amacıyla sunulmuştur.

Bir `while` (veya `do..while`) görevi manuel olarak yerine getirebilirken, bu iş için özel olarak tasarlanmış başka bir sözdizimsel biçim olan bir `for` döngüsü de bulunmaktadır:

```js
for (var i = 0; i <= 9; i = i + 1) {
	console.log( i );
}
// 0 1 2 3 4 5 6 7 8 9
```

Gördüğünüz gibi, her iki durumda da koşul `i <= 9`, her iki döngü biçimi için ilk 10 yineleme (`i` değerleri `0` ile `9` arasında) için `true`'dur, ancak `i` değeri `10` olduğunda `false` olur.

`for` döngüsü üç kısımdan oluşur: başlatma kısmı (`var i=0`), koşul test kısmı (`i <= 9`) ve güncelleme kısmı (`i = i + 1`). Bu nedenle, eğer döngü yinelemeleri ile sayma yapacaksanız, `for` daha kompakt ve genellikle daha anlaşılır ve yazması daha kolay bir biçimdir.

Özel amaçlı başka döngü biçimleri de bulunur ve bu biçimler belirli değerler üzerinde dönmek amacıyla tasarlanmıştır, örneğin bir nesnenin özellikleri (Bkz. Bölüm 2) gibi, burada örtülü koşul testi sadece tüm özelliklerin işlenip işlenmediğidir. "Koşul başarısız olana kadar döngüyü yinele" kavramı, döngünün biçimine bakılmaksızın her zaman geçerlidir.

## Fonksiyonlar (Functions)

Telefon mağazası çalışanının muhtemelen vergileri ve son satın alma miktarını hesaplamak için bir hesap makinesi taşıma ihtimali düşüktür. Bu, bir kez tanımlanması ve tekrar tekrar kullanılması gereken bir görevdir. Muhtemelen, şirketin bu "fonksiyonları" entegre edilmiş bir ödeme kaydı (bilgisayar, tablet vb.) vardır.

Benzer şekilde, programınız büyük olasılıkla kodun görevlerini yeniden kullanılabilir parçalara bölmek isteyecek ve kendinizi sürekli olarak tekrar ederken bulunmak istemezsiniz. Bunu yapmanın yolu bir `fonksiyon` tanımlamaktır.

Bir fonksiyon genellikle adlandırılmış bir kod bölümüdür ve adıyla "çağrılabilir", ve içindeki kod her seferinde çalıştırılır. Düşünün:

```js
function printAmount() {
	console.log( amount.toFixed( 2 ) );
}

var amount = 99.99;

printAmount(); // "99.99"

amount = amount * 2;

printAmount(); // "199.98"
```

Fonksiyonlar isteğe bağlı olarak argümanlar (veya parametreler) alabilirler - içine geçirdiğiniz değerler. Ayrıca isteğe bağlı olarak bir değer de döndürebilirler.

```js
function printAmount(amt) {
	console.log( amt.toFixed( 2 ) );
}

function formatAmount() {
	return "$" + amount.toFixed( 2 );
}

var amount = 99.99;

printAmount( amount * 2 );		// "199.98"

amount = formatAmount();
console.log( amount );			// "$99.99"
```

`printAmount(..)` fonksiyonu `amt` adını verdiğimiz bir parametre alır. `formatAmount()` fonksiyonu bir değer döndürür. Tabii ki, bu iki tekniği aynı fonksiyonda birleştirebilirsiniz.

Fonksiyonlar genellikle birden çok kez çağırmayı planladığınız kodlar için kullanılır, ancak sadece bir kez çağırmayı planlıyorsanız bile, ilgili kod parçacıklarını adlandırılmış koleksiyonlar içinde düzenlemek için yararlı olabilirler.

Düşünün:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}

var amount = 99.99;

amount = calculateFinalPurchaseAmount( amount );

console.log( amount.toFixed( 2 ) );		// "107.99"
```

`calculateFinalPurchaseAmount(..)` sadece bir kez çağrılsa bile, davranışını ayrı bir adlandırılmış fonksiyona düzenlemek, mantığını kullanan kodu ( `amount = calculateFinal...` ifadesi) daha temiz hale getirir. Eğer fonksiyonun içinde daha fazla ifade olsaydı, faydaları daha da belirgin olurdu.

### Kapsam (Scope)

Eğer telefon mağazası çalışanından mağazasında bulunmayan bir telefon modeli isterseniz, istediğiniz telefonu size satamayacaktır. Sadece mağazasının envanterindeki telefonlara erişimi vardır. İstediğiniz telefonu bulmak için başka bir mağazayı denemeniz gerekecektir.

Programlamada bu kavram için bir terim vardır: *kapsam* (teknik olarak *lexical kapsam* denir). JavaScript'te her fonksiyon kendi kapsamını alır. Kapsam temelde değişkenlerin bir koleksiyonu ve bu değişkenlerin adıyla nasıl erişileceği kurallarıdır. Sadece o fonksiyonun içindeki kod, o fonksiyonun *kapsamlı* değişkenlerine erişebilir.

Aynı kapsam içinde bir değişken adı benzersiz olmalıdır - yan yana iki farklı `a` değişkeni olamaz. Ancak aynı değişken adı `a`, farklı kapsamlarda görünebilir.

```js
function one() {
	// this `a` only belongs to the `one()` function
	var a = 1;
	console.log( a );
}

function two() {
	// this `a` only belongs to the `two()` function
	var a = 2;
	console.log( a );
}

one();		// 1
two();		// 2
```

Ayrıca, bir kapsam başka bir kapsamın içine gömülebilir, tıpkı bir doğum günü partisinde palyaçonun bir balonu başka bir balonun içine üflemesi gibi. Bir kapsam başka bir kapsamın içine gömülüyorsa, en içteki kapsamın içindeki kod, her iki kapsamdan da değişkenlere erişebilir.

Düşünün:

```js
function outer() {
	var a = 1;

	function inner() {
		var b = 2;

		// we can access both `a` and `b` here
		console.log( a + b );	// 3
	}

	inner();

	// we can only access `a` here
	console.log( a );			// 1
}

outer();
```

Lexical kapsam kuralları, bir kapsamdaki kodun, o kapsamın veya dışındaki herhangi bir kapsamın değişkenlerine erişebileceğini söyler.

Bu nedenle, `inner()` işlevi içindeki kod, hem `a` hem de `b` değişkenlerine erişebilir, ancak `outer()` içindeki kod sadece `a`'ya erişebilir - `b` değişkenine erişemez çünkü bu değişken yalnızca `inner()` içindedir.

Daha önceki bu kod örneğini hatırlayın:

```js
const TAX_RATE = 0.08;

function calculateFinalPurchaseAmount(amt) {
	// calculate the new amount with the tax
	amt = amt + (amt * TAX_RATE);

	// return the new amount
	return amt;
}
```

`TAX_RATE` sabiti (değişkeni), lexical scope nedeniyle `calculateFinalPurchaseAmount(..)` fonksiyonunun içinden erişilebilir, onu iletmemize rağmen.

**Not:** Lexical kapsam hakkında daha fazla bilgi için bu serinin *Scope & Closures* başlığındaki ilk üç bölümü inceleyebilirsiniz.

## Pratik (Practice)

Programlamayı öğrenmek için pratik yapmanın kesinlikle bir alternatifi yok. Benim tarafımdan yapılan ayrıntılı yazılar bile başlı başına sizi bir programcı yapmaz.

Bu düşünceyle, bu bölümde öğrendiğimiz bazı kavramları uygulamayı deneyelim. İlk olarak "gereksinimleri" veriyorum ve siz denemeyi yapın. Ardından, yaklaşımımı nasıl ele aldığımı görmek için aşağıdaki kod listesine başvurun.

* Telefon alımınızın toplam fiyatını hesaplamak için bir program yazın. Banka hesabınızdaki paranız bitene kadar telefonlar alacaksınız (ipucu: döngü kullanın!). Alışveriş miktarınız, zihinsel harcama sınırınızın altında olduğu sürece her telefon için aksesuarlar da alacaksınız.
* Alım miktarınızı hesapladıktan sonra vergiyi ekleyin ve hesaplanmış alım miktarını düzgün bir şekilde biçimlendirilmiş olarak yazdırın.
* Son olarak, miktarı banka hesap bakiyenizle karşılaştırın ve bunu karşılayıp karşılayamayacağınızı kontrol edin.
* "Vergi oranı", "telefon fiyatı", "aksesuar fiyatı" ve "harcama sınırı" için bazı sabitler oluşturmalısınız, ayrıca "banka hesap bakiyesi" için bir değişken oluşturmalısınız.
* Vergiyi hesaplama ve fiyatı "$" ile biçimlendirme ve iki ondalık basamağa yuvarlama işlemleri için işlevler tanımlamalısınız.
* **Bonus Zorluk:** Bu programa giriş yapmak için "Giriş" bölümünde ele alınan `prompt(..)` ile kullanıcı girişini entegre etmeyi deneyin. Örneğin, kullanıcıdan banka hesap bakiyelerini sorabilirsiniz. Eğlenin ve yaratıcı olun!

Peki, hadi deneyin. Kendi çabanızı göstermeden kodumuza bakmayın!

**Not:** Bu bir JavaScript kitabı olduğu için, açıkçası bu pratik egzersizi JavaScript'te çözeceğim. Ancak şu an daha rahat hissederseniz başka bir dilde de yapabilirsiniz.

İşte bu egzersiz için JavaScript çözümüm:

```js
const SPENDING_THRESHOLD = 200;
const TAX_RATE = 0.08;
const PHONE_PRICE = 99.99;
const ACCESSORY_PRICE = 9.99;

var bank_balance = 303.91;
var amount = 0;

function calculateTax(amount) {
	return amount * TAX_RATE;
}

function formatAmount(amount) {
	return "$" + amount.toFixed( 2 );
}

// keep buying phones while you still have money
while (amount < bank_balance) {
	// buy a new phone!
	amount = amount + PHONE_PRICE;

	// can we afford the accessory?
	if (amount < SPENDING_THRESHOLD) {
		amount = amount + ACCESSORY_PRICE;
	}
}

// don't forget to pay the government, too
amount = amount + calculateTax( amount );

console.log(
	"Your purchase: " + formatAmount( amount )
);
// Your purchase: $334.76

// can you actually afford this purchase?
if (amount > bank_balance) {
	console.log(
		"You can't afford this purchase. :("
	);
}
// You can't afford this purchase. :(
```

**Not:** Bu JavaScript programını çalıştırmanın en basit yolu, en yakın tarayıcınızın geliştirici konsoluna yazmaktır.

Nasıl bir sonuç elde ettiniz? Şimdi kodumu gördükten sonra tekrar denemekte fayda var. Ayrıca bazı sabitleri değiştirerek programın farklı değerlerle nasıl çalıştığını gözlemlemek de iyi bir fikir olabilir.

## Gözden Geçirme (Review)

Programlamayı öğrenmek karmaşık ve bunaltıcı bir süreç olmak zorunda değildir. Kafanızı sarmanız gereken sadece birkaç temel kavram var.

Bunlar yapı taşları gibi davranır. Uzun bir kule inşa etmek için önce bloğu bloğun üstüne bloğun üstüne koyarak başlarsınız. Aynı şey programlama için de geçerlidir. Temel programlama yapı taşlarından bazıları şunlardır:

* Değerler üzerinde işlem yapabilmek için *operatörlere* ihtiyacınız vardır.
* Farklı türde işlemleri gerçekleştirmek için `number` türündeki sayılarla matematik yapmak veya `string` türündeki çıktılar üretmek gibi işlemler için değerlere ve *türlere* ihtiyacınız vardır.
* Programınızın çalışması sırasında verileri (yani *durumu*) saklamak için *değişkenlere* ihtiyacınız vardır.
* Kararlar vermek için `if` ifadeleri gibi *koşullu yapıları* kullanmanız gerekir.
* Görevleri bir koşul artık doğru olmadığında kadar tekrar etmek için *döngülere* ihtiyacınız vardır.
* Kodunuzu mantıklı ve tekrar kullanılabilir parçalara ayırmak için *fonksiyonlara* ihtiyacınız vardır.

Kod yorumları, daha okunaklı kod yazmanın etkili bir yoludur, bu da programınızın daha iyi anlaşılmasını, bakımını yapılmasını ve daha sonra sorunlarla başa çıkılmasını kolaylaştırır.

Son olarak, pratik yapmanın gücünü ihmal etmeyin. Kod yazmayı öğrenmenin en iyi yolu, kod yazmaktır.

Şimdi kod yazmayı öğrenme yolunda iyi bir şekilde ilerliyorsunuz! Devam edin. Başka başlangıç seviyesi programlama kaynaklarını (kitaplar, bloglar, çevrimiçi eğitimler vb.) kontrol etmeyi unutmayın. Bu bölüm ve bu kitap iyi bir başlangıç olsa da, sadece kısa bir giriştir.

Sonraki bölüm, bu bölümden birçok kavramı daha özgü bir JavaScript bakış açısından ele alacak ve serinin geri kalanında daha derinlemesine ele alınan başlıca konuların çoğunu vurgulayacaktır.
