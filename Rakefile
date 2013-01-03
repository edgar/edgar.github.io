require 'rubygems'
require 'rake'

task :default => 'server:auto'

# Default site deploy to staging
@folder = 'vp.com.ve:/home/odin/public_html/edgar.staging'

desc "Set site deployment to production environment (folder)"
task :production do
  @folder = 'vp.com.ve:/home/odin/public_html/edgar'
end

namespace :site do
  task :deploy do
    exec("jekyll && rsync -avz --delete _site/ odin@#{@folder}")
  end
end

namespace :server do
  desc "Starts the server with autobuild enabled"
  task :auto do
    exec('jekyll --server --auto')
  end
end

