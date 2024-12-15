# Quick and dirty notes on [learnyouahaskell](https://learnyouahaskell.com)

## 8 Making Our Own Types and Typeclasses 

### The Functor Typeclass

A functor is a typeclass which describe other typeclasses (not concrete types!) whose values can transformed into other values.

The definition looks like this:
```
class Functor f where
  fmap :: (a -> b) -> f a -> f b
```

An some example implementations:
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
