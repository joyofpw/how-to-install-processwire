# Why and When Use ProcessWire?

![](https://user-images.githubusercontent.com/292738/158168576-fa0db21d-d113-4575-a609-99dadd0332b0.jpg)
> [Photo by Victor Aznabaev](https://unsplash.com/photos/pjTU9Edzc1g)
  

[ProcessWire](https://processwire.com/) is a free content management system (CMS) and framework (CMF) built to save you time and work the way you do. With all custom fields, a secure foundation, proven scalability and performance, _ProcessWire_ connects all of your content seamlessly, making your job fast, easy and fun.

### Pros

_ProcessWire_ have many goodies that make it one of the best choices for a _PHP CMS/CMF_.

**Slim and Modular** 

When other tools like Wordpress or _Drupal_ are too bloated and you need to monkey patch with third party plugins until a big mess is on the table. _ProcessWire_ can shine with its [powerful modular system](https://processwire.com/docs/modules/) , where you can create your own or choose among the vast library of modules. You can pick and make _ProcessWire_ as huge or as small as you need.

**Granular Control** 

_ProcessWire_ brings you granular control over your data and all the complex relationships between fields. Despite using a _MySQL_ database under the hood, it feels more like a tree or a graph schema, where each node can have parents or children and pointers to each other. You don't need to know _SQL_ since _ProcessWire_ have a simple to learn and use query engine inspired by _jQuery_ .

**It's PHP** 

It does not force you into a complex way of code organization, neither force you to learn a new template engine. Your code will be inside the _site/templates_ directory and from there it up to you how the files are organized, they are good ol' _PHP_ . Also since it's just _PHP_ you don't need a fancy _VPS_ or cloud servers, a regular shared hosting with _Cpanel_ would do for most projects. Where you can run _Wordpress,_ ProcessWire _will_ run.

However if your prefer some strategies. You can check:

- [Output strategies](https://processwire.com/docs/front-end/output/).
- [Wireframe framework](https://wireframe-framework.com/)
- [Alternatives](https://wireframe-framework.com/about/alternatives/)
- [Inertia.js Adapter](https://github.com/joyofpw/inertia)

**Roles and Permissions** 

The [roles and permissions](https://processwire.com/docs/user-access/) feature is easy to work with and you can create complex security requirements in record time.

**Multi Language is First Citizen**

You can easily create [multilanguage sites](https://processwire.com/docs/multi-language-support/) in no time. No need for wacky configurations. Need to support multiple languages? All you need to do is translate the text, and ProcessWire takes care of the rest.

**Hooks** 

ProcessWire is filled with [Hooks](https://processwire.com/docs/modules/hooks/) that are used and triggered on mostly every part of the system. This means you can alter the behaviour of system and third party modules, pages and system events, overriding their content or triggering events before, during or after their call. It's practically an [IFTTT](https://en.wikipedia.org/wiki/IFTTT) system inside _ProcessWire._ 

**Composer Ready** 

You can use _ProcessWire_ as a normal composer library and benefit from its huge amount of functions and helpers, and import other external libraries without problems to your site.

**Headless** 

If you need to only return JSON for a _Headless CMS_ experience, then it will be a piece of cake. You can choose to use a module like [AppAPI](https://github.com/Sebiworld/AppApi) or return the json using PHP's _json_encode()_ function. Maybe a [GraphQL](https://processwire.com/modules/process-graph-ql/) module too.

**Battle Tested** 

[More than ten years of continuos development](https://en.wikipedia.org/wiki/ProcessWire) . _ProcessWire_ has been in development since 2003 (with other names and cores).

**Awesome Admin** 

You have an awesome administration dashboard that is fully customizable both in PHP and Javascript (jQuery UI).

**Friendly Community** 

The [ _ProcessWire_ forums](https://processwire.com/talk/) is filled with friendly and welcoming folks. Please join and ask if you need help.

**Command Line Ready** 

_ProcessWire_ can work in console apps (terminal). You don't need a browser and can create command line scripts that interacts with the _ProcessWire_ apis. You can look at the [_Wireshell_](https://wireshell.github.io) project for an example console application that uses the _ProcessWire_ apis.

**Ever Green** 

Updating your _ProcessWire's core_ is a breeze. In most projects you just need to replace the _wire/_ directory with the new version and you are done. In contrast with _Wordpress_ where not updating your CMS is a huge security risk, _ProcessWire_ sites can be not updated for **years** and they will be fine. All the core updates are mostly new features and bug fixes. Security is strong with _ProcessWire._ 

### Cons

**Apache and MySQL only** 

_ProcessWire_  is strongly opinionated on these technologies. You can choose other web server like _nginx_, but the main security features are tested on _Apache_ only.

If you like other database systems like _PostgreSQL_ you are out of luck. At least if you want to use the _jQuery_ inspired engine from _ProcessWire_. That query engine is tailored to the bone for _MySQL._ Other databases compatible with _MySQL_ like _MariaDB_ are fine though.

**Migrations and Version Control** 

Working with multiple people on the same site can be a little difficult. Specially on how to send the changes in field relationships. If a site is in production it would be difficult to replicate the different changes in fields and page relationships from a dev enviroment. There are modules to address this issue though like [RockMigrations](https://processwire.com/talk/topic/21212-rockmigrations-easy-migrations-from-devstaging-to-live-server/) and [Version Control](https://processwire.com/modules/version-control/) . Be sure your team agrees on their strategy before sending a site to production.

Also _ProcessWire_ is heavily dependent on its query engine. If you need to execute custom SQL for fetching _PW's_ data, is best that you create a custom table. _ProcessWire_ stores its data on heavily optimized table structures that are not easy to grok.

**Testing** 

You will have to configure your own testing suite and testing engine. Since _ProcessWire_ is mainly tested manually in dev and production sites. It does not have an automated testing suite or tooling for that use case yet (afaik).

**Analytics and Telemetry** 

In the same situation as testing. You will have to configure your own analytics and telemetry engine. (afaik).

**At least basic PHP knowledge is required** 

Some _Wordpress_ folks may expect a point and click type of experience. But with _ProcessWire_ you require to learn a bit of PHP. Other folks that comes from other frameworks like _Laravel_ or _CakePHP_ can be a little confused on the terminology of _page, field and template_ . Both are easy to learn and with some experiments and asking you will get the hang of it.

### Use Cases

The following are use cases where _ProcessWire_ can shine:


* Read heavy systems. Where there are more read than write operations, for example a simple Blog or catalogue of products, informational site or landing page.


* A dashboard for other systems. You can leverage the beautiful _ProcessWire_ dashboard and via Hooks send the data to other systems apis. Having _ProcessWire_ as a single source of truth for the data.


* Small complexity relationships. Even though you can create complex parent - child relationships, is best to keep them slim and simple. If a more complex database structure is needed, maybe other framework can be used and use _ProcessWire_ as a client for that framework.


* Stable projects that do not need many changes (in the database structure) after being sent to production.



The following are use cases where _ProcessWire_ would not be recommended:


* Realtime systems. For example chat applications or long living operations. For these kind of systems there are better tools like [Elixir with Phoenix](https://www.phoenixframework.org/) .


* E-commerce. Although there are wonderful solutions for e-commerce like [Padloper.pw](https://padloper.pw/), this area is best to configure a dedicated e-commerce software and communicate via its apis, if you need something quick for e-commerce. Do try **Padloper** though, it could solve many common e-commerce scenarios. This is just a personal opinion, mainly because the time required to create a custom e-commerce. 


* Teams greater than 2. If the development team is one or two people per project it would be fine. With more people modifyng fields and templates it would be difficult to coordinate. Be sure to use migrations module or at least document each change for reproduction in the main production site.

## Conclusion

_ProcessWire_ is a wonderful system to build your next project if you use it within it's constraints. With its modular structure and simple requirements you can have a complex site ready using less effort.

