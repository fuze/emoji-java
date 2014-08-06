# emoji-java

*The missing emoji library for java.*

Based on the data provided by [github/gemoji project](https://github.com/github/gemoji), **emoji-java** is a lightweight java library that helps you to use Emojis in your java applications.

## How to get it?

Just add the dependency to your maven project:

```
<dependency>
  <groupId>com.vdurmont<groupId>
  <artifactId>emoji-java<artifactId>
  <version>1.0</version>
</dependency>
```

You can also build the project with `mvn clean install` and add the generated jar to your buildpath.

## How to use it?

### EmojiManager

The `EmojiManager` provides a bunch of static methods to search throught the emojis database:

* `getForTag` returns all the emojis for a given tag
* `getForAlias` returns the emoji for an alias
* `getAll` returns all the emojis
* `isEmoji` checks if a string is an emoji

You can also query the metadata:

* `getAllTags` returns the available tags

### Emoji model

An `Emoji` is a POJO (plain old java object), which provides the following methods:

* `getUnicode` returns the unicode representation of the emoji
* `getDescription` returns the (optional) description of the emoji
* `getAliases` returns a list of aliases for this emoji
* `getTags` returns a list of tags for this emoji

### Parse a string

To replace all the aliases by their unicode, use `EmojiParser.parseToUnicode(myString)`.

For example:

```
String str = "An :grinning:awesome :smiley:string with a few :wink:emojis!";
String result = EmojiParser.parseToUnicode(myString);
System.out.println(myString);
// Prints:
// "An 😀awesome 😃string with a few 😉emojis!"
```

To replace all the emoji's unicodes by their aliases, use `EmojiParser.parseToAliases(myString)`.

For example:

```
String str = "An 😀awesome 😃string with a few 😉emojis!";
String result = EmojiParser.parseToAliases(myString);
System.out.println(myString);
// Prints:
// "An :grinning:awesome :smiley:string with a few :wink:emojis!"
```