# Understanding Processwire Templates, Fields and Pages

Why Processwire is like an Object Oriented CMS/CMF.

Many are confused by the terminology used by Processwire to describe how it handles the data and relationships. The terms “template”, “field” and “page” are generic and widely used in other contexts not related to databases or information arquitecture.

In this article I will compare Processwire terminology to UML and basic Object Orientation principles.

![imagen](https://github.com/joyofpw/joyofpw.github.io/assets/292738/96b86b3c-c3e2-45b2-849b-938688f69f18)
> Class and Instances by [Wikibooks](https://en.wikibooks.org/wiki/A-level_Computing_2009/AQA/Problem_Solving,_Programming,_Operating_Systems,_Databases_and_Networking/Programming_Concepts/Object-oriented_programming_(OOP))

## Template

The template its the more abstract concept in Processwire. Its a contract that determines what can be done with whoever adheres to the contract. In other CMS or systems a template its only related to the output, the view, what the users sees on the screen. But in Processwire, the templates it´s a class that holds properties (fields) and instances (pages). A template could have an associated output for rendering, like html or json. But this is optional and its not required for working with templates. A template is an isolated entity, it could copy the fields from another template, but you can not make references or inheritance between templates.

## Fields

Fields are like the properties or attributes of a template (class). A field could contain simple information containers like “username” or complex relationships between pages (objects).

## Pages

Pages are the instances of a template (class). They contain the specific information stored in each field (property). Example: A page that adheres to a template (class, contract) “user”. This template has the field (property, attribute) “name”. Then the page can store information in the “name” field such as “camilo123”. A page can only adhere to a single template. Similar to single inheritance in programming languages.
Template Render Method

Each template has a “render” method inherited by its parent class. This method its only called when a file with the same name as the template its present on the filesystem at site/templates/. Example site/templates/user.php. You can overwrite this behaviour easily using Processwire’s admin and other techniques, but that its not in the scope of this article. The render method its content agnostic, you could throw html, json, pdf, zip, etc. The files associated with templates in the filesystem are just php files, so they can be rendered using complex or simple php arquitectures. When a template is “rendered”, it will use the information contained in the page that adheres to that template and belongs to the route that was requested.

## Example: A Simple Car

We will use the Car as simple example.

![imagen](https://github.com/joyofpw/joyofpw.github.io/assets/292738/44f241c2-48d9-4278-9b08-4fef08ca6a24)

In this simple template (class) named “CarTemplate” we have two fields (properties): color and maker. The class have a render method that outputs content as html. This class have two pages (objects, instances) that will render html with Red, Audi and White, VolksWagen as content for each page.

[Class Diagram](https://en.wikipedia.org/wiki/Class_diagram)

## How to Engineer a Processwire Site

The following tips describe my methodology before creating a new website or app that uses Processwire. Feel free to adapt these ideas to your own context. In this exercise we will make a simple site for a book collection.

As Processwire handles relationships between pages as a Tree. First I go to my favorite plain text editor and create a simple tree.

```yaml
Home
  - Authors
    - HP Lovecraft
     - The Call of Cthulhu
    - Mark Twain
     - The Prince and the Pauper
```

Using this approach I can see the relationships and templates that we will need.

First we need an author list template that will hold the authors, an author template that will hold the author info, and finally a book template that will hold the book info.

You can also check out [SolidWire](https://github.com/joyofpw/solidwire).

Using an UML tool like Astah, PlantUML or Mermaid we can make a simple class diagram.

![imagen](https://github.com/joyofpw/joyofpw.github.io/assets/292738/72f504bd-0710-4884-9925-293867bff275)

All classes have a render():html method. That means they will have a file inside the site/templates/ directory that will render the page content as html. If we omit that method its means the template will only be used for storing information and not for rendering. Also the “book” class have a special property. An array of Images.

Now we must create the relationships between the classes. [Here´s some UML info for class relationships](https://creately.com/guides/class-diagram-relationships/).

![imagen](https://github.com/joyofpw/joyofpw.github.io/assets/292738/e5900961-4596-4021-bf13-499e0ea0f6a7)

The diagram tells that zero or more “author” belongs just one “author-list” and if the “author-list” gets deleted, all authors will be deleted too. (composition relationship). For the books its says that one “author” could have zero or more “book”, and if the “author” gets deleted, the “book” objects will be deleted too.

With this information we can know which templates we need, and how they relate to each other and the page tree it will be created. Now you can use 
[The Wire Render Pattern](https://github.com/joyofpw/wire-render-pattern) or another technique you like for creating the site.

## Conventions

The following conventions are useful for creating class diagrams that will be used for creating Processwire sites.

### Template Names

Using Processwire´s admin its more easy to name templates in lower case and dash separated between words. In that way will be the same as the file inside the filesystem. For complex lists its useful naming with the suffix list and its children as list-item example: author-list, author-list-item.

### Field Types

The following types will be used for creating class diagrams:

- String = TextField
- Text = TextArea
- Bool = Checkbox
- Image = ImageField
- Int = IntegerField
- Float = FloatField
- Date = DateField

### Repeater Fields

Repeater are a special case, but they only need to inherit from “Repeater” class. And can be used as another page relationship. I prefer to handle relationship between pages as a composite relationship and relationship between repeaters as aggregation relationship.

![imagen](https://github.com/joyofpw/joyofpw.github.io/assets/292738/378a3b82-f9d1-4446-bafd-8a76942b2252)

A book could have multiple editions, but that will not be represented in the book page tree, because its inside a repeater field. I prefer to use composition relationships to page level relationships and aggregation relationships to repeater fields and other that do not make direct page tree modification.

## Conclusion

Some documentation and engineering before making a Processwire site could help us a lot and save us time in the long run. And it help us to collaborate with other peers if we are inside a team or understanding what we made months after the project was done.

Made with <i class="fa fa-heart">&#9829;</i> by <a href="https://ninjas.cl" target="_blank">Ninjas.cl</a>.
