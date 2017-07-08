# No-op Travis Webhook Emitter

## Caveat

This is just something I'm tinkering with and is not intended for any kind of public consumption as-is.  

## Description

This is a barebones repo intended to emit TravisCI webhook notifications to a service that is waiting to consume them.  I adapted it from [this repo](https://github.com/rkh/test-project-matrix-1), which I stumbled across while looking for a way to run a "dummy" Travis build.

If you're reading this and you're not me, you probably have no use for this.  But, if you wanted to adapt it for your own purposes:

1. Fork this repo and enable TravisCI for your fork
2. Spin up a tiny web app somewhere to accept the notification payloads (here's [mine](https://github.com/sadatay/trap-webhooks), which is based off of [this](https://github.com/travis-ci/webhook-signature-verifier))
3. Edit .travis.yml's `notifications.webhooks` directive to point to your tiny web app
4. Edit .travis.yml's `script` directive to `'rake test_pass'` or `'rake test_fail'` depending on what kind of build notifications you want to simulate.
5. Push your changes (or restart an existing Travis build) and, if all goes well, your tiny web app will receive some POST requests from TravisCI

Why would you want to do this?  Travis does provide an [example payload](https://docs.travis-ci.com/user/notifications/#Webhooks-Delivery-Format) in their notifications documentation, but this approach lets you simulate a build in "real-time".  In my case, I was trying to build a chatbot handler that consumed Travis notifications and I wanted to fiddle around with some "real" payloads.
