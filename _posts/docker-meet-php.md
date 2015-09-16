---
layout: post
title:  "Php, meet Docker. Docker, meet Php"
date:
categories: technology php docker
---

I'm going to say it: I am a [Docker](https://docker.com) fan boy. We've been running Docker ever since my fist [Docker meetup in Amsterdam](http://www.meetup.com/Docker-Randstad/). (I believe it was the third ever for group at that time)
But I digress. Let me first introduce Docker to the PHP community who don't already know: it's awesome! To keep it short, running your PHPunit test suite across 20 different PHP versions with just a few commands and hardly any diskspace-, time- or resource usage! How cool is that?

```
gekkie@mypc:~/projects/php-mt940$ docker run --rm -w /app -v $(pwd):/app php:5.4-cli php vendor/bin/phpunit
PHPUnit 4.4.5 by Sebastian Bergmann.

Configuration read from /app/phpunit.xml.dist

................................................................. 65 / 82 ( 79%)
...............I.

Time: 171 ms, Memory: 5.75Mb

OK, but incomplete, skipped, or risky tests!
Tests: 82, Assertions: 168, Incomplete: 1.

gekkie@mypc:~/projects/php-mt940$ docker run --rm -w /app -v $(pwd):/app php:5.5-cli php vendor/bin/phpunit
PHPUnit 4.4.5 by Sebastian Bergmann.

Configuration read from /app/phpunit.xml.dist

................................................................. 65 / 82 ( 79%)
...............I.

Time: 136 ms, Memory: 6.00Mb

OK, but incomplete, skipped, or risky tests!
Tests: 82, Assertions: 168, Incomplete: 1.

gekkie@mypc:~/projects/php-mt940$ docker run --rm -w /app -v $(pwd):/app php:5.6-cli php vendor/bin/phpunit
PHPUnit 4.4.5 by Sebastian Bergmann.

Configuration read from /app/phpunit.xml.dist

................................................................. 65 / 82 ( 79%)
...............I.

Time: 122 ms, Memory: 6.00Mb

OK, but incomplete, skipped, or risky tests!
Tests: 82, Assertions: 168, Incomplete: 1.

gekkie@mypc:~/projects/php-mt940$ docker run --rm -w /app -v $(pwd):/app php:7-cli php vendor/bin/phpunit
PHPUnit 4.4.5 by Sebastian Bergmann.

Configuration read from /app/phpunit.xml.dist

................................................................. 65 / 82 ( 79%)
...............I.

Time: 77 ms, Memory: 4.00Mb

OK, but incomplete, skipped, or risky tests!
Tests: 82, Assertions: 168, Incomplete: 1.
```

Yes it's that simple to mount your current working directory into a `container` and run you're composer installed PHPunit using *all* these versions of PHP :)
And *yes* that does include PHP7(RC2 at time of writing) now i'm cutting alot of corners with this example, but I believe this is the main selling point, the gateway drug so to speak, that will get _any_ PHP developer into Docker

Imagine running a single command on a brand new laptop,server,raspberryPI after installing the docker engine and having your production environment comepletely there... (Mysql,Redis,a Loadbalancer, serveral PHP `boxes` and possibly more?) just with a single command.. That would be weird wouldn't it? Yes it would, but it would also be possible using docker (compose)

``` docker-compose up```

Yes, it could be that simple. (provided you have the right project and prequisite configuration yml file.. ) but basically: yes... Just that... 

I will write up more, but feel free to leave me some kind of note if you already want to know more (specifics?) I'll be glad to help (i really get excited talking about the low barrier of entry and great opportunity this technology brings...) Heck I even gave a talk once [@AmsterdamPHP]()

Anyway, I really hope I've triggered you into looking up more information on docker...

(just a tease to get you even more interested: layered-filesystems, easy application experimentation, applications-on-the-go, cleans up after itself etc etc)