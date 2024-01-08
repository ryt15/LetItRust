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
- `String` vs `&str` vs ... - Just make my day! Add syntactic sugar or whatever,
  just don't have several different string types!
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
- Compilers for most decent programming languages give you one error message and a line
  number. But in Rust, one and the same problem is related to many different lines
  in the code, combined with cryptic error messages. This makes it difficult to know
  where to start. If you also have a tight schedule, trying to fix the bug becomes
  a nightmare. Should you ask for advice, you most likely get a link to a chapter
  in the Rust documentation which feels very unrelated to the actual bug (see below).
- According to [polls](https://survey.stackoverflow.co/2023/#section-admired-and-desired-programming-scripting-and-markup-languages),
  Rust has become a very popular and admired programming language.
  But why? Very few job ads ask for Rust developers. So I wonder - has Rust become a
  religion only understood by some higher priests? If so, keep me out of it! At
  least until it has matured enough.

# Rust Compiler Example
```rust
   Compiling fig02 v0.1.0 (/home/salfor/lab/rust/fig02)
error[E0505]: cannot move out of `design` because it is borrowed
   --> src/product.rs:703:9
    |
609 | ...ub fn build_design_lists<'a>(main_documents:&Vec<MainDocument>,
    |                             -- lifetime `'a` defined here
...
617 | ...   let mut design = Design::default();
    |           ---------- binding `design` declared here
...
687 | ...      let fill_nodes: &HashMap<String, FillNode> = design.style_fills.as_ref().un...
    |                                                       --------------------------- borrow of `design.style_fills` occurs here
...
703 | ...   design
    |       ^^^^^^
    |       |
    |       move out of `design` occurs here
    |       returning this value requires that `design.style_fills` is borrowed for `'a`

error[E0515]: cannot return value referencing local data `design.style_fills`
   --> src/product.rs:703:9
    |
687 | ...      let fill_nodes: &HashMap<String, FillNode> = design.style_fills.as_ref().un...
    |                                                       --------------------------- `design.style_fills` is borrowed here
...
703 | ...   design
    |       ^^^^^^ returns a value referencing data owned by the current function

Some errors have detailed explanations: E0505, E0515.
For more information about an error, try `rustc --explain E0505`.
error: could not compile `fig02` (lib) due to 2 previous errors
```

# My Verdict
If you're a normal company with a limited budget, just don't care about Rust!
__Wait__ until Rust has matured, and the fanatics are gone, replaced by
decent easy-to-find developers demanding normal salaries, before you allow
Rust into your software environment. Or - use another programming language
which has adopted some of the good parts from Rust, skipping the bad ones.

# The Future
So it's pretty clear what's going to happen:
- Some Universities will adopt Rust and plague their students with it. They can do
  so because they just burn tax payers money, not their own.
- Several companies will go bankrupt because they adopted Rust too early, which
  slowed down their development time heavily because they couldn't find enough
  Rust developers and the learning curve for their (already busy and not very
  inspired) developer took too long to learn Rust.
- Developers forced to maintain Rust before being experts in it, would probably
  take on a trial-and-error approach. And to avoid dealing with
  scary lifetime parameters, they would try to reduce the number of functions.
  This results in large functions that are very difficult to debug, understand,
  test and maintain. In other words - technical debt is built up quickly and in
  the end you might have to rewrite the entire code base in some other language!
- Someone else will cherry pick the good core ideas about Rust, and develop
  a much better programming language. But...
- AI will make programming languages less interesting. We will just talk to the
  AI, letting it do the coding. And, while we're at it - talking,
  not typing, is the future!

# Final Conclusion
Rust risks becoming a very __expensive__ programming language if "rustaceans" manage
to trick software companies adopting it - and they can be very convincing!
They will maintain that Rust is fast and safe, and other programming languages
contain many undiscovered bugs that are hard and time consuming to iron out. I
agree to some extent - but what other costs does Rust bring?
- __Rust developers are rare__, so they become expensive and critical __bottle-necks__.
- Since Rust is still in development, you __regularly need to upgrade__ the code, and
  put aside time to learn the new versions, which also adds expenses and delays.
- If you don't have time to catch up with recent versions of Rust, __security
  holes__ will linger in your code without being patched. And the longer you wait
  before upgrading, the harder will it be to catch up. Most developers want to
  create new code, not poke around in old, unless you really pay them well.
- Since it takes so long time to develop code in Rust, your product will hit the
  market late. Definitely __not an option for startups__!
- If universities adopt it, it will be yet another expense for tax payers.
- Be aware! Rust risks becoming a __Trojan horse__ if allowed inside your project!
