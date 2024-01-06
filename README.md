# LetItRust
Some thoughts on Rust, or not Rust

# Intro
This article wraps up my experience in Rust after having tried it during 2023.
I'm practical, I want things to happen, I want to produce code that does something
and have no patience with theoretical discussions. That's how I judge different
programming languages and software tool in general. I hate fluffy text, so this
will be compact!

# Rust Pros
I really liked some of the ideas about Rust, so I gave it a chance.
- Compact names (but see Cons also!)
  `pub` means __public__, , `fn` means __function__ and so on. Short names mean
  you don't have to put three or four displays next to each other just to
  read the source code!
- The compiler catches lots of errors instead of letting them become
  runtime errors. Good idea!
- Everything are constants, unless you declare it `mut`!
- Documentation rules are well defined and can be easily generated with the
  Rust God _cargo_, and it even checks your documentation before accepting it.
- There's no need for garbage collection because anything can only have one
  owner at a given time.
- Numerical types are distinct - there's no question how many bit's you intend
  to use for a variable declared `u16` or `i32`!
- You can have a comma after the last element declaration in a `struct`.
- Most syntax is the same as in languages you know. Blocks still start with
  `{` and end with `}`.
- There's no `NULL`. You have to learn how to handle `None`, `if let Some()` et al,
  which is doable (compared to lifetimes).

  
# Rust Cons
- You can't switch your team into starting coding in Rust. You won't be able to
  find enough good Rust developers. You could of course give them regular training but
  that will delay your project and Rust will change so quickly (since it's still
  immature) so what they learn now won't be applicable tomorrow. Your code base will
  always be old.
- Some things are not very elegant, such as the `Option` specifiers. What's wrong
  with `Opt` or just `?` as in TypeScript?
- Stupid extra declarations. Suppose you want to declare a function `myfunc` that
  takes a lifetime specifier `y` for the parameter `x`. Then you must declare `<'y>`
  at the end of the function name like this `fn myfunc<'y>(x:&'y Mytype<'y>)`.
  How hard can it be for the compiler to figure out that there's a `y` lifetime in
  the parameter block?
- `String` vs `&str` - Just make my day! Add syntactic sugar or whatever, just don't
  have two string types!
- You can never get a make-my-day answer to your question in a Rust forum. You
  ask a simple question, but get kilometers of theoretical explanations in response.
  Yes, I know they mean well. They are trying to explain the theory behind it.
  But useful languages simple shouldn't expect you to read a bible just to get
  through ordinary and common issues. C has this issue with memory allocation
  which is a bitch - but that's all. This is a fart in the galaxy compared to
  what you also have to grasp to become a Rust Priest. Well, maybe if you can
  waste tax payers money or are doing time it might be an option to read it,
  but most people are busy.
- Strange declarations such as `#derive(Debug, Default)]` etc. If the compiler can
  advice you to add these declarations anyway, why aren't they automatically
  implemented so you don't need to bother?
- Entanglement: You make a function e1() and it works. You make function e2() and
  it also works. But when you call function e2() after e1(), all hell breaks lose
  and you have to spend hours getting it right.
- Silly long sequences of shit like `return self.desc.as_ref().unwrap().to_string();`.
  Hey, come on!
- According to [polls](https://survey.stackoverflow.co/2023/#section-admired-and-desired-programming-scripting-and-markup-languages),
  Rust has become a very popular and admired programming language.
  But why? Very few job ads ask for Rust developers. So I wonder - has Rust become a
  religion only understood by some higher priests? If so, keep me out of it! At
  least until it has matured enough.

# My verdict
If you're a normal company with a limited budget, just don't care about Rust!
At least for now.

# The Future
So it's pretty clear what's going to happen:
- Some Universities will adopt Rust and plague their students with it. They can do
  so becuase they just burn tax payers money.
- Several companies will go bankrupt because they adopted the idea to use Rust, but
  slowed down their development time heavily because they couldn't find enough
  Rust developers and the learning curve for their [already busy and not very
  inspired] developer took too long to learn Rust, and basically used a trial-and-error
  approache to it. Also, to avoid having to deal with lifetime parameters they tried
  to reduce the number of functions, making them very difficult to debug, which
  made testing very difficult and nobody got a good grasp on what the functions
  really did (since they did too many things).
- Technical debt will build up rapidly in many Rust based projects because the
  general rule will be: __Don't touch it if it works!__. And all Rust modules
  will start with `#[allow(unused_imports)]` and `#[allow(unused)]` simply because
  developers were too far behind schedule so they didn't have time to
  consider those nice built-in warnings.
- Someone else will catch the good core ideas about Rust, and cherrypick the good
  stuff out of it, create a much better programming language. But...
- AI will make programming languages less interesting. We will just talk to the
  Ai system and let it take care of the coding. And, while we're at it - talking,
  not typing, is the future!

  
