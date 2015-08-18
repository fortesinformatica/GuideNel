Ruby
=
##Indentação de métodos aninhados [[#4]](https://github.com/fortesinformatica/GuideNel/issues/4)

* com o ponto antes do nome do método e não na linha anterior
* com parâmetros longos quebrados em linhas mais semânticas
```ruby
joins(:admin_grupos)
  .where
    (
      organization_id: current_user.last_organization_logged, 
      admin_grupos: { user_id: current_user.id }
    )
  .order(created_at: :desc)
```

##Relacionamentos many to many 

* Mapeamento [[#3]](https://github.com/fortesinformatica/GuideNel/issues/3)
```ruby
has_and_belongs_to_many: #usado quando NÃO houver necessidade de lógica ou campo adicional
has_many: throug: #usado somente quando houver necessidade de lógica ou campo adicional
```
- - -
* Regras na tabela intermediária [[#2]](https://github.com/fortesinformatica/GuideNel/issues/3)
  * só pode haver regra em tabela intermediário quando envolver campo dessa tabela
  * quando a associação atender, não implementar na intermediária
  

- - -
