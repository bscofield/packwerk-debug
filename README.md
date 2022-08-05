# Packwerk debug repo

This repo is a minimal reproduction of an issue I'm seeing and can't figure out (probably because I'm missing something obvious). It's a Rails 6.1.6.1 application, and the only additional gem I've added is Packwerk itself.

I'm trying to set up packs within `/packages`, but Packwerk is not recognizing violations of those packs' constants. `packwerk check` on the current state of the repo returns:

```
📦 Packwerk is inspecting 13 files
You don't have net-smtp installed in your application. Please add it to your Gemfile and run bundle install
.........E...
📦 Finished in 0.4 seconds

packages/restaurant_data/models/restaurant.rb:5:6
Dependency violation: ::User belongs to '.', but 'packages/restaurant_data' does not specify a dependency on '.'.
Are we missing an abstraction?
Is the code making the reference, and the referenced constant, in the right packages?

Inference details: this is a reference to ::User which seems to be defined in app/models/user.rb.
To receive help interpreting or resolving this error message, see: https://github.com/Shopify/packwerk/blob/main/TROUBLESHOOT.md#Troubleshooting-violations


1 offense detected

No stale violations detected
```
