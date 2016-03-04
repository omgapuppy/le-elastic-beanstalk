## AWS ElasticBeanstalk config for [Logentries Agent](https://github.com/logentries/le)


You can utilize Logentries Token-Based approach with Elastic Beanstalk applications.

First, create a host in your Logentries account. Next, add a logfile with the source type set to Token TCP. You will be given a Token UUID which represents that logfile.

In the root of your app’s directory, create the following hidden directory, .ebextensions and inside that logentriesBeanstalk.config. Edit the following portion of the ```logentriesBeanstalk.config``` file:

```
[Application name]
path = /path/to/log/file
token = MY_TOKEN
```

Or **alternatively**, the `destination` parameter can be used so that the log is created automatically in your account:

```
[Application name]
path = /path/to/log/file
destination = LogSet/Log
```

Repeat the above section for every file on your EB instances, that you wish to follow.

Please see the [Logentries Agent documentation](https://github.com/logentries/le#follow-log-files-through-your-configuration-file) for more details on how to use the Agent configuration file.
