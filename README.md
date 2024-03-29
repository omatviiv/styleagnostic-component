React template compatible with style agnostic components approach.
**Replace with component description and how to use info when template used**

**Dont forget to update new project with component specific basic data**
For simplicity all places that need attention are marked with:
```
  replace-oncreate:
```
So simply grep project for this phrase and go through the search results.

**For example in package.json pay attention to:**
- name
- description
- repository url
- bugs url
- homepage

Preferrably for the public demo page styleagnostic-theme-service should be
used which has ready simple components useful in the demo.

# why this component exists
**Provide explanation what kind of valuable logic or JSX structure this
component provides so that it can't be just part of the theme**

# Style agnostic component approach
Component is implemented in a way that in its JSX structure all tags and styles
are coming from one single conponent property `theme`.
Thanks to [styled-components](https://styled-components.com/) we can
create a map (`theme` property object) of styled components where each will
represent a specific node in the JSX structure of the component.

Thus when following the rule above we are achieving complete style separation
from the component structure and logic. And taking this into account there is
one more important rule for styleagnostic components:
- if component doesn't have any logic to be separated from the styling then
such component doesn't deserve a separate repo and can be simply part of the
theme.

# Build setup notes
The component is provided as is without any bundling or transformation.
It is responsibility of the destination project to build it and bundle.
Which means that this approach will only work in the infrastructure where
all projects share same eslint rules and similar build configuration.

This particular project also contains a component demo for convenience of
development and testing. And the demo project is very similar to 
[react-template](https://github.com/omatviiv/react-template#setup-notes).
Except that its buildable src/ is demo/ and stores not the component itself
but demo pages for the component.

## Build setup notes for component demo
`demo/` contains component demo application for developer convenience
of component development and testing.

This demo application is not hosted anywhere directly because its intented
for local development use but it is very useful to have a separate
components demo public web application that would have all the components
demonstrated in one web site where component user can see how to use
components with code examples.

**Demo requirements to satisfy manually:**
- Create `demo/index.tsx` public demo which should be independent from anything
inside `demo/` and can only import the component or optionally some external
libraries
- no import aliases are allowed in the `demo/index.tsx`
- demo/index.tsx may be reused in local demo but only as independent demo page
(i.e. without demo controls like menu etc.)
**Demo requirements to satisfy by using `npm run publish-all`:**
- This @demo tagged version should include the demo commponent which should be
located in the `demo/index.tsx` file.
- to reuse code from local demo app in the public consolidated components
demo there should be @demo tag npm published version which will contain one
demo component for the component which then could be imported in the
consolidated components demo app.

`demo/pages` can contain any number of demo pages to be used for specific
testing purposes: some specific test cases for cypress tests to make
testing more convenient isolated and focused on specific aspect of
the component.

## Webpack bundle analyzer
There is no need for bundle analyzer because there is no bundle.
Webpack is present here only for demo application which is only intended
for local development and its newer deployed anywhere. It is just demo/index.tsx
which is included into demo tagged npm version but it is provided as is
without any additional processing.

And same thing with ensuring that test files don't go into bundle - nothing
to ensure because there is no deployable bundle.


# Demo application webpack setup notes
As `demo/index.tsx` is reserved for the isolated default demo component for
ability to share default demo into some consolidated components demo web app
the demo application itself originates from `demo/main.tsx`.

# Component release notes
todo.md - is a file where some fixes or improvements are planned and documented
specifically for the component itself independently from the whole
styleagnostic project backlog.
Project backlog is for organising work between all of the components and themes
but todo.md is completely dedicated to the component related changes.

# Node & npm versions
Project created with node 20 and npm 10.
