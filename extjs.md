Ext.JS
=

##+ Estrutura de um arquivo de view

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

##+ Herança de componentes visuais
```javascript
- AppExemplo
  |_ model
  |_ view
    |_ pessoas
      |_ Combo.js
      |_ SistemasCombo.js
    |_ compras
      |_ PessoasCombo.js
      |_ SistemasCombo.js
```

######Quando compras.PessoasCombo.js tem o mesmo comportamento de pessoas.Combo.js, com pequenas individualidades
```javascript
//Herda do componente base[#5]
Ext.define("AppExemplo.view.compras.PessoasCombo", {
  extend: 'AppExemplo.view.pessoas.Combo',
  alias: ['widget.compraspessoascombo']
  .
  .
  .
});
```

#####Quando compras.SistemasCombo.js tem o mesmo comportamento de pessoas.SistemasCombo.js, com pequenas individualidades, porém SistemasCombo é de outra natureza
```javascript
- AppExemplo
  |_ model
  |_ view
    |_ common
      |_ SistemasCombo.js
    |_ pessoas
      |_ Combo.js
      |_ SistemasCombo.js
    |_ compras
      |_ PessoasCombo.js
      |_ SistemasCombo.js
      
//Extrai o componente base para o pacote common[#5]
Ext.define("AppExemplo.view.common.SistemasCombo", {
  extend: 'Ext.combo.Combo',
  alias: ['widget.commonsistemascombo']
  .
  .
  .
});

//Implementa as particularidades e herda do componente base[#5]
Ext.define("AppExemplo.view.pessoas.SistemasCombo", {
  extend: 'AppExemplo.view.common.SistemasCombo',
  alias: ['widget.pessoassistemascombo']
  .
  .
  .
});

//Implementa as particularidades e herda do componente base[#5]
Ext.define("AppExemplo.view.compras.SistemasCombo", {
  extend: 'AppExemplo.view.common.SistemasCombo',
  alias: ['widget.comprassistemascombo']
  .
  .
  .
});
```
