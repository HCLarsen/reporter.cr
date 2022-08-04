# Reporter [Work In Progress]

Reporter is a Report/Document generation shard, that expands on the [ECR](https://crystal-lang.org/api/latest/ECR.html) module from the core library.

The goals are to make it easy to generate the same report in multiple formats (ie, HTML, text, rtf, etc), to make it simple to include reusable "partial" documents, in the same format, and to include CSS for the HTML outputs.

By creating a subclass of the `Document` class, a developer can automatically generate output classes for many formats, such as HTML or text. This allows all the data parsing and generating code to be contained in one class.

The `Document` object will look for ECR files bearing a specified file name of the expected type, and use `ECR` to generate the output. In the case of HTML files, you can also add a CSS file as a style tag in the `<head>` element.

The default location for template file is in a directory named `templates` in the same directory as the file for the `Document` subclass.

## Installation

1. Add the dependency to your `shard.yml`:

   ```yaml
   dependencies:
     reporter:
       github: HCLarsen/reporter
   ```

2. Run `shards install`

## Usage

```crystal
require "reporter"
```

### A simple example:

```crystal
# src/greeting.cr

class Greeting < Reporter::Document
  def initialize(@name : String)
  end
end
```

In `templates/greeting.txt.ecr`:
```crystal
Hello <%= @name %>
```

```crystal
greeting = Greeting.new("World!")

greeting.to_text #=> "Hello World!"
```

## Development

TODO: Write development instructions here

## Contributing

1. Fork it (<https://github.com/HCLarsen/reporter/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Contributors

- [Chris Larsen](https://github.com/HCLarsen) - creator and maintainer
