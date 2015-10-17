# http://arjanvandergaag.nl/blog/creating-new-jekyll-posts.html
# usage: rake draft t="Dei. Dei."

require 'date'

desc 'create a new draft post'
task :draft do
  title = ENV['t']
  slug = "#{Date.today}-#{title.downcase.gsub(/[^\w]+/, '-')}"

  file = File.join(
    File.dirname(__FILE__),
    '_posts',
    slug + '.markdown'
  )

  File.open(file, "w") do |f|
    f << <<-EOS.gsub(/^    /, '')
    ---
    layout: post
    title: #{title}
    published: false
    categories:
    ---

    EOS
  end

  system ("#{ENV['EDITOR']} #{file}")
end
