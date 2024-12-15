# Quick and dirty notes on [learnyouahaskell](https://learnyouahaskell.com)

## 8 Making Our Own Types and Typeclasses 

### The Functor Typeclass

A functor is a typeclass which describe other typeclasses (not concrete types!) whose values can transformed into other values.

The definition looks like this:
```
class Functor f where
  fmap :: (a -> b) -> f a -> f b
```

And some example implementations:
```
instance Functor [] where
  fmap = map

instance Functor Maybe where
  fmap f (Just x) = Just (f x)
  fmap f Nothing = Nothing

instance Functor (Either a) where
  fmap f (Right x) = Right (f x)
  fmap f (Left x) = Lef x
```

Its up to use to make our own typeclasses functors and define them in reasonable ways.
We just to have to massage our typeclass to something where we just change of the types inside it.

### Kinds and some type-foo

Just like functions can have signatures (like `Int -> Int`), so too can typeclasses.
They are called kinds and can be inspected using `:k` (a `*` simply means its a concrete type in the output).
In the example below, we can see that an `Int` simply is a concrete type, while `Maybe` is typeclass which takes one concrete type and produces another concrete type.
Typeclasses can be curried, just like regular functions.

```
ghci> :k Int
Int :: *

ghci> :k Maybe
Maybe :: * -> *
ghci> :k Maybe Int
Maybe Int :: *

ghci> :t isUpper
Char -> Bool
ghci> :t isUpper 'A'
Bool

ghci> :k isUpper
*
ghci> :k isUpper 'A'
*

```
