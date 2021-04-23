---
layout: post
title: "Installing Let’s Encrypt SSL certificate on Heroku hosted Rails servers"
date: 2015-12-23 00:00:00 -0800
categories: [security, Open Source]
---

# Installing Let’s Encrypt SSL certificate on Heroku hosted Rails servers

If you manage a web site and your SSL certificate is about to expire, now could be a good time to take a look at the [Let’s Encrypt](https://letsencrypt.org/) project.

Since December 3rd 2015 Let’s Encrypt has begun their [public beta](https://letsencrypt.org/2015/12/03/entering-public-beta.html) and opened the door to anybody who wish to obtain a free SSL/TLS certificate for their server. The process requires interacting with the Let’s Encrypt ACME server and proving you control the domain for which you request a certificate.

For an overview of the process you can read Chris Hager’s post featuring a [Comparison of 10 ACME / Let’s Encrypt Clients](https://www.metachris.com/2015/12/comparison-of-10-acme-lets-encrypt-clients/). Although you will not find a Rails client in the list, there is a gem for that.

The [letsencrypt\_http\_challenge](https://rubygems.org/gems/letsencrypt_http_challenge) gem provides a Rails::Engine that will allow your server to answer the [Simple Http](https://letsencrypt.github.io/acme-spec/#rfc.section.7.1) validation challenge as well as a rake script to handle the certificate creation process without needing to install the [official Let’s Encrypt client](https://letsencrypt.readthedocs.org/en/latest/using.html). The inspiration for LetsencryptHttpChallenge comes from the following gems:  
lgromanowski/letsencrypt-plugin [https://github.com/lgromanowski/letsencrypt-plugin](https://github.com/lgromanowski/letsencrypt-plugin)  
unixcharles/acme-client [https://github.com/unixcharles/acme-client](https://github.com/unixcharles/acme-client)

Below is a walkthrough of the steps needed to obtain your own Let’s Encrypt SSL certificate for a twelve-factor app Rails server using the [letsencrypt\_http\_challenge](https://rubygems.org/gems/letsencrypt_http_challenge) ruby gem. For the initial release, the installation requires manually updating the environment variables on the server but full automation should also be possible.

## Getting started

These steps assume you already have an existing Rails application that can be reached using the domain name(s) you wish to obtain an SSL certificate for. The engine doesn’t have any database dependency and requires only minimal code change to install so if you change your mind, removing the gem is trivial too.

### Installation

Add the gem to your application Gemfile:

```bash
gem 'letsencrypt_http_challenge'
```

Install it with bundler:

```bash
$ bundle install
```

Or manually with the gem command:

```bash
$ gem install letsencrypt_http_challenge
```

Next, add this line to conditionally mount the engine in your application’s routes.rb file:

```ruby
Rails.application.routes.draw do

mount LetsencryptHttpChallenge::Engine => "/" unless ENV['LE_HTTP_CHALLENGE_RESPONSE'].blank?

# Other routes...

end
```

Unless the `LE_HTTP_CHALLENGE_RESPONSE` environment variable is set at the time routes.rb is read, the Engine will not be mounted.

You can now deploy your server code update.

### Usage

With the gem installed on your server, run the following Rake task locally from your development machine. Set environment variables to provide the necessary inputs to the script, specifying the desired contact email as well as the list of domains / sub-domains you wish to include in the certificate.

```bash
$ LE_HTTP_CHALLENGE_CONTACT_EMAIL=admin@example.com LE_HTTP_CHALLENGE_CERTIFICATE_DOMAINS="www.example.com example.com" bundle exec rake generate_letsencrypt_cert
```

The first domain in the list will be the “Common Name” of the certificate, in this case “www.example.com”.

As the interactive script executes, set the LE\_HTTP\_CHALLENGE\_RESPONSE environment variable as requested on your server, restart it and test the response with your browser for each domain that needs to be validated.

You can first test the process using Let’s Encrypt’s staging server. Once you confirmed everything is working properly, execute the script again, this time specifying the production endpoint URL as follow:

```bash
LE_HTTP_CHALLENGE_ENDPOINT='https://acme-v01.api.letsencrypt.org/'
```

After you are done with the verification, be sure to delete the LE\_HTTP\_CHALLENGE\_RESPONSE environment variable on your web server and restart it one last time to disable the route provided by the gem.

The [gem README](https://github.com/datamolecule/letsencrypt_http_challenge) provides outputs for a sample run of the script and gives examples of commands to run using the Heroku toolbelt CLI to manipulate environment variables and update your SSL certificate. Further details about setting up SSL on Heroku can be found in this [SSL Endpoint](https://devcenter.heroku.com/articles/ssl-endpoint) article.

What’s next?

Future improvements to the gem will fully automate certificate deployment on Heroku and also refactor the code to make the addition of other deployment targets easier.