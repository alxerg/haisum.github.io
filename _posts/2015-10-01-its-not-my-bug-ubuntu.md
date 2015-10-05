---
layout: post
title: Relief of knowing the bug isn't your fault
---

I wrote a vagrant file for local setup of jekyll for this blog last week. One really annoying bug that bothered me was that in spite of installing ruby2.0 package, bundle install command was failing on different bundles again and again with very obscure errors. Digging in deep revealed in spite of installing ruby2.0 only, `/usr/bin/ruby` was pointing to ruby1.9. I thought I was at fault first, but after some retries concluded, either of ruby, ubuntu or jekyll screwed up. Ruby 2.0 is requirement for jekyll, so symlinking `/usr/bin/ruby2.0` to `/usr/bin/ruby` solved the issue, but if anything else depended on ruby1.9 in ubuntu, it would break. I didn't really care because all I wanted with my ubuntu/vagrant vm was running jekyll so I could preview my blog before pushing it. Today after some google search I found it was indeed a bug by Ubuntu itself. You can see a lot of bashing going on at <a href="https://bugs.launchpad.net/ubuntu/+source/ruby2.0/+bug/1310292" rel="nofollow">Bug#1310292: installing `ruby2.0` results in ruby 1.9.3-p484 as default version</a>. It feels good to find bugs in such big scale, quality software. You find satisfaction in knowing you aren't the only one introducing stupid bugs in production.