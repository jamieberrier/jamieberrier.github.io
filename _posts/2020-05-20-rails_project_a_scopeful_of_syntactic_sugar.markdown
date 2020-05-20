---
layout: post
title:      "Rails Project – A 'Scope'ful of Syntactic Sugar"
date:       2020-05-20 21:39:38 +0000
permalink:  rails_project_a_scopeful_of_syntactic_sugar
---

A scope is a custom query defined inside a model and is available as a class method…basically ‘syntactic sugar’ for defining a class method. A scope uses a lambda, which re-evaluates the scope each time it is called and guarantees it will return an ActiveRecord::Relation object. 

But what is a lambda?  

*Anyone else immediately think of ‘Revenge of the Nerds’? The Lambda Lambda Lambda fraternity? No? Just me?*

A lambda is an object that represents a block and has method-like behavior. By wrapping the logic and data in a lambda, a block can be manipulated as an object (e.g. chained). 

In my rails project, there is a `DanceStudio` model that `has_many :dancers` and a `Dancer` model that `belongs_to :dance_studio`, with a boolean field `current_dancer`.  

To display all of the current dancers at a dance studio, I could define a class method:

```
def self.current_dancers(dance_studio)
  where("dance_studio_id = '%s' and current_dancer = '%s'", dance_studio.id, 1)
end
```

But, a spoonful of syntactic sugar helps define a scope:
```
scope :current_dancers, lambda { |dance_studio| where("dance_studio_id = '%s' and current_dancer = '%s'", dance_studio.id, 1) }
```

The literal lambda operator, aka ‘stabby lambda’ syntax, can also be used:
```
scope :current_dancers, ->(dance_studio) { where("dance_studio_id = '%s' and current_dancer = '%s'", dance_studio.id, 1) }
```
With either syntax, the method call is the same:
```
Dancer.current_dancers(@dance_studio)
```
But wait! There's more!  

**Scopes are also available to has_many associations!**

Since the `DanceStudio` model `has_many :dancers`, the scope can be sweetened further to:
```
scope :current_dancers, -> { where(current_dancer: 1) }
```
Now, the method call is:
```
@dance_studio.dancers.current_dancers
```
![](https://media.giphy.com/media/BW5OaeGBHVBf2/giphy.gif)  
*In a most delightful way!*


