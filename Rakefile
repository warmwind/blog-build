task :commit, [:comment]  do |t, args|
  `git add . && git ci -am "#{args[:comment]}" && git push` 
end

task :publish, [:comment] do |t, args|
  `bundle exec middleman build && cp -r build/* ../warmwind.github.io/ && cd ../warmwind.github.io/ && git add . && git add -u && git ci -am "#{args[:comment]}" && git push`
end
