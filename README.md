# node_alchemy

### a *promise* based shim for [AlchemyAPI](http://www.alchemyapi.com/developers/getting-started-guide)

Usage:

*npm install node_alchemy*

The alchemy object is instantiated on initial require, accepting a single argument (the API key).

After instantiation, the primary method exposed is *lookup*, which accepts four arguments:

alchemy.lookup(CALL_TYPE, INPUT_TYPE, INPUT_DATA, OPTIONS)

The lookup method returns a promise, which can be handled typically:

```
var alchemy = require('node_alchemy')(YOUR_API_KEY);

  alchemy.lookup('keywords', 'url', someURL)
    .then(function (result) {
      res.json(result);
    })
    .catch(function (err) {
      res.json({status: 'error', message: err});
    });
```

## entities

**alchemy.lookup('entities', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the entities for text, a URL or HTML.
* For an overview, please refer to: http://www.alchemyapi.com/products/features/entity-extraction/
* For the docs, please refer to: http://www.alchemyapi.com/api/entity-extraction/

ARGS:
* INPUT_TYPE -> which version of the call, i.e. text, url or html.
* INPUT_DATA -> the data to analyze, either the text, the url or html code.
* OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
* disambiguate -> disambiguate entities (i.e. Apple the company vs. apple the fruit). 0: disabled, 1: enabled (default)
* linkedData -> include linked data on disambiguated entities. 0: disabled, 1: enabled (default)
* coreference -> resolve coreferences (i.e. the pronouns that correspond to named entities). 0: disabled, 1: enabled (default)
* quotations -> extract quotations by entities. 0: disabled (default), 1: enabled.
* sentiment -> analyze sentiment for each entity. 0: disabled (default), 1: enabled. Requires 1 additional API transction if enabled.
* showSourceText -> 0: disabled (default), 1: enabled
* maxRetrieve -> the maximum number of entities to retrieve (default: 50)

## keywords

**alchemy.lookup('keywords', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the keywords from text, a URL or HTML.
* For an overview, please refer to: http://www.alchemyapi.com/products/features/keyword-extraction/
* For the docs, please refer to: http://www.alchemyapi.com/api/keyword-extraction/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	keywordExtractMode -> normal (default), strict
*	sentiment -> analyze sentiment for each keyword. 0: disabled (default), 1: enabled. Requires 1 additional API transaction if enabled.
*	showSourceText -> 0: disabled (default), 1: enabled.
*	maxRetrieve -> the max number of keywords returned (default: 50)

## concepts

**alchemy.lookup('concepts', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Tags the concepts for text, a URL or HTML.
* For an overview, please refer to: http://www.alchemyapi.com/products/features/concept-tagging/
* For the docs, please refer to: http://www.alchemyapi.com/api/concept-tagging/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	maxRetrieve -> the maximum number of concepts to retrieve (default: 8)
*	linkedData -> include linked data, 0: disabled, 1: enabled (default)
*	showSourceText -> 0:disabled (default), 1: enabled

## sentiment

**alchemy.lookup('sentiment', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Calculates the sentiment for text, a URL or HTML.
* For an overview, please refer to: http://www.alchemyapi.com/products/features/sentiment-analysis/
* For the docs, please refer to: http://www.alchemyapi.com/api/sentiment-analysis/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	showSourceText -> 0: disabled (default), 1: enabled

## sentiment_targeted

**alchemy.lookup('sentiment_targeted', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Calculates the targeted sentiment for text, a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/sentiment-analysis/
*	For the docs, please refer to: http://www.alchemyapi.com/api/sentiment-analysis/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	target -> the word or phrase to run sentiment analysis on.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	showSourceText	-> 0: disabled, 1: enabled

## text

**alchemy.lookup('text', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the cleaned text (removes ads, navigation, etc.) for a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/text-extraction/
*	For the docs, please refer to: http://www.alchemyapi.com/api/text-extraction/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. url or html.
*	INPUT_DATA -> the data to analyze, either the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	useMetaINPUT_DATA -> utilize meta description data, 0: disabled, 1: enabled (default)
*	extractLinks -> include links, 0: disabled (default), 1: enabled.

## text_raw

**alchemy.lookup('text_raw', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the raw text (includes ads, navigation, etc.) for a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/text-extraction/
*	For the docs, please refer to: http://www.alchemyapi.com/api/text-extraction/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. url or html.
*	INPUT_DATA -> the data to analyze, either the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	none

## author

**alchemy.lookup('author', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the author from a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/author-extraction/
*	For the docs, please refer to: http://www.alchemyapi.com/api/author-extraction/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. url or html.
*	INPUT_DATA -> the data to analyze, either the the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Availble Options:
*	none

## language

**alchemy.lookup('language', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Detects the language for text, a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/api/language-detection/
*	For the docs, please refer to: http://www.alchemyapi.com/products/features/language-detection/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	none

## title

**alchemy.lookup('title', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the title for a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/text-extraction/
*	For the docs, please refer to: http://www.alchemyapi.com/api/text-extraction/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. url or html.
*	INPUT_DATA -> the data to analyze, either the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	useMetaINPUT_DATA -> utilize title info embedded in meta data, 0: disabled, 1: enabled (default)

## relations

**alchemy.lookup('relations', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the relations for text, a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/relation-extraction/
*	For the docs, please refer to: http://www.alchemyapi.com/api/relation-extraction/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	sentiment -> 0: disabled (default), 1: enabled. Requires one additional API transaction if enabled.
*	keywords -> extract keywords from the subject and object. 0: disabled (default), 1: enabled. Requires one additional API transaction if enabled.
*	entities -> extract entities from the subject and object. 0: disabled (default), 1: enabled. Requires one additional API transaction if enabled.
*	requireEntities -> only extract relations that have entities. 0: disabled (default), 1: enabled.
*	sentimentExcludeEntities -> exclude full entity name in sentiment analysis. 0: disabled, 1: enabled (default)
*	disambiguate -> disambiguate entities (i.e. Apple the company vs. apple the fruit). 0: disabled, 1: enabled (default)
*	linkedData -> include linked data with disambiguated entities. 0: disabled, 1: enabled (default).
*	coreference -> resolve entity coreferences. 0: disabled, 1: enabled (default)
*	showSourceText -> 0: disabled (default), 1: enabled.
*	maxRetrieve -> the maximum number of relations to extract (default: 50, max: 100)

## category

**alchemy.lookup('category', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Categorizes the text for text, a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/text-categorization/
*	For the docs, please refer to: http://www.alchemyapi.com/api/text-categorization/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e. text, url or html.
*	INPUT_DATA -> the data to analyze, either the text, the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	showSourceText -> 0: disabled (default), 1: enabled

## feeds

**alchemy.lookup('feeds', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Detects the RSS/ATOM feeds for a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/feed-detection/
*	For the docs, please refer to: http://www.alchemyapi.com/api/feed-detection/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e.  url or html.
*	INPUT_DATA -> the data to analyze, either the the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	none

## microformats

**alchemy.lookup('microformats', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Parses the microformats for a URL or HTML.
*	For an overview, please refer to: http://www.alchemyapi.com/products/features/microformats-parsing/
*	For the docs, please refer to: http://www.alchemyapi.com/api/microformats-parsing/

ARGS:
*	INPUT_TYPE -> which version of the call, i.e.  url or html.
*	INPUT_DATA -> the data to analyze, either the the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.

Available Options:
*	none

## taxonomy

**alchemy.lookup('taxonomy', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Categorized through the taxonomy call for text, HTML, or a URL.
	
ARGS:
*	INPUT_TYPE -> which version of the call (currently, only 'url' is supported)
*	INPUT_DATA -> the data to analyze, either the the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.
	
Available Options:
*	showSourceText -> 0: disabled (default), 1: enabled.

## combined

**alchemy.lookup('combined', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts the combined call for a URL.
	
ARGS:
*	INPUT_TYPE -> which version of the call (currently, only 'url' is supported)
*	INPUT_DATA -> the data to analyze, either the the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.
	
Available Options:
*	extract -> VALUE,VALUE,VALUE,... (possible VALUEs: page-image,entity,keyword,title,author,taxonomy,concept,relation,doc-sentiment)
*	extractMode -> (only applies when 'page-image' VALUE passed to 'extract' option) 
*	trust-metadata: less CPU-intensive, less accurate
*	always-infer: more CPU-intensive, more accurate
*	disambiguate -> whether to disambiguate detected entities, 0: disabled, 1: enabled (default)
*	linkedData -> whether to include Linked Data content links with disambiguated entities, 0: disabled, 1: enabled (default). disambiguate must be enabled to use this.
*	coreference -> whether to he/she/etc coreferences into detected entities, 0: disabled, 1: enabled (default)
*	quotations -> whether to enable quotations extraction, 0: disabled (default), 1: enabled
*	sentiment -> whether to enable entity-level sentiment analysis, 0: disabled (default), 1: enabled. Requires one additional API transaction if enabled.
*	showSourceText -> 0: disabled (default), 1: enabled.
*	maxRetrieve -> maximum number of named entities to extract (default: 50)

## image

**alchemy.lookup('image', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Extracts images from a URL.
	
ARGS:
*	INPUT_TYPE -> which version of the call (currently, only 'url' is supported)
*	INPUT_DATA -> the data to analyze, either the the url or html code.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.
	
Available Options:
*	extractMode -> trust-metadata: less CPU-intensive and less accurate, always-infer: more CPU-intensive and more accurate

## image_keywords

**alchemy.lookup('image_keywords', INPUT_TYPE, INPUT_DATA, OPTIONS)**

Tags image with keywords

INPUT:
*	INPUT_TYPE -> which version of the call (currently, only 'url' or 'image' is supported)
*	INPUT_DATA -> the URL to the data to analyze.
*	OPTIONS -> various parameters that can be used to adjust how the API works, see below for more info on the available options.
	
Available Options:
*	extractMode -> trust-metadata: less CPU-intensive and less accurate, always-infer: more CPU-intensive and more accurate
*	imagePostMode -> not-raw: pass an unencoded image file with "image=URI_ENCODED_DATA"; raw: pass an unencoded image file using POST ('image' flavor only).
