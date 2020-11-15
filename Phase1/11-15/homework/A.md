```html
<div>
<strong>
<em>父子选择器<em>
</strong>
</div>
<em>父子选择器</em>
```
```css
   div strong em{
    color:rde;
}
```
```html
<div>
<strong>
<em>直接子元素选者器</em>
</strong>
<em>单独显示选</em>
</div>
```
```css
div>strong>em{
    color:#ffffff
}
```
```css
div>em{
    color:#0000ff
}
```
```html
<div>
<div>1</div>
<div class="并列选择器1">2</div>
<p class="并列选择器2">3</div>
</div>
```
```css
div.class{
    color:#5c3317;
}
div.并列选择器1{
    color:#ff0000;
}
p.class.并列选择器2； 
```
```html
<div>123</div>
<p>456</p>
```
```css
div,p{
    color:#00ff00;
}
```


