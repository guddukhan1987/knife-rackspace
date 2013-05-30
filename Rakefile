#
# Author:: Adam Jacob (<adam@opscode.com>)
# Author:: Daniel DeLeo (<dan@opscode.com>)
# Copyright:: Copyright (c) 2008, 2010 Opscode, Inc.
# License:: Apache License, Version 2.0
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

require 'bundler'
Bundler::GemHelper.install_tasks

require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec)
task :default => [:spec, 'integration:live']

namespace :integration do
  desc 'Run the integration tests'
  RSpec::Core::RakeTask.new(:test) do |t|
    t.pattern = 'spec/integration/**'
  end

  desc 'Run the integration tests live (no VCR cassettes)'
  task :live do
    ENV['INTEGRATION_TESTS'] = 'live'
    Rake::Task['integration:test'].invoke
  end
end