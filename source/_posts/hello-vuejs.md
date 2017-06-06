---
title: Hello VueJs
date: 2017-06-04 18:09:46
tags: vuejs javascript intro
---

# Hello world!!!...from Vuejs 
# ![](https://avatars1.githubusercontent.com/u/6128107?v=3&s=30)

## Preamble:

Coming from a .net backend, i have a very limited experience using front-end javascript, libraries and frameworks. Aside from the obvious jQuery knowledge that comes out of the box with MVC/Rails/Django legacy apps, for the past 10 years, my experience with javascript has been a considerable broken mess, creating tons of spaghetti code and hacks. [jQuery](https://jquery.com/) did open the door for a lot of people to a succint Api that had more cohesion than its usage. Selectors and DOM manipulation made the library sometimes a cryptic jumble.

## First try, AngularJs:

I started looking at [Angularjs](https://angularjs.org/) on version 1.X, but i remained rather unconvinced. Most of the people who i knew talked about how awesome it was, using the DOM manipulation and two way binding technique to magically fill your models without the need to physically update each field and keep track of it all. It gave me familiar concepts like controllers and dependency injection. All in one neatly wrapped SPA, that would issue requests for data when needed, while also forcing the user to organize its code in a more structural approach. Components wasnt still such a huge topic as today, so reusability was not that paramount. 

While i started learning, i quickly noticed 2 things:

1. There is a lot of magic happening behind the scenes. This gaved me pause, javascript is not a language to trust. 
2. While libraries required some sprinkle here or there without being too invasive, a js framework requires a full fledge discipline, a custom (separate) build system and even a different mental approach.

While im sure it has their plus, and i really feel angular is doing great, i always thought the entry barrier was too high, especially for teams.

I started using Yeoman at home, and doing some sample apps, mostly silly CRUD to explore a bit of the API. After a few months of back and forth i remained rather unconvined, ive also heard from friends about the bad experiences scaling Angular, discovering issues with 2 way data binding and above all, find it that they would fight the Fx more than felt guided by it.

## Lets try some React:

Last year, after finally getting some time i started looking into React. Although i am not a fan of Facebook and their philosophy, i wont go all political on it. Suffice to say, React is more of a library instead of a complete framework, and so it is way lighter in terms of size. It also, doesnt focus on the whole MVVM/MVC pattern, instead opting to focus on the View scope. I read a few articles and decided to simply try a simple hellow world:

``` html
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Hello React.js</title>
</head>
<body>
    <script src="https://fb.me/react-15.1.0.js"></script>
    <script src="https://fb.me/react-dom-15.1.0.js"></script>
    <div id="app">
    </div>
</body>
</html>
```
So far, so good right? And then...

``` jsx
ReactDOM.render(
  <p>Hello World!</p>,
  document.getElementById('app')
);
```

My first reaction was, what is going on here?! Am i supposed to use that weird looking syntax all the time? I sort of dislike this idea that writing more symbols in our code makes it somehow more verbose, hence my love with a language like F#, who is so expressive while being terse. After researching a bit more with regards to the JSX syntax and using Babel, transpilers and this whole world of crazy loaders, i stood back a bit. Of course i know you could use React without Jsx, but the syntax seems hard for debugging:

``` javascript
const e = React.createElement;

ReactDOM.render(
  e('div', null, 'Hello World'),
  document.getElementById('app')
);
```

I guess JSX is a neat workaround to the limitation of wanting to do html in your javascript. Interestingly enough, most of the examples i find on the web are using JSX, which gave me pause, i am after all a noob, i could really use well thought of examples and some grasp of some of the more novelty concepts. I was rather dissapointed in React , but it introduced very important ideas, especially on the whole Flux architecture with state management. Big js web apps wont get such a performance penalty (which used to happen with angularjs). I watched from afar for a few months, thinking if i should invest time or not.

## Vue

Around Winter last year, A friend of mine was telling me about this newest javascript lib, this was after all not new...[see here](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f?gi=aab94dafd93), but suffice to say i was curious simply because the hello world sample seem so simplistic:


``` html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.3/vue.js"></script>
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
<div id="app">
  <p>{{ message }}</p>
</div>
</body>
</html>
```

And the javascript:

``` javascript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello World!'
  }
})
```

My first thought was, i dont need any transpilers or loaders! This probably means the library is trivial for usage. Then i started checking some examples, Heres a sample from the vuejs.org site:

``` html
<div id="el"></div>

<!-- using string template here to work around HTML <option> placement restriction -->
<script type="text/x-template" id="demo-template">
  <div>
    <p>Selected: {{ selected }}</p>
    <select2 :options="options" v-model="selected">
      <option disabled value="0">Select one</option>
    </select2>
  </div>
</script>

<script type="text/x-template" id="select2-template">
  <select>
    <slot></slot>
  </select>
</script>
```

``` javascript
Vue.component('select2', {
  props: ['options', 'value'],
  template: '#select2-template',
  mounted: function () {
    var vm = this
    $(this.$el)
      // init select2
      .select2({ data: this.options })
      .val(this.value)
      .trigger('change')
      // emit event on change.
      .on('change', function () {
        vm.$emit('input', this.value)
      })
  },
  watch: {
    value: function (value) {
      // update value
      $(this.$el).val(value).trigger('change');
    },
    options: function (options) {
      // update options
      $(this.$el).select2({ data: options })
    }
  },
  destroyed: function () {
    $(this.$el).off().select2('destroy')
  }
})

var vm = new Vue({
  el: '#el',
  template: '#demo-template',
  data: {
    selected: 2,
    options: [
      { id: 1, text: 'Hello' },
      { id: 2, text: 'World' }
    ]
  }
});
```

I was somewhat familiar with angular's directives, therefore the v- directives felt like a "standard". But the javascript really caught my eye, the declarative approach has this simplicity that i wasnt accustomed to in other javascript libraries. Its brief, which helps it a lot. It sure looks like it does a lot of magic, but in truth, once you read what does each declaration does, you get a sense of how it scopes the components and the DOM that it generates. After making some demos using the vue-cli i discovered that for BIG apps, Vue has already a go to way on how to handle separation of snippets of html. Heres a sample .vue file:

 ``` html
 <template>
  <div class="hello">
    <el-row :gutter="20">
      <el-col :span="4">
        <el-input placeholder="Please input"
                  v-model="input"></el-input>
      </el-col>
      <el-col :span="2">
        <el-button type="primary">Default Button</el-button>
        <div class="grid-content"></div>
      </el-col>
      <el-col :span="6">
        <div class="grid-content"></div>
      </el-col>
      <el-col :span="6">
        <div class="grid-content"></div>
      </el-col>
    </el-row>
  </div>
</template>
```
``` javascript
<script>
export default {
  name: 'hello',
  data() {
    return {
      input: ''
    }
  }
}
</script>
```
``` css
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
 ```

 (Imagine this is all one .vue file altogether, more info here -> [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)).  These files have some neat abilities like scoping your css per component or also allowing you to use different syntax templates. 

 ## Going Forward

 So after almost a year of dabbling with javascript front end fx and libraries, my initial plan is to go full fledge on using Vue as basically a gateway library and see how it goes from there in terms of the comparison with React. So far, i see no reason to use React over Vue, even though i am completely aware that React has a LOT of custom components on Github. 


 ### Angular 2...ermm

 As a footnote, i thought i should include that since i dont plan on creating big apps, i always thought Angular 2 was out of the question. I do find Typescript very appealing, but at best is just too much ceremony to simply make an app for me. Im sure big teams will have usability for it, but for smaller teams i just dont feel the need to punish us with so much complexity.