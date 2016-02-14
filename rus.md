# Основы CSS-селекторов на примере котиков

![confused-cat][1]

Вам проще воспринимать информацию визуально? При попытке написать CSS-селектор
для стилизации определённых элементов вы становитесь так же озадачены, как и наш
мохнатый друг над этим абзацем? Если всё это про вас — не расстраивайтесь, скоро
мы исправим это. Если вы только начинаете изучать синтаксис CSS-селекторов, то
наверняка вы испытываете трудности с запоминанием того, какой селектор за что
отвечает. Я написал это руководство с котиками для вас. Наслаждайтесь!

## Выбираем родителей

Чтобы выбрать родительский элемент, достаточно использовать в качестве селектора
класс, идентификатор или имя элемента. Добавьте после селектора
[блок объявлений][2], и на этом всё! Вот пример разметки и стилей:

    <div class="parent">
      <div class="child"></div>
      <div class="child"></div>
    </div>
    

    .parent {
      border: 10px solid cyan;
    }
    

Вот как стили повлияют на [DOM][3] (голубым подсвечен выбранный нашим селектором
элемент):

![dom-cats][4]

## Выбираем потомков

Потомки бывают двух видов. Первый вид — прямые потомки — это те элементы,
которые непосредственно вложены в родителя без всяких промежуточных элементов.
Второй вид — косвенные потомки, они включают в себя как прямых потомков, так
и вложенные в них элементы, и так далее вглубь DOM-дерева.

### Прямые потомки

Знак `>` между селекторами говорит браузеру сперва найти элемент по первому
селектору, а затем найти всех прямых потомков этого элемента, соответствующих
второму селектору. В следующем примере мы выбираем только тех потомков `.child`,
которые лежат непосредственно внутри `.parent`:

    <div class="parent">
      <div class="child"></div>
        <div class="grand child"></div>
      <div class="child"></div>
    </div>
    

    .parent > .child {
      border: 10px solid cyan;
    }
    

Вот как это повлияет на DOM:

![cats][5]

###### Targeting a Descendant

The descendant selector is less specific than the direct child selector. It
targets any element within a parent that has the class of`.child` no matter how
far down the DOM tree it resides. To use it we place a space between selectors. 
In the following example we’re looking for*any* element nested within `.parent`
`.child`.

    <div class="parent">
      <div class="child"></div>
        <div class="grand child"></div>
      <div class="child"></div>
    </div>
    

    .parent .child {
      border: 10px solid cyan;
    }
    

Here’s how it affects the DOM:

![cats][6]

### Target an Adjacent Sibling

An adjacent sibling is an element that resides next to, and on the same level
of the DOM as another. Targeting them is simple. In this case what we need to do
is join the selectors together with a`+`. Check out the example below.

    <div class="parent">
      <div class="child"></div>
      <div class="child"></div>
    </div>
    
    <div class="sibling">
      <div class="child"></div>
    </div>
    

    .parent + .sibling {
      border: 10px solid cyan;
    }
    

Here’s how it affects the DOM:

![cats][7]

### Using Multiple Selectors

Sometimes you want to apply styles to multiple elements. So how does that work
? The answer is quite simple. All one has to do is separate each selector with a
comma. Here’s an example.

    <div class="parent">
      <div class="child"></div>
      <div class="child"></div>
    </div>
    

    .parent,
    .child {
      border: 10px solid cyan;
    }
    

Here’s how it affects the DOM:

![cats][8]

### Finish Strong

To learn even more about CSS selectors (though sadly with no cats), try 
[CSS Diner][9], which will lead you from basic to complex selectors using
delicious food.

###### Props

Thanks to all the cat lovers of Flickr. All cats herded under 
[Creative Commons Attribution 2.0 Generic][10].

![cat][11]

 [header-cat][12] | [parent-cat-one][13] | [kitten-one][14] | [kitten-two][15]
[full-cat-one][16] | [full-cat-two][17] | [goofy-cat][18] | [sibling-cat][19]

 [1]: img/confused-cat.jpg
 [2]: http://developer.mozilla.org/en-US/docs/Web/CSS/Syntax
 [3]: http://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model
 [4]: img/dom-cats.png
 [5]: img/cats-css-rev-child.jpg
 [6]: img/cats-css-rev-descendant.jpg
 [7]: img/dom-cats-siblings.jpg
 [8]: img/dom-cats-multiple.jpg
 [9]: http://flukeout.github.io/
 [10]: http://creativecommons.org/licenses/by/2.0/
 [11]: img/dancing-cat.gif
 [12]: http://flic.kr/p/oczbW
 [13]: http://flic.kr/p/6v2WG4
 [14]: http://flic.kr/p/p4hE6h
 [15]: http://flic.kr/p/cWxtYy
 [16]: http://flic.kr/p/igi3Y9
 [17]: http://flic.kr/p/dmK2CR
 [18]: http://flic.kr/p/mC8vqC
 [19]: http://flic.kr/p/doo6PL