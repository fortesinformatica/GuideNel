Ext.JS
=

##Estrutura de um arquivo de view

```javascript
Ext.define('<NOME_DO_APP_EM_CAMEL_CASE>.view.<PACOTE_EM_MINUSCULO>.<SUBPACOTE_QUANDO_HOUVER_EM_MINUSCULO>.<CLASSE_DO_COMPONENTE_EM_CAMEL_CASE>', {
alias: ['widget.<PACOTE_EM_MINUSCULO><SUBPACOTE_QUANDO_HOUVER_EM_MINUSCULO><CLASSE_DO_COMPONENTE_EM_MINUSCULO>'],

//configurações do componente visual logo abaixo das definições de nome
//width: 520,
//height: 290,
//padding: 10,
//frame: true,

//Items logo após as configurações[#6]
items: [
  {xtype: "aaa"},
  {xtype: "bbb"}
]

//Quando houver[#1]
//logo após as configurações[#7]
buildItems: function() {
  return [{xtype: "xxx"}];
},

//Quando houver[#1]
//logo após as configurações[#7]
buildButtons: function() {
  return [{yyy},{kkk}];
},

//Métodos de negócio ficam na zona intermediária[#7]
processarAlgo: function(){
  fazerAlgo();
},

//Ultimo método da classe (aplica-se o mesmo para o constructor)[#7]
initComponent: function() {
  this.items = this.buildItems();
  this.buttons = this.buildButtons();
  this.callParent();
}
```

##Herança de componentes visuais
se A é um combo de sistemas e B também, só que em outro contexto com suas peculiaridades, ele pode ser extendido sim.
Já para reaproveitar código apenas para remover a duplicação, devemos criar um C com o código similar e tanto A quanto B devem extender C.
