// ==UserScript==
// @name         BingBot
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  bot for Bing
// @author       Vukolov Artem
// @match        https://www.bing.com/*
// @icon         data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==
// @grant        none
// ==/UserScript==

let keywords = ["10 самых популярных шрифтов от Google", "Отключение редакций и ревизий в WordPress", "Вывод произвольных типов записей и полей в WordPress", "Плагины VS Сode. Что помогает в работе с редактором от Microsoft?"];
let keyword = keywords[getRandom(0, keywords.length)];
let search = document.getElementsByName("search")[0];
let links = document.links;

if (search !== undefined) {
  document.getElementsByName("q")[0].value = keyword;
  search.click();
} else {

  for (let i = 0; i < links.length; i++) {
    if (links[i].href.indexOf("napli.ru") !== -1) {
      let link = links[i];
      console.log("Нашел строку " + link);
      link.click();
      break;
    }
  }
}


function getRandom(min, max) {
  return Math.floor(Math.random()*(max - min) + min);
} 
