!SLIDE 
# PHP7

!SLIDE
## Why?

!SLIDE bullets small

* Update servers to 2016, and keep them up to date.
* Speed improvements are a nice bonus. 
* PHP7 features? not so much

!SLIDE 
# Speed

!SLIDE code small
    @@@ php

    › cat fact.php
    <?php

    function fact($n) {
      if ($n < 2) return $n;
      else return ($n * fact($n - 1));
    }

    $count = 10000;

    $start = microtime(true);
    for ($i=0; $i < $count; $i++) {
      fact(10000);
    }
    echo microtime(true) - $start . "\n";

!SLIDE bullets
## benchmarks on server417

* PHP7 _inside_ container: **10s**
* PHP5.3 _outside_ container: **45s**


!SLIDE

# Where are we?

!SLIDE bullets

* docker-staging with custom engagor_web image
* Recreated Folkes' original libcld + php-cld. This is on github now as well.
* prepare puppet (extensions, config,...)
* Focus on unit tests

!SLIDE BULLETS small
# unit tests

* convert errors in failures with asserts. (E.g. Mention::getMention)
* failures at this point are due to missing data

!SLIDE bullets

* Most of Engagor just worked, parts that didn't are patched
* #1 problem: static methods (Die! Simplepie)
* calls like $controller->$routeRs[1](); must be escaped with {} 
* For the rest, sort of ok

!SLIDE bullets

# What shiny new features are we using now?

!SLIDE 

None at all. For now, trying to stay backwards compatible.

!SLIDE bullets

# What's next?

* fixes-for-php7 + Toms' staging build instructions.
* Production: unix solutions migration -OR- docker
