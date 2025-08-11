<script setup lang="ts">
interface Props {
  label?: string;
  to?: string;
  variant?: 'primary' | 'secondary' | 'outline';
  size?: 'sm' | 'md' | 'lg';
  disabled?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  variant: 'primary',
  size: 'md',
  disabled: false
});

const buttonClasses = computed(() => {
  const baseClasses = 'btn inline-flex items-center justify-center font-medium rounded-md transition-all duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2';

  const variantClasses = {
    primary: 'bg-white text-black-950 hover:bg-gray-100 focus:ring-gray-300',
    secondary: 'bg-black-800 text-white hover:bg-black-700 focus:ring-black-600',
    outline: 'border-2 border-white text-white bg-transparent hover:bg-white hover:text-black-950 focus:ring-white'
  };

  const sizeClasses = {
    sm: 'px-3 py-1.5 text-sm',
    md: 'px-4 py-2 text-base',
    lg: 'px-6 py-3 text-lg'
  };

  const disabledClasses = props.disabled ? 'opacity-50 cursor-not-allowed' : '';

  return `${baseClasses} ${variantClasses[props.variant]} ${sizeClasses[props.size]} ${disabledClasses}`;
});
</script>

<template>
  <NuxtLink v-if="to && !disabled" :to="to" :class="buttonClasses">
    <slot>{{ label }}</slot>
  </NuxtLink>

  <button v-else :class="buttonClasses" :disabled="disabled" type="button">
    <slot>{{ label }}</slot>
  </button>
</template>
