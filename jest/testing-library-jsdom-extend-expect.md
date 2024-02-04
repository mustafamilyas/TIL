# Cannot find module '@testing-library/jest-dom/extend-expect' on 'jest.setup.js'

One of the possible cause of this error is you are using @testing-library/jest-dom@6 or above. As this module already removed from the package, you either use previous version of @testing-library/jest-dom (v5) or use the default import.

```javascript
// jest.setup.js
import "@testing-library/jest-dom";
```

### Reference

- [Cannot find module '@testing-library/jest-dom/extend-expect' from 'jest.setup.js' | Stackoverflow](https://stackoverflow.com/questions/77328459/cannot-find-module-testing-library-jest-dom-extend-expect-from-jest-setup-js)
- [https://github.com/testing-library/jest-dom/releases/tag/v6.0.0](@testing-library/jest-dom)
