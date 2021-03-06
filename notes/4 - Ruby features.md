HoundCI
=======
# Ruby features
## Array

```
arr = [1,2,3,4,5,6]
```
===
```
arr.first #=> 1
arr.take(3) #=> [1, 2, 3]

arr.last  #=> 6
arr.drop(3) #=> [4, 5, 6]
```
===
```
arr.size # => 4
arr.length # => 4
arr.count # => 4
```
===
```
arr.empty?
```
===
```
arr.push
arr.pop

arr.shift
arr.unshift
```
===
```
arr.compact
arr.uniq
arr.reverse
arr.rotate 3
arr.sample
arr.shuffle
arr.slice => [1..2]
arr.sort
arr.transpose [[1,2], [3,4], [5,6]]
```
===
```
arr.each
arr.reverse_each
```
===
```
arr.map

arr.select
arr.keep_if

arr.reject
arr.delete_if
```
===
```
* operation

arr * 4
arr * ' '
```
===
```
arr + [10]
arr - [1]
arr << 10
arr << [10]
arr == [1,2,3,4,5,6]
```
===
```
arr.bsearch { }
```
===
```
arr.combination(2)
arr.repeated_combintion(2)
arr.permutation(3)
arr.repeated_permutation(2)
arr.product [7,8], [9,10]

arr.cycle(?3)
```
===
```
arr.fetch(3) { |i| 10 }
arr.fill 10, 1..3
```
===
```
arr.flatten
```

## Enumerable
===
```
arr.all?
arr.any?
```
===
```
[3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5].chunk { |n|
  n.even?
}.each { |even, ary|
  p [even, ary]
}
```
===
```
arr.each_slice(2) {}
arr.each_slice(2).to_a #enumerator to array
arr.each_with_index
```

## Range
```
range = 1..4
arr = (1..6).to_a
arr = (1...6).to_a
range.include? 3
```

## Complex
```
Complex(0.3)         #=> (0.3+0i)
Complex('0.3-0.5i')  #=> (0.3-0.5i)
Complex('2/3+3/4i')  #=> ((2/3)+(3/4)*i)
Complex('1@2')       #=> (-0.4161468365471424+0.9092974268256817i)

0.3.to_c             #=> (0.3+0i)
'0.3-0.5i'.to_c      #=> (0.3-0.5i)
'2/3+3/4i'.to_c      #=> ((2/3)+(3/4)*i)
'1@2'.to_c           #=> (-0.4161468365471424+0.9092974268256817i)
```

## Dir
```
Dir.chdir("/var/spool/mail")
puts Dir.pwd
Dir.chdir("/tmp") do
  puts Dir.pwd
  Dir.chdir("/usr") do
    puts Dir.pwd
  end
  puts Dir.pwd
end
puts Dir.pwd

Dir.foreach("testdir") {|x| puts "Got #{x}" }
```
===
```
Dir["config.?"]                     #=> ["config.h"]
Dir.glob("config.?")                #=> ["config.h"]
Dir.glob("*.[a-z][a-z]")            #=> ["main.rb"]
Dir.glob("*.[^r]*")                 #=> ["config.h"]
Dir.glob("*.{rb,h}")                #=> ["main.rb", "config.h"]
Dir.glob("*")                       #=> ["config.h", "main.rb"]
```
===
```
Dir.mkdir(File.join(Dir.home, ".foo"), 0700) #=> 0
```

## ENV
```
export MYVAR=123
irb
ENV['MYVAR']
```

## File
```
File.absolute_path("~oracle/bin")
File.atime("testfile")
File.basename("/home/gumby/work/ruby.rb")
File.ctime("testfile")
File.directory?(file_name)
File.file?(file_name)
File.exists?(file_name)
```
## Hash
```
h = {a: 1, b: 2}
h.keys
h.values
h.each_pair
```

## Benchmark
```
require 'benchmark'
include Benchmark          # we need the CAPTION and FORMAT constants

n = 50000
Benchmark.benchmark(CAPTION, 7, FORMAT, ">total:", ">avg:") do |x|
  tf = x.report("for:")   { for i in 1..n; a = "1"; end }
  tt = x.report("times:") { n.times do   ; a = "1"; end }
  tu = x.report("upto:")  { 1.upto(n) do ; a = "1"; end }
  [tf+tt+tu, (tf+tt+tu)/3]
end
```

```
require 'benchmark'

array = (1..1000000).map { rand }

Benchmark.bmbm do |x|
  x.report("sort!") { array.dup.sort! }
  x.report("sort")  { array.dup.sort  }
end
```

## Math and CMath
Provide functions for real and comples numbers respectively.

## CSV
```
require 'csv'

csv_string = CSV.generate do |csv|
  csv << [1,2,3]
  csv << ['he','she','OHO']
  csv << [:do, :not, :know]
end
File.open('test.txt', 'w') { |f| f << csv_string }
```
===
```
CSV.foreach("path/to/file.csv") do |row|
  p row
end
```
===
```
CSV.parse("Class,Module,Object") do |row|
  p row
end
```

# Conclusion
1. Change your mind! You should think about logic not about implementation.
2. Write with the help of the language not using the language!
3. Have fun!
>>>>>>> 18a6db32ffdff8bc58f27161a680c4cf7c537428
