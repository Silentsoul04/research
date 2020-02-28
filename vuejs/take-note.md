# Take-note

---

# Some case XSS in VueJS

## v-html

https://codepen.io/vouill/pen/wdVdZZ

```html
<div id="app" class="container">
   Welcome :
  <span v-html="attack">
   </span>
</div>
```

