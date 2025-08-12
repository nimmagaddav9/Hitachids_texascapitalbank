Technical + Coding interview

I’m a Core UI Developer with over 10 years of experience building .com websites using HTML5, CSS3, JavaScript, React.js, and Redux.

**United Airlines** – Worked on the React migration team converting .NET pages to React (using ATMOS components), implementing features like Forgot Password, Miles Pooling, TSA PreCheck, and Account Security. Used Redux-Saga for async flows and ensured WCAG accessibility compliance.

**Visa** – On the Accelerator team, remediated and developed MBDA modules (Application Management, Account Management, Portfolio Management, Analytics, etc.) for banking clients like Wells Fargo and Bank of America, with a focus on accessibility.

**Capital Group** – Built data visualizations for the DAVIS project using Highcharts + React, integrated into AEM, and developed the Creative Workbench tool for publishing articles.

## Architecture Designs and Their Use Cases – Based on My Experience

In my career, I’ve worked with multiple UI architecture patterns, selecting them based on scale, team structure, and performance needs.

### 1. Monolith SPA

- **Example:** Visa – Single React + Redux app for all modules.
- **Why:** Small team, aligned releases, easy to optimize with code splitting/lazy loading.

### 2. Modular Monolith

- **Example:** United Airlines – One repo, but features like TSA PreCheck, Miles Pooling, Sign-In in separate modules with own routing and state.
- **Why:** Monolith simplicity with scalable structure for onboarding and maintenance.

### 3. Micro Frontends

- **Example:** Capital Group – Separate React apps (Discover Search, Creative Workbench) integrated into AEM.
- **Why:** Independent deployments, different tech stacks, reduced bottlenecks.

### 4. Rendering Models

- **CSR:** Internal tools, no SEO needs.
- **SSR:** United.com public pages for faster TTFB.
- **SSG:** Static marketing pages at Capital Group.
- **Why:** Chosen per SEO, performance, and content freshness needs.

### 5. Backend-for-Frontend (BFF)

- **Example:** United Airlines – Node-based middleware aggregating multiple APIs.
- **Why:** Reduced network calls, optimized payloads, improved load time.

### 6. Design System

- **Example:** ATMOS (United Airlines), MUI-based (Capital Group).
- **Why:** Consistent branding, faster dev cycles, accessibility compliance.

### 7. Progressive Web App (PWA)

- **Example:** Field-use tools with offline caching.
- **Why:** Works in low-network areas, better mobile experience.

## SOLID Principles

SOLID is a set of five object-oriented design principles that make software more maintainable and scalable.

1. **S – Single Responsibility Principle (SRP)**

   - A class/component should have only one reason to change.
   - **Example:** In United Airlines projects, I kept UI components focused only on rendering, while data fetching was handled in services or Redux sagas.

2. **O – Open/Closed Principle (OCP)**

   - Open for extension, closed for modification.
   - **Example:** At Capital Group, I extended chart components with new props rather than modifying their core logic.

3. **L – Liskov Substitution Principle (LSP)**

   - Subclasses should be replaceable by their base classes without breaking functionality.
   - **Example:** In Visa’s component library, different form field components followed the same base API so they could be swapped without changing consumers.

4. **I – Interface Segregation Principle (ISP)**

   - Clients should not be forced to depend on interfaces they do not use.
   - **Example:** I designed smaller, focused TypeScript interfaces so components only imported the props they needed.

5. **D – Dependency Inversion Principle (DIP)**
   - High-level modules should not depend on low-level modules; both depend on abstractions.
   - **Example:** At United, UI components consumed data through API service interfaces, not directly from Axios calls, so switching APIs was easy.

**Why it matters:** Following SOLID in UI architecture improves reusability, testability, and scalability, especially in large codebases with multiple teams.

## Security in React + Redux Applications

1. **XSS Prevention** – Avoid `dangerouslySetInnerHTML`; sanitize all dynamic HTML.
2. **Authentication** – Use secure auth flows (OAuth2/OIDC), httpOnly cookies for tokens, and avoid storing sensitive data in Redux or localStorage.
3. **Authorization** – Implement route guards and role-based access control at both UI and API levels.
4. **API Security** – Always validate inputs server-side, use HTTPS, and apply CSRF tokens if needed.
5. **Data Protection** – Mask sensitive data in UI and logs, and avoid exposing API keys in client code.
6. **Dependency Safety** – Keep npm packages updated and run `npm audit` regularly.

---

## Performance in React + Redux Applications

1. **State Optimization** – Keep Redux store minimal; store server data in caching layers like React Query, not Redux, to avoid bloat.
2. **Code Splitting** – Use `React.lazy` and dynamic imports to load features on demand.
3. **Memoization** – Use `useMemo`, `useCallback`, and `React.memo` to prevent unnecessary re-renders.
4. **Reselect Selectors** – Use `reselect` to compute derived data efficiently.
5. **Batch Updates** – Use React’s automatic batching and avoid multiple dispatches in a row.
6. **Asset Optimization** – Compress images, enable gzip/Brotli, and remove unused code via tree shaking.
7. **Virtualization** – Use libraries like `react-window` for large lists or tables.

---

**Example from my experience:**  
At **United Airlines**, we optimized performance by splitting the account management features into lazy-loaded routes, memoizing expensive components, and using reselect for derived Redux state. For security, we implemented httpOnly cookies for tokens, added role-based route guards, and sanitized all dynamic content to prevent XSS.

Coding

## Types of Forms

1. **Controlled Forms**

   - React component controls form input values via state.
   - **Pros:** Easy validation, predictable state.
   - **Example:** Login form with `useState` or Redux store values.

2. **Uncontrolled Forms**

   - DOM maintains its own state, accessed via `ref`.
   - **Pros:** Less code for simple forms, no re-renders on every keystroke.
   - **Example:** Simple contact form without live validation.

3. **Hybrid Forms**

   - Mix of controlled and uncontrolled inputs.
   - **Example:** Search bar (controlled) + file upload (uncontrolled).

4. **Dynamic Forms**

   - Fields generated at runtime based on data or user actions.
   - **Example:** Multi-step survey where next step depends on previous answers.

5. **Multi-Step / Wizard Forms**

   - Broken into multiple pages or sections with progress tracking.
   - **Example:** Account creation process with profile, preferences, and confirmation steps.

6. **Form with State Management Library**

   - Managed via Redux, React Hook Form, or Formik.
   - **Example:** Large forms with shared data across multiple components.

7. **Accessible Forms**
   - WCAG-compliant with ARIA labels, keyboard navigation, and screen reader support.
   - **Example:** Visa project forms designed to meet ADA/WCAG 2.0 standards.

## Creating Forms in React

1. **Controlled Forms** – Inputs tied to React state via `value` and `onChange`. Best for validation and predictable state.
2. **Uncontrolled Forms** – Inputs store their own state, accessed via `ref` or `FormData`. Best for simple or quick forms.
3. **Template Forms in React** – No direct Angular-style system; use uncontrolled forms with JSX as the template and read values on submit.
