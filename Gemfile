source 'https://rubygems.org'

gemspec

if ENV['AREL']
  gem 'arel', :path => ENV['AREL']
else
  gem 'arel'
end

gem 'bcrypt-ruby', '~> 3.0.0'

if RUBY_VERSION < '1.9.3'
  gem 'jquery-rails', '< 4'
else
  gem 'jquery-rails'
end

if ENV['JOURNEY']
  gem 'journey', :path => ENV['JOURNEY']
else
  gem 'journey'
end

if RUBY_VERSION < '1.9.3'
  gem 'i18n', '~> 0.6.11', '< 0.7'
else
  gem 'i18n', '~> 0.6.11'
end

gem 'test-unit', '~> 3.0.0'

if RUBY_VERSION < '1.9.3'
  gem 'rack-cache', '~> 1.2.0'
end

# This needs to be with require false to avoid
# it being automatically loaded by sprockets
if RUBY_VERSION < '1.9.3'
  gem 'uglifier', '>= 1.0.3', '< 3', :require => false
else
  gem 'uglifier', '>= 1.0.3', :require => false
end

# execjs >= 2.1.0 doesn't work with Ruby 1.8
gem 'execjs', '< 2.1.0'

if RUBY_VERSION < '1.9.3'
  gem 'rake', '>= 0.8.7', '< 11'
else
  gem 'rake', '>= 0.8.7'
end

gem 'mocha', '~> 0.14', :require => false

# group :doc do
#   # The current sdoc cannot generate GitHub links due
#   # to a bug, but the PR that fixes it has been there
#   # for some weeks unapplied. As a temporary solution
#   # this is our own fork with the fix.
#   gem 'sdoc',  :git => 'git://github.com/fxn/sdoc.git'
#   gem 'RedCloth', '~> 4.2'
#   gem 'w3c_validators'
# end

# AS
gem 'memcache-client', '>= 1.8.5'

platforms :mri_18 do
  gem 'system_timer'
  gem 'json'
end

# Add your own local bundler stuff
instance_eval File.read '.Gemfile' if File.exists? '.Gemfile'

platforms :mri do
  group :test do
    gem 'ruby-prof', '~> 0.11.2' if RUBY_VERSION < '2.0'
  end
end

platforms :ruby do
  gem 'yajl-ruby'
  gem 'nokogiri', '>= 1.4.5', '< 1.6'

  # AR
  # gem 'sqlite3', '~> 1.3.5'

  group :db do
    if RUBY_VERSION < '1.9.3'
      gem 'pg', '>= 0.11.0', '< 0.18'
    else
      gem 'pg', '>= 0.11.0'
    end
    # gem 'mysql', '>= 2.8.1'
    # gem 'mysql2', '~> 0.3.10'
  end
end

platforms :jruby do
  gem 'json'
  gem 'activerecord-jdbcsqlite3-adapter', '>= 1.2.7'

  # This is needed by now to let tests work on JRuby
  # TODO: When the JRuby guys merge jruby-openssl in
  # jruby this will be removed
  gem 'jruby-openssl'

  group :db do
    gem 'activerecord-jdbcmysql-adapter', '>= 1.2.7'
    gem 'activerecord-jdbcpostgresql-adapter', '>= 1.2.7'
  end
end

# gems that are necessary for ActiveRecord tests with Oracle database
if ENV['ORACLE_ENHANCED_PATH'] || ENV['ORACLE_ENHANCED']
  platforms :ruby do
    gem 'ruby-oci8', '>= 2.0.4'
  end
  if ENV['ORACLE_ENHANCED_PATH']
    gem 'activerecord-oracle_enhanced-adapter', :path => ENV['ORACLE_ENHANCED_PATH']
  else
    gem 'activerecord-oracle_enhanced-adapter', :git => 'git://github.com/rsim/oracle-enhanced.git'
  end
end

# A gem necessary for ActiveRecord tests with IBM DB
gem 'ibm_db' if ENV['IBM_DB']

gem 'benchmark-ips'
