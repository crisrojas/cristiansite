### 1. Things pull to search

#swiftui

<video controls autoplay muted loop playsinline>
	<source src="media/2023-28-01-pull-to-refresh-things.mov" type="video/mp4">
</video>

Things I learned:

- ScrollView is very limited and doesn't allow tracking of any useful event
- Correctly wrap an `UIScrollView` in a *representable*
- Create swift alike modifiers that return the view à la Swift: `ScrollRepresentable().onLift { _ in }`