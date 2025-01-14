# Մաթեմատիկական տարրական գործողություններ

Մենք գպրոցից գիտեն շատ գործողություններ։ Դրանցից են, օրինակ գումարում `+`, բազմապատկում `*`, հանում `-` և այլն։

Այս հատվածում, մենք կսկսենք պարզ գործողույթուններից, ապա կկենտրոնանանք JavaScript-ի հատուկ ասպեկտների վրա, որոնք գոյություն չունեն դպրոցական թվաբանության մեջ։

## "ունար", "բինար" և "օպերանդ" հասկացությունները

Մինչ առաջ անցնելը, եկեք հասկանանք որոշ տերմինների նշանակությունը։

-  *Նշան* -- հասկացություն, որը կազմում է գործողությունների հիմքը։ Օրինակ ՝ `5 * 2` –ի բազմապատկման մեջ կան երկու օպերանդներ՝ ձախ օպերանդը՝ `5`, իսկ աջը՝ `2`: Երբեմն, մարդիկ «օպերանդներ»-ի փոխարեն, անվանում են «արգումենտներ»:
- Գործողությունը համարվում է *ունար* եթե այն ունի միայն մեկ օպերանդ։ Օրինակ՝ ունար ժխտումը `-` հակադարձում է թվի նշանը:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, կիրառվել է ունար ժխտում
    ```
- Գործողույթունը համարվում է *երկուական* եթե այն ունի երկու օպերանդ. Նույն մինուսը գոյություն ունի նաև հանման տեսքով:

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, երկուական մինուսը ցույց է տալիս արժեքների տարբերությունը
    ```

  Վերը նշված օրինակներում մենք ունենք երկու տարբեր օպերատորներ, որոնք կիրառում են նույն նշանը. Ժխտման օպերատոր, նշանը հակադարձող ունարի օպերատոր և հանում օպերատոր, երկուական օպերատոր, որը հանում է մեկ թիվը մյուսից:

## Մաթեմատիկա

Հետևյալ մաթեմատիկական գործողությունները աջակցվում են․

- Գումարում `+`,
- Հանում `-`,
- Բազմապատկում `*`,
- Բաժանում `/`,
- Մնացորդ `%`,
- Աստիճան բարձրացնել (անգլ․՝ Exponentiation) `**`.

Առաջին չորս գործողությունները պարզ են, մինչդեռ `%` և `**` գործողությունների համար, մի քան խոսք ավելին։

### Մնացորդ %

Մնացորդի օպերատորը հետևյալն է `%`, չնայած նշանի պատկերմանը, դա կապված չէ տոկոսների հետ:

Հետրյալ հավասարման `a % b` արդյունքը [remainder](https://en.wikipedia.org/wiki/Remainder) `a` բաժանած `b` մնացորդն է։

Օրինակ՝

```js run
alert( 5 % 2 ); // 1, 5-ը բաժանած 2-ի մնացորդը
alert( 8 % 3 ); // 2, 8-ը բաժանած 3-ի մնացորդը
```

### Աստիճան բարձրացնել  **

Աստիճան բարձրացնելու օպերատորը `a ** b` բարձրացնում է `a`-ն `b`-ի աստիճան.

Դպրոցական մաթեմատիկայում այն գրում ենք հետևյալ տեսքով a<sup>b</sup>։

Օրինակ՝

```js run
alert( 2 ** 2 ); // 2² = 4
alert( 2 ** 3 ); // 2³ = 8
alert( 2 ** 4 ); // 2⁴ = 16
```

Ինչպես մաթեմատիկայում, այստեղ նույնպես հետևայալ օպերատորը կարող ենք կիրառել ոչ ամբողջ թվերի դեպքում։

Օրինակ՝ ½-ի աստիճանը:

```js run
alert( 4 ** (1/2) ); // 2 (power of 1/2 is the same as a square root)
alert( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)
```


## Տողերի միավորումը երկուական +-ով

Եկեք ծանոթանանք JavaScript-ի հնարավորությունների հետ, որոնք հիմքում ընկած է դպրոցական թվաբանությունը։

Սովորաբար, `+` գործողությունը գումարում է թվերը։

Բայց, երբ երկուական `+`-ը կիրառովում է տողերի համար, դա միացնում է դրանք․

```js
let s = "my" + "string";
alert(s); // mystring
```

Նշում, եթե ցանկացած օպրանդ տող է, ապա մյուս օպերանդը նույնպես ձևափոխվում է տողի։

Օրինակ՝

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

Կապ չունի այն, որ առաջին օպերանդն է տող, թե երկրորդը․

Դիտարկենք ավելի բարդ օրինակ՝

```js run
alert(2 + 2 + '1' ); // "41", այլ ոչ թե "221"
```

Այստեղ օպերատորները աշխատում են հաջորդաբար։ Առաջին `+`-ը գումարում է երկու թվերը, վարադարձնում է `4`, ապա հաջորդ `+`-ը ավալցանում`1` տողային փոփոխականը, այսպիսով դա նման է հետևյալին `4 + '1' = '41'`.

```js run
alert('1' + 2 + 2); // "122", այլ ոչ թե "14"
```
Այստեղ առաջին օպերանդը տող է, կոմպիլյատորը վերաբերվում է մյուս օպերանդներին նույնպես տող . `2`-ը կմիավորվի `'1'`-ի հետ, այսպիսով դա նման է հետևյալին `'1' + 2 = "12"` և `"12" + 2 = "122"`.

Երկուական `+`-ը միակ օպերատորնե, որը նման կերպ է վարվում տողերի հետ։ Մյուս թվաբանական օպերատորները աշխատում են միայն թվերի հետ և միշտ կերպափոխում են օպերանդները թվերի։

Դիտարկենք հանման և բաժանման ցուցադրությունը․

```js run
alert( 6 - '2' ); // 4, '2'-ը ձևափոխվում է թվի
alert( '6' / '2' ); // 3, երկու օպերանդներնել ձևափոխվում են թվերի
```

## Թվային կերպափոխումներ, ունար +

Գոյություն ունի `+`-ի երկու տեսակ․ երկուական տեսակ, որը մենք կիրառեցինք վերևում և ունար տեսակ։

Ունար գումարում կամ մեկ այլ խոսքով `+` որը կիրառվում է մեկ արժեքների դեպքում, թվերի վրա չի ազդում։ Բայց եթե օպերանդը թիվ չէ, ապա ունար գումարումը այն կերպափոխում է թվի։

Օրինակ՝

```js run
// Թվերի վրա ազդեցություն չի ունենում
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// Կերպափոխում է ոչ թվային արժեքները
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

Այն իրականում անում է նույնը, ինչ `Number(...)`-ը, բայց կարճ տարբերակով։

Տողերը թվերի կերպափոխելու անհրաժեշտությունը շատ հաճախ է առաջանում։ Օրինակ՝ եթե մենք ստանում ենք դաշտերը HTML ֆորմայից, դրանք սովորաբար տողային տիպի են։ Ի՞նչ կլինի այդ դեպքում դրանց գումարը։

Երկուական գումարումը դրանք կավելացնի իրար ինչպես տող։

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", երկուական գումարը միացնում է տողերը իրար հետ
```

Եթե մենք ուզում ենք նրանց վերաբերվել որպես թվերի, կարիք կա կերպափոխելու դրանք և կատարել դրանց գումարումը:

```js run
let apples = "2";
let oranges = "3";

*!*
// երկու արժեքները մինչև երկուական գումարմանը մասնակցելը, կերպափոխվում են թվերի
alert( +apples + +oranges ); // 5
*/!*

// երկար տարբերակը
// alert( Number(apples) + Number(oranges) ); // 5
```

Մաթեմատիկական տեսանկյունից, պլյուսների առատությունը կարող է տարօրինակ թվալ։ Բայց ծրագրավորողների տեսանկյունից, հատուկ ոչինչ չկա: ունար պլյուսը կիրառվում է սկզբից, դրանք կերպափոխում են տողերը թվերի, իսկ երկուական պլյուսը գումարում է դրանք։

Ինչու՞ է ունար պլյուսը կիրառվում սկզբից, նախքան երկուականը, դա կախված է *բարձր առաջնահերթություն*.

## Օպերատորների առաջնահերթություն

Եթե արդահայտությունը ունի մեկից ավել օպերատորներ, ապա կատարման հերթականությունը սահմանվում է կախված նրանց *առաջնահերթությունից*, կամ այլ բառով, օպերատորների կանխադրված առաջնահերթ կարգը։

Դպրոցից մենք գիտեն արտահայտությունում բազմապատկման կարգի մասին `1 + 2 * 2` պետք է կատարվի մինչ գումարումը։ Դա հենց առաջնահերթությունն է: Ասում են, որ բազմապատկումը ունի *ավելի բարձր առաջնահերթություն* քան թե գումարումը։

Փակագծերը ավելի առաջնահերթ են քան մյուսները, ուստի, եթե մենք համամիտ չենք առաջնահերթությունից, կարող ենք օգտագործել դրանք, այն փոխելու համար: Օրինակ՝ գրելով `(1 + 2) * 2`.

Կան բազմաթիվ օպերատորներ JavaScript-ում։ Յուրաքանչյուր օպերատոր ունի իր համապատասխան առաջնահերթության համարը: Ավելի մեծ թիվ ունեցողը կատարվում է առաջինը։ Եթե առաջնահերթությունը նույնն է, ապա կատարման հերթականությունը ձախից դեպի աջ է։

Ահա քաղվածքը [precedence table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) (դուք պարտավոր չեք հիշել սա, բայց նշեք, որ ունար օպերատորներն ավելի բարձր են, քան համապատասխան երկուականները):

| Առաջնահերթություն | Անվանում | Նշան |
|------------|------|------|
| ... | ... | ... |
| 15 | ունար պլյուս | `+` |
| 15 | ունար ժխտում | `-` |
| 14 | աստիճան բարձրացում | `**` |
| 13 | բազմապատկում | `*` |
| 13 | բաժանում | `/` |
| 12 | գումարում | `+` |
| 12 | հանում | `-` |
| ... | ... | ... |
| 2 | վերագրում | `=` |
| ... | ... | ... |

Կարող ենք տեսնել, "ունար պլյուս"-ը ունի `15` գերակայությունը, որը մեծ է քան `12`-ը "գումարում" (երկուական պլյուս)։ Ահա թե ինչու է `"+apples + +oranges"` արտահայտությունում ունար պլյուսը կատարվում նախքան գումարումը։

## Վերագրում

Պետք է նշել այն, որ վերագրումը `=` նույնպես օպերատոոր է։ Այն գերակայության աղյուսակում ունի շատ ցածր դիրք՝ `2`։

Ահա ինչու, երբ մենք վերագրում ենք փոփոխկան, ինչպիսին է `x = 2 * 2 + 1`, հաշվարկը կատարվում է սկզբում և հետո կատարվում է`=`, պահպանելով արդյունքը `x`-ում։

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

### Վերագրումը = վերադարձնում է արժեք

Վերագրման `=` օպերատոր լինլու փաստը, ունի ոչ "կախարդական" ենթատեքստ։

JavaScript-ում բոլոր օպերատորները վերադարձնում են արժեք։ Դա ակնհայտ է `+`-ի և `-`-ի համար, բայց նաև `=`-ի համար։

`x = value`-ի կանչը գրանցում է `value`-ն  `x`-ի մեջ *և վերադարձնում է այն*։

Այա վերագրման կիրառման օրինակ, որպես բարդ արտահայտության հատված:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

Վերը նշված օրինակում, հետևյալ արտահայտության `(a = b + 1)` արժեքը դա այն է, որը պետք է վերագրվի `a`-ին (դա `3`-ն է)։ Այնուհետեւ այն օգտագործվում է հետագա արժեվորման համար։

Զվարճալի կոդ է, այնպես չէ՞: Մենք պետք է հասկանանք թե ինչպես է այն աշխատում, քանի որ երբեմն այն կարող եք հանդիպել JavaScript-ի գրադարաններում։

Ամեն դեպքում, խնդրում եմ, կոդը այդպես մի գրեք: Նման հնարքները հաստատ հստակ ու հասկանալի չեն դարձնում կոդը:

### Կապակցված վերագրումներ

Մեկ այլ հետաքրքիր առանձնահատկություն է վերգրումների կապակցումը․

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Կապակցումը կատարվում է աջից դեպի ձախ։ Առաջին կատարվում է ամենաաջակողմյան `2 + 2` արդահայտությունը, ապա վերագրվում է ձախ կողմի փոփոխականին․ `c`, `b` և `a`։ Ամենավերջում, բոլոր փոփոխականները հավաքվում է մեկ արժեքի մեջ։

Կրկին անգամ, ընթերցելիության նկատառումներից ելնելով, լավ է որ այն բաժանված է մի քանի տողերի․

```js
c = 2 + 2;
b = c;
a = c;
```
Սա հեշտ է ընթերցվում, հատկապես այն դեպքւոմ, երբ աչքը արագ է դիտարկում կոդը։

## Փոփոխել տեղում

Երբեմն մենք կարիք ենք ունենում, կիրառել օպերատորը և պահպանել նոր արդյունքը նույն փոփոխականի մեջ։

Օրինակ՝

```js
let n = 2;
n = n + 5;
n = n * 2;
```

Այս ամենը կարող ենք կարճ գրել `+=` և `*=`:

```js run
let n = 2;
n += 5; // այժմ n = 7 (նույնն է ինչ n = n + 5)
n *= 2; // այժմ n = 14 (նույնն է ինչ n = n * 2)

alert( n ); // 14
```

Կարճ "ձևափոխել և վերագրել" օպերատորները գոյություն ունեն բոլոր մաթեմատիկական և բիթային օպերատորների համար․ `/=`, `-=` և այլն։

Նման օպերատորներն ունեն նույն գերակայությունը, ինչ սովորական վերագրումները, այնպես որ նրանք աշխատում են շատ այլ հաշվարկներից հետո.

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (նախ կատարվում է աջ մասը, նույնն է ինչ n *= 8)
```

## Ինկրեմենտ/դեկրեմենտ

<!-- Can't use -- in title, because the built-in parser turns it into a 'long dash' – -->

Թիվը մեկով մեծացնելը կամ փոքրացնելը ամենատարածված թվային գործողություններից է։

Այսպիսով դրա համար կան հատուկ օպերատորներ․

- **Ինկրեմենտ** `++` փոփոխականի ավելացումը 1-ով․

    ```js run no-beautify
    let counter = 2;
    counter++;        // կաշխատի որպես counter = counter + 1, բայց կարճ տարբերակով
    alert( counter ); // 3
    ```
- **Դեկրեմենտ** `--` փոքրացնել փոփոխականը 1-ով․

    ```js run no-beautify
    let counter = 2;
    counter--;        // կաշխատի որպես counter = counter - 1, բայց կարճ տարբերակով
    alert( counter ); // 1
    ```

```warn
Ինկրեմենտ/դեկրեմենտ պետք է կրատվի փոփոխականների համար։ Այն փորձելով օգտագործել օրինակ՝ `5++` փոփոխականի համար կստանանք սխալ։
```

`++` և `--` օպերատորները կարող են տեղադրվել փոփոխականից առաջ և հետո։

- Երբ օպերատորը կիրառվում է փոփոխականից հետո, դա համարվում է "պոստֆիքս կառուցվածք"․ `counter++`.
- "պրեֆիքս կառուցվածք"-ը երբ կիրառվում է փոփոխականից առաջ․ `++counter`.

Բոլոր գործեղությունները կատարում են նույնը․ ավելացնում են `counter`-ին `1`.

Կա՞ արդյոք տարբերություն․ Այո, բայց դա մենք կարող ենք տեսնել դա միայն վերադարձվող արժեքում `++/--`.

Եկեք պարզաբանենք։ Ինչպես գիտենք բոլոր օպերատորները վերադարձնում են արժեք։ Ինկրեմենտ/դեկրեմենտ-ը բացառություն չեն։ Պրեֆիքս տեսքը վերադարձնում է նոր արժեք, մինչ դեռ պոստֆիքը վերադարձնում է հին արժեքը (նախքան ինկրեմենտ/դեկտրեմենտ-ը).

Տարբերությունը տեսնելու համար, դիտարկենք օրինակը․

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

Հետևյալ տողում `(*)`, *պրեֆիք*-ը `++counter` ավելացնում է `counter`-ի արժեքը և վերադարձնում է նոր արժեքը, `2`։ Այսպիսով `alert`-ը ցույց կտա`2`։

Դիտարկենք պոստֆիքս կառուցվածքը․

```js run
let counter = 1;
let a = counter++; // (*)  ++counter-ը ձևափոխվել է counter++ - ի

alert(a); // *!*1*/!*
```

Հետևյալ տեղում `(*)`, *պոստվիքս* կառուցվածքը `counter++` նույնպես ավելացնում է `counter`-ի արժեքը, բայց վերադարձնում է *հին* արժեքը (նախքան ավելացումը)։ Այսպիսով `alert`-ը ցույց կտա `1`։

Ամփոփում․

- Եթե ինկրեմենտ/դեկրեմենտ-ի արժեքները չեն օգտագործվում, ապա տարբերություն չկա թե որ մեկը կկիրառվի․

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, վերը նշված տողերը իրականացնում են նույնը
    ```
- Եթե մենք ցանկանում են ավելացնել արժեքը *և* անմիջապես օգտագործել օպերատորի արժեքը, մենք պետք է օգտագործենք պրեֆիքս կառուցվածքը․

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- Եթե ցանկանում ենք ավելացնել արժեքը, բայց օգտագործել նախորդ արժեքը, կարիք կա կիրառելու պոստֆիքս կառուցվածքը․

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Increment/decrement among other operators"
Հետևյալ օպերատորները `++/--` կարող են կիրառվել նաև արտահայտությունների ներսում։ Նրանց գերակայությունն ավելի բարձր է, քան մյուս թվաբանական գործողություններինը։

Օրինակ՝

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Համեմատել հետևյալի հետ

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, քանի որ counter++ վերադարձնում է "հին" արժեքը
```

Չնայած տեխնիկապես սա լավ է, սովորաբար նման կիարառությունը կոդը դարձնում է քիչ ընթեռնելի։ Մի տողը կատարում է բազմաթիվ գործողություններ -- դա լավ չէ։

Քանի դեռ ընթերցվում է կոդը, արագ "ուղղահայաց" դիտարկումը կարող է բաց քողնել այնպիսի բան, ինչպիսին է `counter++`-ը և ակնհայտ չի լինի, որ փոփոխականի արժեքը ավելացել է։

Մենք խորհուրդ ենք տալիս "մեկ տող -- մեկ գործողություն" ոճը:

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Բիթային օպերատորներ

Բիթային օպերատորները արգումենտներին վերաբերվում են որպես 32-բիթ երկարությամբ ամբողջ թվերի և աշխատում են իրենց երկուական ներկայացման մակարդակով:

Այս օպերատորները կոնկրետ JavaScript-ինը չեն։ Դրանք աջակցվում են ծրագրավորման լեզուների մեծ մասում։

Օպերատորների ցանկը․

- և ( `&` )
- կամ ( `|` )
- Բացառող կամ (XOR) ( `^` )
- ժխտում ( `~` )
- Ձախ տեղաշարժ ( `<<` )
- Աջ տեխաշարժ ( `>>` )
- Զրոյի ավելացմամբ աջ տեղաշարժ ( `>>>` )

Այս օպերատորները շատ հազվադեպ են օգտագործվում, երբ մենք պետք է կիրառենք թվերը ամենացածր (բիթային) մակարդակում։ Մեզ այս օպերատորները շուտով պետք չեն լինի, քանի որ վեբ ծրագրավորման մեջ դրանք քիչ են օգտագործում, բայց որոշ հատուկ ոլորտներում, ինչպիսին է գաղտնագրությունը, դրանք կիրառվում են։ Անհարժեշտության դեպքում կարող եք կարդալ [Բիթային օպերատորներ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Bitwise) հոդվածը MDN-ում։

## Ստորակետ

Ստորակետ օպերատորը `,` ամենահազվագյուտ և անսովոր օպերատորներից է։ Երբեմն դա օգտագործվում է ավելի կարճ կոդ գրելու համար, այնպես որ մենք պետք է դա իմանանք, որպեսզի հասկանանք, թե ինչ է կատարվում:

Հետևյալ օպերատորը թույլ է տալիս հաշվարկել մի քանի արտահայտություններ բաժանելով դրանք `,`-ով։ Նրանցից յուրաքանչյուրը հաշվարկվում է, բայց վերադարձվում է միայն վերջին արդյունքը։

Օրինակ՝

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (3 + 4-ի արդյունքը)
```

Այստես առաջին արտահայտությունը`1 + 2` վերլուծվում է, և արդյունքը անտեսվում է. Որից հետո, `3 + 4` արտահայտությունը վերլուծվում է, և վերադարձվում է որպես արդյունք։

```smart header="Comma has a very low precedence"
Խնդրում ենք նկատի ունենալ, որ ստորակետի օպերատորը շատ ցածր առաջնահերթություն ունի, ցածր քան `=`, այնպես որ փակագծերը կարևոր են վերը նշված օրինակում։

Առանց դրանց: `a = 1 + 2, 3 + 4` վերլուծվում է `+`-ը առաջին հերթին, ստանալով `a = 3, 7`, ապա վերագրամն օպերատորը `=` վերագրում է `a = 3`, իսկ մնացածը անտեսվում է։ Դա նման է հետևյալին `(a = 1 + 2), 3 + 4`։
```

Ինչու՞ է մեզ պետք օպերատոր, որը անտեսում է ամեն ինչ, բացի վերջին արտահայտությունից:

Երբեմն, երբեմն մարդիկ օգտագործում են դա, առավել բարդ կառուցվածքներում,մի շարք գործողություններ դնելում համար մեկ տողում։

Օրինակ՝

```js
// երեք օպերատորներ մեկ տողում
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Նման հնարքներ կիրառվում են JavaScript-ի մի շարք ֆրեյմվորկներում։ Ահա թե ինչում մենք դիտարկեցինք դրանք։ Բայց երբեմն դրանք չեն բարելավում կոդի ընթեռնելիությունը, ուստի դրանք օգտագործելուց առաջ պետք է լավ մտածել։
