# Vaadin Flow and Component Java APIs Documentation

This is the documentation for Vaadin Flow, the new Java web framework available in Vaadin platform.
It also contains documentation on the Java APIs for Vaadin's web components.

This documentation is available in [vaadin.com/docs](https://vaadin.com/docs/v10/flow/Overview.html).
Any issues and contributions can be added here, or in vaadin.com/docs via the _report issues_ or _edit page_ actions.

## Structure

The documentation is split into the following modules:

- `docs-helpers` - sources for validating the code snippets to match the documentation
- `tutorial-*` - standalone tutorial projects that can be run individually
- `documentation` - the documentation files written in .asciidoc and tests

For verifying the changes made to the documentation, run `mvn verify` on the root level project.

### Adding new tutorials

When a new tutorial is added, the end result should be included as a new module that needs to be built before the `documentation` module.
The tutorial should use the `@CodeFor("path/file.asciidoc")` and `@Helper` annotations available from the `docs-helpers` dependency to map the source files to the tutorial code snippets in the `documentation` module.

Any added tutorial module can be included as a dependency to the `documentation` module,
so that the code snippets from the documentation can be verified. This requires couple steps:
- For web app projects with `war` packaging:
  - the `<appendClasses>` configuration must be enabled for the `maven-war-plugin`
  - The dependency should be to `documentation` added with `<classifier>classes</classifier>`
- The `TestTutorialCodeCoverage` class needs to know the source folder location (see static variables)
