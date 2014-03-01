task :publish, [:comment]  do |t, args|
  `git add . && git ci -am "#{args[:comment]}"` 
  `bundle exec middleman build && cp -r build/* ../warmwind.github.io/ && git ci -am "#{args[:comment]}" && git push`
end
