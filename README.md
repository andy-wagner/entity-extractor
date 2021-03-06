## Lightweight entity extraction engine

Extract entities based on a lexicon and/or library of patterns.

  * Easy to use API
  * High performance lexicon-based extraction, up to several hundred times faster than regex
  * Utilizes Lucene analyzers to improve match results
  * Java 8+

### Usage

```java
// create a lexicon
List<Entity> items = new ArrayList<>();
items.add(new DefaultEntity.Builder("John Smith").type("Person").build());
EntityBook entityBook = new EntityBook(items);

// create patterns
List<PatternDef> patterns = new ArrayList<>();
patterns.add(new PatternDef("[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\\.[a-zA-Z0-9-.]+", "Email", false));
PatternBook patternBook = new PatternBook(patterns);

//perform extraction
AggregateExtractor extractor = new AggregateExtractor();
ExtractionManifest manifest = extractor.extract(text, entityBook, patternBook);

for (ExtractionRegion region : manifest.getRegions()) {
    //do something with entities inside each region
}
```

### Examples

The **ner-example** project contains two example programs, [SigBlockExample](https://github.com/cerebrosoft/entity-extractor/blob/master/example/src/main/java/cerebrosoft/ner/example/SigBlockExample.java) and [WonderlandExample](https://github.com/cerebrosoft/entity-extractor/blob/master/example/src/main/java/cerebrosoft/ner/example/WonderlandExample.java), that illustrate extracting entities from text and using the results to mark up those entities in the document.

<img src="etc/sig-example.png" height="300"/>





