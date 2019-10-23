more-sugar.js
=============

Mais uma biblioteca de açúcar sintático em JavaScript

## Pattern matching
```js
import {match} from 'more-sugar'

// Ao invés de
function taxRate(totalIncome) {
    if(totalIncome<300){
        return 0
    }
    if(totalIncome<600){
        return 0.03
    }
    if(totalIncome<940){
        return 0.05
    }
    if(totalIncome<1480){
        return 0.065
    }
    return 0.073
}

// Use
function taxRate(totalIncome) {
    return (match
    
      .lt(300,  () => 0)
      .lt(600,  () => 0.03)
      .lt(940,  () => 0.05)
      .lt(1480, () => 0.065)
      
      // Em outro caso
      ._(() => 0.073)
      
    )
}
```

Formas de usar os operadores `match`:
```js
(match

    $operator($value_checker, $value)
    $operator($value_checker, $fn_value)
    $operator($fn_checker,    $value)
    $operator($fn_checker,    $fn_value)
    
    // $value_checker Pode ser um valor ou expressão regular
    // $fn_checker    É um lambda que retorna `true` ou `false`
    // $fn_value      É um lambda que retorna o produto da operação
    // $operator      Um dos:
    // - eq()            # igual a
    // - ne()            # diferente de
    // - ge()            # maior ou igual a
    // - gt()            # maior que
    // - le()            # menor ou igual a
    // - lt()            # menor que
    // - like()          # ...
    // - notlike()       # ...
    // - match(?)        # combina com expressão regular
    // - notmatch()      # não combina com expressão regular
    // - contains()      # ...
    // - notcontains()   # ...
    // - is(?)           # ...
    // - isnot(?)        # ...

)
```
