source "https://rubygems.org"

# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
gem "jekyll", "~> 3.9.5"

# This is the default theme for new Jekyll sites. You may change this to anything you like.
gem "minima", "~> 2.5.1"

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
# gem "github-pages", group: :jekyll_plugins

# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "jekyll-admin", "~> 0.11.1"
  gem "jekyll-compose", "~> 0.12.0"
  gem "jekyll-feed", "~> 0.17.0"
  gem "jekyll-seo-tag", "~> 2.8.0"
  gem "jekyll-sitemap", "~> 1.4.0"
end

# kramdown 2.x split the GFM input parser into its own gem; Jekyll's default
# `markdown: kramdown` config still expects GFM, so we have to require it explicitly.
gem "kramdown-parser-gfm", "~> 1.1"

# Pin ffi to the last release that still supports Ruby 2.6 (newer ffi requires Ruby >= 3).
gem "ffi", "~> 1.16.3"

# jekyll-admin 0.11.1 monkey-patches `Rack::Handler::WEBrick`, which was removed
# in Rack 3.x. Pin Rack to 2.x (and Sinatra to 3.x, since Sinatra 4 hard-requires
# Rack 3) so `bundle exec jekyll serve` keeps working.
gem "rack", "~> 3.2"
gem "sinatra", "~> 4.2"
gem "sinatra-contrib", "~> 4.2"

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.0" if Gem.win_platform?
