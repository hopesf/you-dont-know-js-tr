# You Don't Know JS: Up & Going
# Bölüm 3: YDKJS'ye Giriş

Bu dizi ne hakkında? Basitçe söylemek gerekirse, bu, JavaScript'in *tüm bölümlerini* öğrenme görevini ciddiye almakla ilgilidir, yalnızca birilerinin "iyi parçalar" olarak adlandırdığı dilin bir alt kümesini değil ve iş yerinde işinizi yapmak için ihtiyacınız olan minimal miktarı değil.

Diğer dillerdeki ciddi geliştiriciler, yazdıkları dillerin çoğunu veya tamamını öğrenmeye çaba göstermeyi beklerler, ancak JS geliştiricileri dilin çok fazla bir kısmını öğrenmeden kalma eğilimindedir gibi görünüyorlar. Bu iyi bir şey değil ve bu durumun norm olmasına izin vermeye devam etmemeliyiz.

*You Don't Know JS* (*YDKJS*) serisi, JS'yi öğrenmeye yönelik tipik yaklaşımlara büyük bir tezat oluşturur ve neredeyse okuyacağınız herhangi bir JS kitabından farklıdır. Sizi sınırlarınızın ötesine çıkmaya ve karşılaştığınız her davranış için daha derin "neden" sorularını sormaya zorlar. Bu zorluğa hazır mısınız?

Bu son bölümü, serinin geri kalan kitaplarından ne beklemeniz gerektiğini ve *YDKJS* üzerine JS öğrenme temeli oluşturmanın en etkili yolunu kısaca özetlemek için kullanacağım.

## Kapsam ve Kapanışlar

Hızla başa çıkmak zorunda kalacağınız en temel şeylerden biri, JavaScript'te değişkenlerin kapsamının gerçekten nasıl çalıştığıdır. Kapsam hakkında belirsiz *inançlar* yeterli değildir.

*Scope & Closures* başlığı, JS'nin bir "yorumlanan dil" olduğu yaygın yanlış anlamasını çürüterek başlar ve bu nedenle derlenmediği düşünülmez. Hayır.

JS motoru kodunuzu tam olarak yürütmeden hemen önce (ve bazen sırasında) derler. Bu nedenle, kodumuzun derleyici yaklaşımını daha derinlemesine anlamak için kodumuzun değişken ve işlev bildirimlerini nasıl bulduğunu ve işlediğini anlamak için kullanırız. Yolda, JS değişken kapsam yönetimi için tipik metafor olan "Hoisting"i görürüz.

Bu "leksikal kapsam"ın kritik anlayışı, kitabın son bölümünde kapanış keşfini temel aldığımız şeydir. Kapanış, muhtemelen JS'nin en önemli kavramıdır, ancak önce kapsamın nasıl çalıştığını sıkıca kavramamışsanız kapanış muhtemelen elinizin altında kalmaya devam eder.

Kapanışın önemli bir uygulaması, bu kitapta 2. Bölümde kısaca tanıttığımız modül desenidir. Modül deseni, muhtemelen tüm JavaScript'lerin en yaygın kod organizasyon desenidir; bunun derin bir anlayışı, önceliklerinizden biri olmalı.

## this ve Nesne Prototipleri

JavaScript hakkında en yaygın ve kalıcı yanlış inançlardan biri, `this` anahtar kelimesinin göründüğü işlevi işaret ettiği yanılgısıdır. Korkunç bir yanlış anlama.

`this` anahtarı, söz konusu işlemin nasıl yürütildiğine bağlı olarak dinamik olarak bağlanır ve `this` bağlama tam olarak belirlemek için anlaşılması gereken dört basit kural olduğu ortaya çıkıyor.

`this` anahtarı ile yakından ilişkili olan diğer önemli konu, nesne prototip mekanizmasıdır, bu, özellikler için bir bakış zinciridir, leksikal kapsam değişkenlerinin nasıl bulunduğu gibi. Ancak prototiplerde sarmaşık olan diğer büyük yanılgı, JS hakkındaki düşüncelerin ötesinde (sahte) sınıfları ve (sözde "prototipal") mirası taklit etme fikri.

Ne yazık ki, sını

f ve miras tasarım deseni düşünme isteği, JS'ye getirmek isteyeceğiniz en kötü şeydir, çünkü sözdizimi sizi sınıfların mevcut olduğuna inandırmaya kandırabilir, aslında prototip mekanizması davranışıyla temelde zıt bir şekilde davranır.

Konu, uyumsuzluğu görmezden gelip uyguladığınızın "miras" olduğunu düşünmek mi, yoksa nesne prototip sisteminin nasıl çalıştığını öğrenmek ve kabul etmek mi daha uygun olduğudur. İkincisi daha uygun bir şekilde "davranış yönlendirme" olarak adlandırılır.

Bu sadece sözdizimsel tercih değil. Delegasyon, farklı ve daha güçlü bir tasarım deseni olan tamamen farklı bir şeydir, bir sınıf ve mirasla tasarım yapma ihtiyacını ortadan kaldırır. Ancak bu iddialar, JavaScript'in ömrü boyunca konuyla ilgili neredeyse her blog yazısı, kitap ve konferans sunumu ile tamamen ters düşecektir.

Prototipler ve delegasyon hakkındaki iddialarım, burada benim katlanacağımdan daha ayrıntılıdır. JavaScript "sınıfları" ve "mirası" hakkında bildiğinizi düşündüğünüz her şeyi yeniden düşünmeye hazırsanız, size "kırmızı hapı al" (*Matrix* 1999) alma fırsatını sunuyorum ve bu serinin *this & Nesne Prototipleri* başlığına göz atabilirsiniz.

## Türler ve Sözdizimi

Bu serinin üçüncü kitabı, büyük ölçüde başka bir çok tartışmalı konu olan tür dönüşümünü ele almayı amaçlar. Muhtemelen, JS geliştiricilerinin içsel dönüşümle ilgili karışıklıkları konuştuğunuzda yaşadığı frustrasyondan daha fazla bir konu yoktur.

Genel kabul gören görüş, içsel dönüşümün dilin "kötü bir parçası" olduğu ve her durumda kaçınılması gereken bir şey olduğudur. Aslında, bazıları dönüşümle herhangi bir şekilde uğraşıyorsanız kodunuzu tarayıp şikayet etmek dışında hiçbir şey yapmayan araçlar olduğunu bile söylemişlerdir.

Ancak dönüşüm gerçekten bu kadar kafa karıştırıcı, kötü ve tehlikeli mi, kullanırsanız kodunuz baştan beri mahvolmuş mu?

Ben hayır diyorum. Türlerin ve değerlerin nasıl çalıştığını tam olarak anladıktan sonra, 1-3. Bölümlerde dönüşümün nasıl çalıştığını tamamen açıklamak ve dönüşümün tüm yönlerini görmek için 4. Bölüm bu tartışmayı ele alır. Hangi dönüşüm kısımlarının gerçekten şaşırtıcı olduğunu ve hangi kısımların zaman verilirse tamamen mantıklı olduğunu öğrenilmesi gerektiğinde görürüz.

Ancak sadece dönüşümün mantıklı ve öğrenilebilir olduğunu önermiyorum, aynı zamanda dönüşümün son derece faydalı ve tamamen hafife alınmış bir araç olduğunu *iddia ediyorum.* Dönüşümün, doğru bir şekilde kullanıldığında, sadece işe yaramakla kalmaz, aynı zamanda kodunuzu daha iyi hale getirir. Buna karşı olanların ve şüphecilerin hepsi bu pozisyonu küçümseyecektir, ancak ben bu pozisyonun JS oyununuzu geliştirmenin anahtarlarından biri olduğuna inanıyorum.

Sadece kalabalığın dediklerini mi takip etmek istersiniz, yoksa tüm varsayımları bir kenara bırakmaya ve dönüşüme taze bir bakış açısıyla bakmaya hazır mısınız? Bu serinin *Türler ve Sözdizimi* başlığı düşüncelerinizi yönlendirecektir.

## Asenkron ve Performans

Serinin ilk üç kitabı, dilin temel mekanizmalarına odaklanırken, dördüncü kitap, asenkron programlamayı yönetmek için mekaniklerin üzerine örülmüş desenlere odaklanmaya biraz daha genişliyor. Asenkronluk, uygulamalarımızın performansı için sadece kritik bir faktör olmakla kalmıyor, aynı zamanda yazılabilirlik ve sürdürülebilirlik açısından da *temel* bir faktör haline geliyor.

Kitap, önce "asenkron," "paralel" ve "eş zamanlı" gibi terimlerle ilgili birçok terim ve kavram karışıklığını ortadan kaldırarak başlar ve bu tür şeylerin JS'ye nasıl uygulandığını veya uygulanmadığını ayrıntılı olarak açıklar.

Ardından, asenkronluğu etkinleştirmenin temel yöntemi olarak geri aramaları incelemeye başlarız. Ancak burada, yalnızca geri aramanın çağdaş asenkron programlamanın modern gereksinimleri için tamamen yetersiz olduğunu hızla görüyoruz. Yalnızca geri aramaları içeren kodların iki temel eksikliğini belirleriz: *Kontrolün Tersine Dönmesi* (IoC) ve doğrusal akıl yürütme eksikliği.

Bu iki büyük eksikliği ele almak için, ES6 iki yeni mekanizma (ve doğrusu desenler) tanıtır: promises (sözler) ve generators (üreteçler).

Promiseler, "gelecekteki bir değer" etrafında zaman bağımsız bir kaplama sağlar ve bu değerin hazır veya henüz hazır olup olmadığına bakılmaksızın bu sözleri düşünmenizi ve birleştirmenizi sağlar. Dahası, IoC güven sorunlarını güvenilir ve birleştirilebilir bir söz mekanizması aracılığıyla çözerler.

Üreteçler, JS işlevlerinin yeni bir çalışma modunu tanıtır, böylece üreteç, `yield` noktalarında durdurulabilir ve daha sonra asenkron olarak yeniden başlatılabilir. Duraklatma ve devam etme yeteneği, üreteç içindeki senkron, ardışık görünen kodun arka planda asenkron olarak işlenmesine olanak tanır. Böyle yaparak, geri aramaların ve dolayısıyla asenkron kodumuzun neden mantıklı olduğunu adreslemiş oluruz.

Ancak promises ve generators'ın birleşimi, JavaScript'te bugüne kadar en etkili asenkron kodlama desenini "verir." Aslında, ES7 ve sonrasındaki asenkronluğun gelecekteki gelişiminin büyük bir kısmının bu temel üzerine inşa edileceğine kesin gözüyle bakılıyor. Asenkron bir dünyada etkili bir şekilde programlamak ciddi bir şekilde promises ve generators'ı birleştirmeyi öğrenmeniz gerekecek.

Eğer promises ve generators, programlarımızın daha fazla işlem yapmasını sağlayan desenleri ifade etmekle ilgiliyse ve bu nedenle daha kısa sürede daha fazla işlem yapma gereksinimini karşılıyorsa, JS'nin keşfedilmeye değer pek çok performans optimizasyon yönü bulunuyor.

5. Bölüm, Web İşçileri ile program paralelliği ve SIMD ile veri paralelliği gibi konulara dalar, aynı zamanda ASM.js gibi düşük seviye optimizasyon tekniklerini ele alır. 6. Bölüm, uygun benchmarking teknikleri açısından performans optimizasyonunu ele alır ve hangi tür performansın endişe verilmesi gereken türler olduğunu ve ihmal edilmesi gereken türleri açıklar.

Etkili bir şekilde JavaScript yazmak, bir programı birçok farklı tarayıcıda ve diğer ortamlarda dinamik olarak çalıştırılma sınırlarını aşabilen kod yazmayı gerektirir. Bir programın "

çalışır" durumdan "iyi çalışır" duruma gelmesi için bizim tarafımızdan karmaşık ve detaylı planlama ve çaba gerektirir.

*Asenkron ve Performans* başlığı, mantıklı ve performanslı JavaScript kodu yazmanız için ihtiyacınız olan tüm araçları ve becerileri size sunmak üzere tasarlanmıştır.

Ne kadar ustalaştığınıza bakılmaksızın JavaScript'i bu noktaya kadar ne kadar ustalaşmış hissetseniz de, gerçek şu ki JavaScript asla evrimleşmeyi bırakmayacak ve dahası, evrim hızı hızla artıyor. Bu gerçek, bu serinin ruhunu kabul etmek için neredeyse bir metafor gibidir; JavaScript'in her parçasını tam olarak *bilmiyoruz* çünkü hepsini tam olarak öğrendiğiniz anda, öğrenmeniz gereken yeni şeyler yolda olacaktır.

Bu başlık, dilin nereye gittiği konusundaki kısa ve orta vadeli vizyonlara adanmıştır, sadece ES6 gibi *bilinen* şeyler değil, ötesindeki *muhtemel* şeyler.

Bu serinin tüm başlıkları, bu yazının yazıldığı sırada JavaScript'in durumunu benimserken, serinin ana odak noktası daha çok ES5'ti. Şimdi dikkatimizi ES6, ES7 ve...

Bu yazının yazıldığı sırada ES6 neredeyse tamamlanmış olduğundan, *ES6 & Beyond* yeni sözdizimi, yeni veri yapıları (koleksiyonlar) ve yeni işleme yetenekleri ve API'lar dahil olmak üzere ES6 peyzajının somut bölümlerine ayrılarak başlar. Bu yeni ES6 özelliklerini, diğer kitaplarının üzerinde durulan ayrıntıları da içeren farklı ayrıntı seviyelerinde ele alıyoruz.

Okumayı dört gözle beklemek için heyecan verici bazı ES6 şeyler: nesneleri çözme (destructuring), varsayılan parametre değerleri, semboller (symbols), özeti (concise) yöntemler, hesaplanmış özellikler (computed properties), ok işlevleri (arrow functions), blok kapsamı (block scoping), sözler (promises), üreteçler (generators), yineleyiciler (iterators), modüller (modules), vekiller (proxies), zayıf haritalar (weakmaps) ve çok daha fazlası! Vay be, ES6 oldukça güçlü!

Kitabın ilk kısmı, önümüzdeki birkaç yıl içinde yazıp keşfedeceğiniz yeni ve geliştirilmiş JavaScript için öğrenmeniz gereken tüm konulara dair bir yol haritasıdır.

Kitabın son kısmı, JavaScript'in yakın geleceğinde görmeyi bekleyebileceğimiz şeylere kısa bir göz atar. Buradaki en önemli farkındalık, ES6 sonrası JS'nin muhtemelen sürüm sürüm yerine özellik özellik evrimleşeceğidir, bu da bu yakın gelecekteki şeyleri tahmin etmemizin çok daha hızlı olacağı anlamına gelir.

JavaScript için gelecek parlak. Artık onu öğrenme zamanı değil mi?

## Gözden Geçirme (Review)

*YDKJS* serisi, tüm JS geliştiricilerinin bu harika dilin tüm parçalarını öğrenmeyi ve öğrenmeyi derinlemesine anlamayı isteyebileceği teklifine adanmıştır. Hiç kimsenin görüşü, hiçbir çerçevenin varsayımı ve hiçbir proje teslim tarihi, JavaScript'i öğrenmediğiniz ve derinlemesine anlamadığınız nedeni olmamalıdır.

Dilin odaklandığı her önemli alanı ele alırız ve muhtemelen bildiğinizi düşündüğünüz ancak muhtemelen tam olarak bilmediğiniz tüm parçalarını tam olarak keşfetmek için kısa ancak çok yoğun bir kitap ayırırız.

"You Don't Know JS" bir eleştiri veya hakaret değil. Bu, hepimizin, ben dahil, yüzleşmemiz gereken bir gerçektir. JavaScript öğrenmek bir son hedef değil, bir süreçtir. JavaScript'i henüz tam olarak *bilmiyoruz*. Ama bileceğiz!
