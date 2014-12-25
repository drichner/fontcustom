FontCustom in docker container!
==============================

FontCustome is useful to generate glyph fonts for use for e.g. in twitter bootstrap

Read more about [FontCustom][1] 

To assemble your own glyph font take a look at existing glyphs at [The NounProject][3]



How to run?
-----------

Default `docker run drichner/fontcustom` shows fontcustom help information.

I recommend using the script below because the local file location needs to be mapped to specific mounts in the container.



Helper script to run it in an environment like [boot2docker][2] or in [coreos][4] :

	#!/bin/bash
	
	docker run -v ${PWD}:/project  drichner/fontcustom $@

if you are in your project directory you can execute ```./fontcustom compile -n iconname -h ./vectors ```

Recommended font project structure:
===================================

This container expects the local project in the following layout:

    .
    |-projectdir/  will contain generated files
           |-vectors/    contains vector files


Usage
=====

1. create a projectdir anywhere on your drive: `mkdir -p myproject/vectors`
2. copy some vectors into you vectors dir: `cp /tmp/*svg myproject/vectors`
3. change into your project dir: cd myproject`
4. Initialize the project YAML: `./fontcustom config ./vectors`
5. generate your icons: `./fontcustom -n test -h ./vectors'

This will result in a "test" directory containig your brad new icon file along with a preview page. Instructions on how to use them can be found on [fontcustom's website][1]

  [1]: http://fontcustom.com/
  [2]: https://docs.docker.com/installation/mac/
  [3]: http://thenounproject.com/
  [4]: https://coreos.com/