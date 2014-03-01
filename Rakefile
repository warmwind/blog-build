task :commit, [:comment]  do |t, args|
  `git add . && git ci -am "#{args[:comment]}" && git push` 
end

task :publish, [:comment] do |t, args|
  `bundle exec middleman build && cp -r build/* ../warmwind.github.io/ && cd ../warmwind.github.io/ && git ci -am "#{args[:comment]}" && git push`
end

task :release, [:comment] => [:commit, :publish] do |t, args|

end