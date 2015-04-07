#Ruby

####Array to hash
```
words = key_words.split(',')
words.inject(Hash.new(0)) { |h, w| h[w.strip]+=1 ; h}
words.each_with_object(Hash.new(0)) { |w, h| h[w.strip]+=1 }
```	

Or the array constructor
```
Hash[ExerciseCategory.all.pluck(:id,:name)]
```

####Hash of arrays, inject vs each_with_object
```
projects.inject(Hash.new{|h,k| h[k]=[]}) { |h,p| h[p.client_id] << p.client_id ; h}
projects.each_with_object(Hash.new{|h,k| h[k]=[]}) {|p,h| h[p.client_id] << p.client_id }
```
