Basic examples demonstrating Plutarch usage.

> Note: If you spot any mistakes/have any related questions that this guide lacks the answer to, please don't hesitate to raise an issue. The goal is to have high quality documentation for Plutarch users!

> Aside: Be sure to check out [Compiling and Running](./../GUIDE.md#compiling-and-running) first!

# Fibonacci number at given index

```hs
import Plutarch.Prelude

fib :: Term s (PInteger :--> PInteger)
fib = phoistAcyclic $
  pfix #$ plam $ \self n ->
    pif
      (n #== 0)
      0
      $ pif
        (n #== 1)
        1
        $ self # (n - 1) + self # (n - 2)
```

from [examples](https://github.com/Plutonomicon/plutarch/tree/master/plutarch-test).

Execution:

```hs
> evalT $ fib # 2
Right (Program () (Version () 1 0 0) (Constant () (Some (ValueOf integer 2))))
```
