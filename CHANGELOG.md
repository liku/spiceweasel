This is the current, previous and future development milestones and contains the features backlog.

knife role from file roles/*.rb
https://gist.github.com/3752021


1.3.0 TODO
=====
* useful error messages for missing files like metadata.rb
* librarian-chef support "cookbooks:" -> "librarian:"
* wildcards for environments and roles http://tickets.opscode.com/browse/CHEF-1911

1.2.1
=====
* Ruby syntax cleanup per https://github.com/styleguide/ruby

1.2.0
=====
* properly auto name by number provider instances (Fletcher Nichol & Michael Beuken)
* YAML wildcards should be quoted (Joshua Timberman)
* Don't add empty strings to the cookbook dependency list (Chris Griego)
* handle single and double-quoted quoting styles in metadata.rb (Fletcher Nichol)
* Remove the already initialized constant error (John Dewey)

1.1.3
=====
* Handle deleting an environment that has had multiple versions of cookbooks uploaded (Mike Fiedler)
* Document how to use parallel to name nodes during `server create`

1.1.2
=====
* explicitly list broken/missing cookbooks during extracts, with --novalidation override

1.1.1
=====
* fixed issue in cookbook dependency sorting

1.1
===
* [Added functionality to extract all relevant cookbooks/roles/environments/databags/nodes from local chef-repo directory](https://github.com/mattray/spiceweasel/issues/9) (Geoff Meakin)
* [Fixed a number of Ruby 1.8.7 issues](https://github.com/mattray/spiceweasel/issues/10)
* Added --extractyaml & --extractjson to output YAML & JSON manifests

1.0.1
=====
* added knife-hp

1.0
===
* --no-validation to skip validation
* switched from raising exceptions to just exiting with STDERR
* validation for cookbooks
 * check metadata.rb for their dependencies
* validation for environments
 * supports both .json and .rb
 * check names within files rather than the names of files
 * cookbooks referenced in environments
* validation for roles
 * supports both .json and .rb
 * check names within files rather than the names of files
 * cookbooks referenced in roles
 * roles referenced in roles
* validate data bags
 * exist and items exist
 * JSON parses and id matches
 * secret key in place
* validate node run_lists
 * existing recipes and roles
* validate custom bootstrap templates?

0.9.1
=====
* support for knife bootstrap windows

0.9
===
* flag to enable 'knife cookbook site install' since we're using site download currently
* on provider delete take count of vendor-specific, delete if match (ec2 server delete and node delete)
* use GNU parallel with knife for vendor-specific knife server creates
* reprioritized backlog

0.8.2
=====
* fixed Issue #6, catch empty cookbooks, environments, roles, data bags and nodes.
* fixed Issue #7, permissions in spiceweasel gem folder
* fixed Issue #8, allow passthrough of knife options (in particular -c KNIFECONFIGFILES) through to the outputted knife commands. (Geoff Meakin)
* linked ravel-repo and php quickstart examples


0.8.1
=====
* typo fix by Rick Martinez (digx)

0.8
===
* refactor by Elliot Crosby-McCullough into libraries and adding testing.

0.7.1
=====
* fixed run list parsing
* updated examples for Chef 0.10
* fixed validation on existing cookbooks
* added examples directory

0.7
===
* add support for environments
* rescue from parser errors
* update cookbook download syntax
* multiple nodes with same runlists syntax
* add support for encrypted data bags
* wildcard support for data bag items

0.6
===
* add support for cookbook options

0.5
===
* support JSON and YAML

0.4
===
* support versions for cookbooks
* support site vendor for cookbooks

0.3
===
* renamed MILESTONES.md to CHANGELOG.md
* fixed version number
* updated YAML schema and examples because Ruby 1.8 does not order hashes.
* validate that the recipes and roles listed in the nodes are loaded

0.2
===
* switch to mixlib-cli
* --dryrun The option `--dryrun` will print the commands to run, but not actually execute them (the default behavior)
* --delete The option `--delete` will delete each cookbook, role, data bag, environment and node described in the yml file. All nodes from the system are deleted with `knife node bulk_delete`.
* --rebuild The option `--rebuild` will remove all currently managed infrastructure for this chef repository and rebuild it from scratch.

0.1
===
* initial README.md describing goals
* command-line tool
* basic options all supported
* create repo on GitHub
* publish as a gem on RubyGems


BACKLOG
=======
1.2
---
* all validation done by converting .rb files to Chef objects
* write out JSON or YAML files from --extract commands
* sort --extractyaml/--extractjson for Ruby 1.8.7 so it's always same results
* sanitize error messages to make sense for both extract & manifest
* [Added support for nesting role files in subdirectories of the role/ directory.](https://github.com/mattray/spiceweasel/pull/11)
* [spiceweasel does not recognize cookbooks outside of ./cookbooks](https://github.com/mattray/spiceweasel/issues/12)
* [Validation for encrypted data bag secret should expand path](https://github.com/mattray/spiceweasel/issues/13)

Future
------
* make .yml files for every quickstart
* CONVERT TO A KNIFE PLUGIN
 * knife batch create from file infrastructure.yml
 * knife batch delete from file infrastructure.json
 * knife batch rebuild from file infrastructure.yml
* EXTRACT EXISTING INFRASTRUCTURE
 * knife batch extract to a tarball named for the organization
 * option to include credentials and knife.rb
 * translate json back to rb?
* EXECUTE THE COMMANDS
 * -e/--execute execute the commands
 * catching return codes and retrying (with retry count?)
 * make the JSON calls directly with Chef APIs? spice?
* ADDITIONAL VALIDATION
 * environment-specific run_lists
* Librarian integration?
