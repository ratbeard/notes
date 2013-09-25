

		.data(array, keyFn)

Default keyFn is to compare based on index.  Instead an identity function or a more
complex mapping function is needed.

Basic form:

		points = container.selectAll("circle")
			.data(data, (d) -> d)

		points.enter()
			.append("circle")
			.attr(cx: ...)

		points.exit().remove()
			

http://knowledgestockpile.blogspot.com/2012/01/understanding-selectall-data-enter.html

