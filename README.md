![rspec-rerun](https://raw.github.com/dblock/rspec-rerun/master/rspec-rerun.png)

[![Gem Version](http://img.shields.io/gem/v/rspec-rerun.svg)](http://badge.fury.io/rb/rspec-rerun)
[![Build Status](http://img.shields.io/travis/dblock/rspec-rerun.svg)](https://travis-ci.org/dblock/rspec-rerun)
[![Dependency Status](https://gemnasium.com/dblock/rspec-rerun.svg)](https://gemnasium.com/dblock/rspec-rerun)
[![Code Climate](https://codeclimate.com/github/dblock/rspec-rerun.svg)](https://codeclimate.com/github/dblock/rspec-rerun)

The **rspec-rerun** gem is a drop-in solution to retry (rerun) failed RSpec examples. It may be useful, for example, with finicky Capybara tests. The strategy to rerun failed specs is to output a file called `rspec.failures` that contains a list of failed examples and to feed that file back to RSpec via `-e`.

Usage
-----

Add `rspec-rerun` to `Gemfile` in the `:development` and `:test` groups.

(For Rspec 2 use version '~> 0.3.1'. )

``` ruby
group :development, :test do
  gem 'rspec-rerun'
end
```

Require `rspec-rerun` and change the default task in `Rakefile`.

``` ruby
require 'rspec-rerun'
task :default => 'rspec-rerun:spec'
```

Run `rake` or `rake rspec-rerun:spec`. Failed examples will be rerun automatically.

Parameters
----------

The `rspec-rerun:spec` task accepts the following parameters:

* `retry_count`: number of retries, defaults to 1, also available by setting

You can set the following global environment variables:

* `RSPEC_RERUN_RETRY_COUNT`: number of retries, defaults to the value of `retry_count` or 1
* `RSPEC_RERUN_PATTERN`: spec file pattern, defaults to the value defined by `RSpec::Core::RakeTask`
* `RSPEC_RERUN_TAG`: only execute the tag specified
* `RSPEC_RERUN_VERBOSE`: if 'false', don't show the rspec command invoked by Rake

Git Ignore
----------

A list of failed examples is stored in a file called `rspec.failures`. It might also be a good idea that you add `rspec.failures` to `.gitignore`.

History
-------

Rerunning failed specs has been a long requested feature [#456](https://github.com/rspec/rspec-core/issues/456) in [RSpec](https://github.com/rspec/rspec-core/). A viable approach was suggested in [#596](https://github.com/rspec/rspec-core/pull/596). The infrastructure from that pull request was merged and released with rspec-core 2.11, which enabled re-running specs outside of RSpec, as described in [our blog post](http://artsy.github.com/blog/2012/05/15/how-to-organize-over-3000-rspec-specs-and-retry-test-failures/). This gem has evolved from it.

Contributing
------------

See [CONTRIBUTING](CONTRIBUTING.md).

Copyright and License
---------------------

MIT License, see [LICENSE](LICENSE.md) for details.

(c) 2012-2015 [Artsy Inc.](http://artsy.github.com), [Daniel Doubrovkine](https://github.com/dblock) and [Contributors](https://github.com/dblock/rspec-rerun/blob/master/CHANGELOG.md)
