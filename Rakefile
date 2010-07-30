require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "edgar.gonzalez.net.ve"
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

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

#  begin
#    require 'watchr'
#    namespace :auto do
#      desc "Automatically deploy to staging when a change is detected in any file"
#      task :deploy do |watch|
#        system 'watchr .watchr/deploy.rb'
#      end
#    end
#  rescue LoadError
#    abort "Watchr is not available. In order to run watchr, execute: $ sudo gem install watchr"
#  end

end

namespace :server do

  desc "Starts the server with autobuild enabled"
  task :auto do
    exec('jekyll --server --auto')
  end

end

