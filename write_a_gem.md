#Make your own gem
1. `bundle gem hola` Create the basic gem skeleton
2. Modify `.gemspec` file as necessary
3. `gem build hola.gemspec` build the gem and try it out (I think this should not be included in the gem itself, so remove it after trying it out)
4. `gem push hola-0.0.0.gem` push the gem
5. Wire a new release in github