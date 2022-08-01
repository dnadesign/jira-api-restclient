# Jira Api Rest Client

[![Build Status](https://secure.travis-ci.org/chobie/jira-api-restclient.png)](http://travis-ci.org/chobie/jira-api-restclient)


you know JIRA5 supports REST API. this is very useful to make some custom notifications and automated jobs.
(JIRA also supports email notification, but it's too much to custom templates, notification timing. unfortunately it requires Administration permission.)
this API library will help your problems regarding JIRA. hope you enjoy it.

# Usage

````php
<?php
require "Jira/Autoloader.php";
Jira_Autoloader::register();

$api = new Jira_Api(
    "https://your-jira-project.net",
    new Jira_Api_Authentication_Basic("yourname", "password")
);

$walker = new Jira_Issues_Walker($api);
$walker->push("project = YOURPROJECT AND (status != closed and status != resolved) ORDER BY priority DESC");
foreach ($walker as $issue) {
    var_dump($issue);
    // send custom notification here.
}
````

# License

MIT License

# JIRA5 Rest API Documents

https://developer.atlassian.com/static/rest/jira/5.0.html

# NOTE

## PHP 8 compatibility breaking changes

In order to make v1 compatible with PHP 8, the signature of Jira_Api::api() and Jira_Api_Client_ClientInterface::sendRequest() have changed.
Parameters have been re-ordered to comply with PHP 8 syntax, see [docs](https://www.php.net/manual/en/migration80.deprecated.php#migration80.deprecated.core)
