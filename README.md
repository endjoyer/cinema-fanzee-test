# Movie List Application

This is a frontend application built with Nuxt.js that displays a list of movies and provides detailed information about each movie. The application is designed in accordance with the provided Figma design file and meets the requirements outlined in the frontend test assignment.

## Features

- **Movie List**: Displays a list of 20 movies on the main page. And with the help of lazy loading, the rest are immersed.
- **Detail Page**: Clicking on a movie card navigates to a detailed page with more information about the selected movie.
- **Routing**: Utilizes Vue Router for navigation between the main page and detail pages.
- **Fade Transitions**: Smooth fade transitions between pages.
- **Responsive Design**: Supports mobile screens.

## Technologies Used

- **Vue 3**: The core framework for building the user interface.
- **Nuxt.js**: A framework for server-side rendered Vue applications.
- **Axios**: For handling HTTP requests to fetch movie data.

## Setup

To get started with the application, follow these steps:

1. **Clone the repository**:

   ```bash
   git clone https://github.com/endjoyer/cinema-fanzee-test
   cd cinema-fanzee-test
   ```

2. **Install dependencies**:

   You can use any of the following package managers:

   ```bash
   # npm
   npm install

   # pnpm
   pnpm install

   # yarn
   yarn install

   # bun
   bun install
   ```

3. **Run the development server**:

   Start the development server on `http://localhost:3000`:

   ```bash
   # npm
   npm run dev

   # pnpm
   pnpm dev

   # yarn
   yarn dev

   # bun
   bun run dev
   ```

## Production

To build the application for production, run:

    ```bash
    # npm
    npm run build

    # pnpm
    pnpm build

    # yarn
    yarn build

    # bun
    bun run build
    ```

## API Endpoints

The application fetches movie data from the following JSON files:

- **Movie List**: data\movies.json
- **Detail Page**: data\movieDetail.json

Make sure to replace the placeholders with the actual URLs of the JSON files.

Task: https://docs.google.com/document/d/1CuxAVnvg3d9uyAPsYH2mf7QcrbOZgv_uqKXRlrJ-SyY/edit?tab=t.0
