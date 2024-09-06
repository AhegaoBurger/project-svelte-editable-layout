# Svelte Editable Layout Dashboard

This project is a Svelte implementation of a drag-and-drop editable dashboard layout. It's inspired by and based on the NextJS implementation by [olliethedev](https://github.com/olliethedev/dnd-dashboard).

## Overview

This dashboard allows users to rearrange different components of the interface by dragging and dropping them. It's built using Svelte and leverages the following technologies:

- [Svelte](https://svelte.dev/)
- [SvelteKit](https://kit.svelte.dev/)
- [Swapy](https://github.com/olliethedev/swapy) for drag-and-drop functionality
- [shadcn-svelte](https://www.shadcn-svelte.com/) for UI components

## Features

- Drag-and-drop interface for rearranging dashboard components
- Responsive design
- Customizable layout sections
- Edit mode toggle for enabling/disabling drag-and-drop
- Persistent layout saving using local storage

## Getting Started

1. Clone the repository:
   ```
   git clone https://github.com/your-username/svelte-editable-layout-dashboard.git
   ```

2. Navigate to the project directory:
   ```
   cd svelte-editable-layout-dashboard
   ```

3. Install dependencies:
   ```
   npm install
   ```

4. Run the development server:
   ```
   npm run dev
   ```

5. Open your browser and visit `http://localhost:5000`

## Project Structure

- `src/routes/+page.svelte`: Main dashboard page
- `src/lib/components/swap-layout.svelte`: SwapLayout component for drag-and-drop functionality
- `src/lib/components/edit-switch.svelte`: Toggle switch for edit mode
- `src/lib/components/ui/`: UI components from shadcn-svelte

## Customization

You can customize the dashboard by modifying the sections in `src/routes/+page.svelte`. Each section is defined as a Svelte component and can be easily replaced or modified.

## Credits

This project is a Svelte adaptation of the [dnd-dashboard](https://github.com/olliethedev/dnd-dashboard) by [olliethedev](https://github.com/olliethedev). The original implementation was built using NextJS, and this project aims to bring similar functionality to the Svelte ecosystem.

## License

[MIT License](LICENSE)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
