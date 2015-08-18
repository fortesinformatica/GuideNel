Ruby
=

##Indentação de métodos aninhados## 
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
