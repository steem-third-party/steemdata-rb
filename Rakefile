require 'bundler/gem_tasks'
require 'rake/testtask'
# require 'yard'

Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.libs << 'lib'
  t.test_files = FileList['test/**/*_test.rb']
  t.ruby_opts << if ENV['HELL_ENABLED']
    '-W2'
  else
    '-W1'
  end
end

# YARD::Rake::YardocTask.new do |t|
#   t.files = ['lib/**/*.rb']
# end

task default: :test

task :console do
  exec "irb -r steem_data -I ./lib"
end

task :build do
  exec 'gem build steem_data.gemspec'
end

task :push do
  exec "gem push steem_data-#{SteemData::VERSION}.gem"
end

# We're not going to yank on a regular basis, but this is how it's done if you
# really want a task for that for some reason.

# task :yank do
#   exec "gem yank steem_data -v #{SteemData::VERSION}"
# end
