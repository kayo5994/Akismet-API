Akismet-API
===========

Small library to access Akismet API

Usage
=====

Initalizing class

    $akismet = new Akismet('api key', 'blog url', Akismet::USE_CURL);

During initalization, class connects to Akismet and verified API key. You have to check `$akismet->getError()` to see if there are any errors

Checking if comment is spam

    $akismet->check(array(
        'permalink' => 'The permanent location of the entry the comment was submitted to',
        'comment_type' => 'May be blank, comment, trackback, pingback, or a made up value like "registration"',
        'comment_author' => 'Name submitted with the comment',
        'comment_author_email' => 'Email address submitted with the comment',
        'comment_author_url' => 'URL submitted with comment',
        'comment_content' => 'The content that was submitted'
    ));

Above function returns `true`, if comment is spam, `false` otherwise. `$akismet->sendSpam()` and `$akismet->sendHam()` works same way.

Data encoding
=============

DO NOT ENCODE DATA SENT TO CLASS! IT IS ENCODED BEFORE REQUEST IS SENT TO AKISMET!
