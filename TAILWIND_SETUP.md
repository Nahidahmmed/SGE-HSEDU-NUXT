# Tailwind CSS Setup Guide for SGE-HSEDU-NUXT

## 🎨 What's Been Configured

Your Nuxt.js project now has a complete Tailwind CSS setup with a **black and white theme** using the color `#121212`:

- ✅ Tailwind CSS v6.14.0 installed and configured
- ✅ **Black and White Theme** with primary color `#121212`
- ✅ Custom CSS file with Tailwind directives
- ✅ Tailwind configuration file with custom theme extensions
- ✅ **Navigation Menu** with responsive design
- ✅ Pre-built component classes for buttons, forms, and cards
- ✅ Custom color palette (black variants and white)
- ✅ Responsive design utilities
- ✅ Custom animations and transitions
- ✅ **Complete Page Structure** (Home, About, Services, Contact)

## 🚀 Getting Started

### 1. Development Server
```bash
npm run dev
```

### 2. Build for Production
```bash
npm run build
```

## 🎯 Available Custom Classes

### Button Components
```vue
<!-- Primary Button (White background, Black text) -->
<button class="btn-primary">Click Me</button>

<!-- Secondary Button (Dark background, White text) -->
<button class="btn-secondary">Secondary Action</button>

<!-- Outline Button (Transparent with white border) -->
<button class="btn-outline">Outline Style</button>

<!-- Custom Sizes -->
<button class="btn-primary px-8 py-3 text-lg">Large Button</button>
```

### Form Components
```vue
<!-- Form Group -->
<div class="form-group">
  <label class="form-label">Email</label>
  <input class="input" type="email" placeholder="Enter email" />
  <p class="form-error">Error message</p>
</div>

<!-- Input Field -->
<input class="input" type="text" placeholder="Enter text" />

<!-- Form Label -->
<label class="form-label">Field Name</label>

<!-- Form Error -->
<p class="form-error">Error message here</p>
```

### Card Components
```vue
<!-- Basic Card -->
<div class="card">
  <h3>Card Title</h3>
  <p>Card content goes here</p>
</div>

<!-- Card with Hover Effects -->
<div class="card hover:shadow-glow transition-all duration-300 hover:-translate-y-2">
  <h3>Interactive Card</h3>
  <p>This card has hover effects</p>
</div>
```

### Navigation Components
```vue
<!-- Navigation Link -->
<a class="nav-link">Home</a>

<!-- Active Navigation Link -->
<a class="nav-link nav-link-active">About</a>
```

### Utility Classes
```vue
<!-- Text Gradient -->
<h1 class="text-gradient">Gradient Text</h1>

<!-- Background Gradients -->
<div class="bg-gradient-primary">Primary Gradient</div>
<div class="bg-gradient-secondary">Secondary Gradient</div>

<!-- Animations -->
<div class="animate-fade-in">Fades in</div>
<div class="animate-slide-up">Slides up</div>
```

## 🎨 Custom Color Palette

### Black Colors (Primary Theme)
- `bg-black-50` to `bg-black-950` (including `#121212` as `bg-black-950`)
- `text-black-300` (for secondary text)
- `text-black-400` (for muted text)
- `border-black-800` (for borders)

### White Colors
- `text-white` (for primary text)
- `bg-white` (for button backgrounds)
- `border-white` (for white borders)

### Usage Examples
```vue
<div class="bg-black-950 text-white p-4 rounded-lg">
  Primary Background (#121212)
</div>

<div class="bg-black-900 text-white p-4 rounded-lg">
  Secondary Background
</div>

<div class="bg-white text-black-950 p-4 rounded-lg">
  White Background with Black Text
</div>
```

## 📱 Responsive Design

Tailwind CSS provides responsive utilities out of the box:

```vue
<!-- Mobile first approach -->
<div class="text-lg md:text-xl lg:text-2xl">
  Responsive text size
</div>

<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  Responsive grid
</div>

<div class="p-4 md:p-6 lg:p-8">
  Responsive padding
</div>
```

## 🔧 Custom Configuration

### Tailwind Config (`tailwind.config.js`)
- Custom black color palette with `#121212` as primary
- Extended spacing values
- Custom border radius
- Custom shadows
- Font family extensions

### CSS File (`app/assets/css/main.css`)
- Base layer styles with black theme
- Component layer styles
- Utility layer styles
- Custom animations
- Navigation-specific styles

## 📝 Best Practices

### 1. Use Component Classes
Instead of writing long utility classes, use the pre-built component classes:
```vue
<!-- ❌ Don't do this -->
<button class="inline-flex items-center justify-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-offset-2 transition-colors duration-200 bg-white text-black-950 hover:bg-gray-100 focus:ring-gray-300">
  Button
</button>

<!-- ✅ Do this instead -->
<button class="btn-primary">
  Button
</button>
```

### 2. Leverage Custom Utilities
```vue
<!-- Use custom utilities for common patterns -->
<div class="card animate-fade-in">
  <h3 class="text-gradient">Title</h3>
  <p>Content</p>
</div>
```

### 3. Responsive Design
```vue
<!-- Always start with mobile and scale up -->
<div class="text-base md:text-lg lg:text-xl xl:text-2xl">
  Responsive typography
</div>
```

## 🎨 Component Examples

### Navigation Bar
```vue
<nav class="bg-black-950 border-b border-black-800">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between h-16">
      <div class="flex items-center">
        <h1 class="text-2xl font-bold text-gradient">SGE-HSEDU</h1>
      </div>
      
      <div class="hidden md:flex items-center space-x-8">
        <a href="#" class="nav-link">Home</a>
        <a href="#" class="nav-link">About</a>
        <a href="#" class="nav-link">Services</a>
        <a href="#" class="nav-link">Contact</a>
        <button class="btn-primary">Get Started</button>
      </div>
    </div>
  </div>
</nav>
```

### Hero Section
```vue
<section class="bg-gradient-primary text-white py-20">
  <div class="container mx-auto px-4 text-center">
    <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in">
      Welcome to Our Platform
    </h1>
    <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90 animate-slide-up text-black-300">
      Build amazing applications with modern tools and best practices
    </p>
    <div class="flex flex-col sm:flex-row gap-4 justify-center">
      <button class="btn-primary px-8 py-3 text-lg">
        Get Started
      </button>
      <button class="btn-outline px-8 py-3 text-lg">
        Learn More
      </button>
    </div>
  </div>
</section>
```

### Feature Grid
```vue
<div class="grid md:grid-cols-3 gap-8">
  <div class="card text-center hover:shadow-glow transition-all duration-300 hover:-translate-y-2">
    <div class="text-6xl mb-4">🎨</div>
    <h3 class="text-2xl font-semibold text-white mb-3">Modern Design</h3>
    <p class="text-black-300">Beautiful and responsive design</p>
  </div>
  
  <div class="card text-center hover:shadow-glow transition-all duration-300 hover:-translate-y-2">
    <div class="text-6xl mb-4">⚡</div>
    <h3 class="text-2xl font-semibold text-white mb-3">Fast Performance</h3>
    <p class="text-black-300">Optimized for speed and efficiency</p>
  </div>
  
  <div class="card text-center hover:shadow-glow transition-all duration-300 hover:-translate-y-2">
    <div class="text-6xl mb-4">🚀</div>
    <h3 class="text-2xl font-semibold text-white mb-3">Easy to Use</h3>
    <p class="text-black-300">Simple and intuitive experience</p>
  </div>
</div>
```

## 🗂️ Page Structure

Your project now includes these pages:

- **Home** (`/`) - Landing page with hero, features, and CTA
- **About** (`/about`) - Company information and values
- **Services** (`/services`) - Service offerings grid
- **Contact** (`/contact`) - Contact form and information

## 🚀 Next Steps

1. **Customize Colors**: Modify the black color palette in `tailwind.config.js`
2. **Add Components**: Create more reusable component classes in `main.css`
3. **Extend Theme**: Add custom spacing, shadows, or animations
4. **Build Pages**: Use the provided classes to build beautiful pages
5. **Add Content**: Fill in the pages with your actual content

## 📚 Resources

- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Nuxt.js Documentation](https://nuxt.com/docs)
- [Vue.js Documentation](https://vuejs.org/guide/)

## 🎉 You're All Set!

Your project now has a professional **black and white theme** with:
- ✅ Beautiful navigation menu
- ✅ Complete page structure
- ✅ Custom component system
- ✅ Responsive design
- ✅ Modern black theme using `#121212`

Start building amazing interfaces with your new minimal, elegant design system! 🎨✨
