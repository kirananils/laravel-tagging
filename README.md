Laravel Tag Plugin
============

This library puts no real limits on what characters can be used in a tag. It uses Str::slug to determine if two tags are identical ("sugar-free" and "Sugar Free" would be treated as the same tag)

#### Composer Install

Versions will match laravel releases that they are compatible with

    "require": {
        "rtconner/laravel-tagging": "4.1"
    }

#### Run the migrations

	php artisan migrate --package=rtconner/laravel-tagging
	
#### Setup your models

    class Article extends \Eloquent {
        use Rtconner\Tagging\Taggable;
    }

#### Sample Usage

    $article->tag('Gardening'); // attach the tag
    
    $article->untag('Cooking'); // remove Cooking tag
    
    $article->tagged(); // return Collection of rows tagged to article
    
    $article->tagNames(); // get array of related tag names	
    
    Article::withTag('Gardening')->get(); // fetch all articles with tag
    
    Rtconner\Tagging\Tag::where('count', '>', 2)->get(); // return all tags used more than twice