# django-gunicorn-supervisor

An ansible role for depoloying a django application using gunicorn and
supervisor.

## Variables

`repo_type` - either 'hg' or 'git' @todo - add 'local'
`django_repo` - the path to the repo or the local source if `repo_type` = local
`app_name` - the name of the app
`django_settings` - the settings python module ex: stars.settings
`ssl` - a boolean flag to indicate if ssl should be used
`ssl_crt` - the certificate file (stored in a vault)
`ssl_key` - the key (should be stored in a vault)
`domain_name` - like www.aashe.org

`install_dev_packages` - flag to indicate that dev packages should be installed
`install_test_packages` - flag to indicate that test packages should be installed
`base_app_apt_packages` - the base apt-get packages for this app
`dev_app_apt_packages` - the base apt-get packages for this app
`test_app_apt_packages` - the test apt-get packages for this app

`gunicorn_workers` - the number of gunicorn workers (default is 1)

`newrelic` - boolean: should we use new relic?
`newrelic_license_key` - the new relic license key (required if using new relic)
`new_relic_log_level` - default is "info"

See vars/main.yml for more variables that can be overridden or shared with other roles.

## Tags

`pull`

Just pulls the latest version of the repo and restarts the server. This would
be the tag you'd use when applying new code changes.

## Dependencies

This role depends on the `repo-vars` role for connectivity with github and bitbucket.

## Notes

Use a local repository instead of pulling from a remote repo by setting the
`repo_type` variable to 'local' and setting the `django_repo` variable.
