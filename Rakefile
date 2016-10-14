# coding: utf-8
#
# das ist für org-mode system
require 'jekyll'
require 'rubygems'
require 'time'
require 'rake'
require 'yaml'

# config # {{{
SOURCE = "."
CONFIG = {
  'posts' => File.join(SOURCE, "_posts"),
  'orgposts' => File.join(SOURCE, "org/_posts/"),
  'orgpost_ext' => "org",
  'post_ext' => "md"
}
# }}}

# create a new org-mode doc# {{{
# useage: "rake orgpost"
desc "Create a new org-mode doc in #{CONFIG['org-mode-posts']}"
task :orgpost, :title do |t, args|
  abort("rake aborted: '#{CONFIG['orgposts']}' directory not found.") unless FileTest.directory?(CONFIG['orgposts'])
  if args.title
    title = args.title
  else
    title = get_stdin("Enter a title for your org-mode post: ")
  end
#  title = ENV["title"] || "new-post"
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  begin
    date = (ENV['date'] ? Time.parse(ENV['date']) : Time.now).strftime('%Y-%m-%d')
  end
  filename = File.join(CONFIG['orgposts'], "#{date}-#{slug}.#{CONFIG['orgpost_ext']}")
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end

  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "\#\+TITLE:#{title.gsub(/-/, ' ')}"
    post.puts "\#\+OPTIONS: toc:nil"
    post.puts "\#\+STARTUP: showall indent"
    post.puts "\#\+STARTUP: hidestars"
    post.puts "\#\+BEGIN_HTML"
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: #{title}"
    post.puts "subtitle: "
    post.puts "date: #{date}"
    post.puts "author: hugohoover"
    post.puts "---"
    post.puts "\#\+END_HTML"

  end
end # task :orgpost
# }}}

# create a new frontend post # {{{
# useage: "rake post"
desc "Create a new post in #{CONFIG['posts']}"
task :post, :title do |t, args|
  abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
  if args.title
    title = args.title
  else
    title = get_stdin("Enter a title for your post: ")
  end
#  title = ENV["title"] || "new-post"
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  begin
    date = (ENV['date'] ? Time.parse(ENV['date']) : Time.now).strftime('%Y-%m-%d')
  end
  filename = File.join(CONFIG['posts'], "#{date}-#{slug}.#{CONFIG['post_ext']}")
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end

  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: #{title}"
    post.puts "subtitle: "
    post.puts "date: #{date}"
    post.puts "author: hugohoover"
    post.puts "---"
  end
end # task :post
# }}}

# definitions # {{{
def ask(message, valid_options)
  if valid_options
    answer = get_stdin("#{message} #{valid_options.to_s.gsub(/"/, '').gsub(/,/, '/')}") while !valid_options.include?(answer)
  else
    answer = get_stdin(message)
  end
  answer
end

def get_stdin(message)
  print message
  STDIN.gets.chomp
end
# }}}

#Load custom rake scripts
Dir['_rake/*.rake'].each { |r| load r }
