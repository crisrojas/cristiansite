Things I learned:

- ScrollView is very limited and doesn't allow tracking of any useful event
- Correctly wrap an `UIScrollView` in a *representable*
- Create swift alike modifiers that return the view à la Swift: `ScrollRepresentable().onLift { _ in }`


[Gist](https://gist.github.com/crisrojas/312b6c823562ee35bf1da98461d8534b)