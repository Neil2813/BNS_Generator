# BNS Generator - Frontend

This directory contains the user interface for the BNS Generator, built with modern web technologies to provide a seamless and responsive experience for legal analysis.

## Tech Stack

*   **Core:** React 18, TypeScript, Vite.
*   **Styling:** Tailwind CSS, Shadcn UI (Radix UI primitives).
*   **Networking:** Axios (with custom interceptors).
*   **Routing:** React Router DOM.
*   **icons:** Lucide React.

## Project Structure

```
src/
├── components/     # Reusable UI components (InputForm, ResultsCard, Navbar)
├── lib/            # Utilities (API clients, helpers)
├── pages/          # Full page layouts (Analyze, Home)
├── types/          # TypeScript interface definitions
├── App.tsx         # Main application root
└── main.tsx        # Entry point
```

## Workflow

1.  **User Interaction**: Users interact mainly with the `AnalyzePage`.
2.  **State Management**: Complex form state (facts, victim details) is managed via `useState`.
3.  **API Communication**: 
    - The `predictAxios` function in `lib/apiAxios.ts` handles communication with the backend.
    - It supports request cancellation to prevent race conditions during rapid typing/submission.
4.  **Proxying**: Development requests to `/predict` are proxied via `vite.config.ts` to the backend running on port 8000 to avoid CORS issues (configured to handle both 5173 and 8080).

## Setup & Run

### Install Dependencies
```bash
npm install
```

### Start Development Server
```bash
npm run dev
```
The application will be available at `http://localhost:8080` (or `http://localhost:5173` depending on configuration).