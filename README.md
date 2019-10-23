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
      
      ._(() => 0.073)
      
    )
}
```
