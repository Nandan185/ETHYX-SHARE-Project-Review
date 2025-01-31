# ETHYX-SHARE-Project-Review
## Identified Mistakes and Corrections
### 1. Hardcoded Colors in Theme
Mistake: In src/theme/styles.ts, colors are hardcoded. This can make it difficult to maintain and update the theme.

Correction: Use a separate configuration file for colors and import them into your theme file.
```bash
export const colors = {
  brand: {
    100: "#E9E3FF",
    200: "#422AFB",
    300: "#422AFB",
    400: "#7551FF",
    500: "#422AFB",
    600: "#3311DB",
    700: "#02044A",
    800: "#190793",
    900: "#11047A",
  },
  // ...
};
```
```bash
import { colors } from './colors';

export const globalStyles = {
  colors,
};
```
### 2. Unused Imports
Mistake: In src/components/navbar/NavbarAdmin.tsx, there are unused imports such as useState and useEffect.

Correction: Remove unused imports to clean up the code.

### 3. Disabled ESLint
Mistake: ESLint is disabled using /* eslint-disable */. 

Correction: Enable ESLint and fix the issues it reports instead of disabling it.

### 4. Inconsistent Prop Types
Mistake: In src/views/admin/rtl/components/WeeklyRevenue.tsx, the props are typed as { [x: string]: any }, which is not specific and can lead to runtime errors.

Correction: Define specific prop types using TypeScript interfaces.
```bash
interface WeeklyRevenueProps {
  revenue: number;
  // other props
}

export default function WeeklyRevenue(props: WeeklyRevenueProps) {
```
### 5. Direct DOM Manipulation
Mistake: In src/app/auth/layout.tsx, direct DOM manipulation is used, which is not recommended in React.

Correction: Use React state and effects instead of direct DOM manipulation.
```bash
import { useEffect } from 'react';

useEffect(() => {
  if (isWindowAvailable()) {
    document.documentElement.dir = 'ltr';
  }
}, []);
```
### 6. Redundant Code
Mistake: In src/components/sidebar/Sidebar.tsx, there are redundant comments and unused variables.

Correction: Remove redundant comments and unused variables.
### 7. Hardcoded Strings
Mistake: In src/components/navbar/NavbarLinksAdmin.tsx, there are hardcoded strings that should be replaced with constants or localization.

Correction: Use constants or localization for strings.
```bash
const AP_TEXT = 'AP';

<Text fontSize={'xs'} fontWeight="bold" color={'white'}>
  {AP_TEXT}
</Text>
```
### 8. Missing Error Handling
Mistake:In src/app/layout.tsx, there is no error handling for potential issues during rendering.

 Correction: Add error boundaries or try-catch blocks where necessary.
```bash
import { ErrorBoundary } from 'react-error-boundary';

function ErrorFallback({ error, resetErrorBoundary }) {
  return (
    <div role="alert">
      <p>Something went wrong:</p>
      <pre>{error.message}</pre>
      <button onClick={resetErrorBoundary}>Try again</button>
    </div>
  );
}

export default function RootLayout({ children }: { children: ReactNode }) {
  return (
    <ErrorBoundary FallbackComponent={ErrorFallback}>
      {children}
    </ErrorBoundary>
  );
}
```
#### These are few mistakes which i have noticed during code review.
#### Implementing these corrections will enhance the code quality and maintainability of the project for future.
### Thank you.



