# Patchwork Contribution Guidelines

Hey, thanks for contributing to Patchwork! We've collected some useful info
below, but if you have any questions please don't hesitate to [create an
issue][new-issue]!

## Process

Patchwork is developed on GitHub using the usual [GitHub flow][flow]. New
releases are usually at least a week apart, and code in `master` should always
work.

## Style

Please ensure all submitted code conforms to [StandardJS][standard]. This makes
our code more consistent and accessible for people who are working on Patchwork.

You can run `npm test` or `npx standard` to run the linter. Lots of small issues
can be automatically fixed using `npx standard --fix`.

## Structure

Our directory structure isn't static, but *generally* it's pretty consistent.

- **assets:** miscellaneous static files (images, HTML, XML, etc)
- **build:** files for building Patchwork with electron-builder
- **docs:** documents (like this one!) for working on Patchwork
- **dist:** temporary build files generated by electron-builder
- **lib:** JavaScript files that make Patchwork work!
  - **depject:** legacy modules written in the [depject][depject] style
  - **plugins:** modules written as [secret-stack plugins][plugins] 
- **locales:** translations of Patchwork in lots of different languages
- **scripts:** utility scripts designed to automate repetitive tasks
- **styles:** interface styles written with [micro-css][mcss]

## Debugging

You can increase Patchwork's logging output by making it more verbose. Try
launching Patchwork with different logging levels to change the amount of
console output:

```shell
npm start -- --logging.level info
```

## Modules

**Please consider depject deprecated in Patchwork!** It should be removed in
the future so please don't add new depject modules.

Currently [patch-settings][settings] is the only dependency that includes
depject modules, and that's for legacy reasons. Please don't treat this as a
best practice or follow its example.

Please do as much as possible in the Patchwork repo rather than splitting your
work into a bunch of modules. This makes it easier to maintain and update the
over all application. Only modularize code that are clearly reusable and make
sense as independent modules (algorithms, widgets, indexes) and use `require()`
to include them.

[depject]: https://github.com/depject/depject
[flow]: https://guides.github.com/introduction/flow/
[mcss]: https://github.com/mmckegg/micro-css
[new-issue]: https://github.com/ssbc/patchwork/issues/new
[plugins]: https://github.com/ssbc/secret-stack/blob/master/PLUGINS.md
[settings]: https://github.com/mixmix/patch-settings
[standard]: https://standardjs.com/
