<script setup lang="ts">
interface FormData {
  firstName: string;
  lastName: string;
  email: string;
  password: string;
  confirmPassword: string;
  agreeToTerms: boolean;
}

interface FormErrors {
  firstName?: string;
  lastName?: string;
  email?: string;
  password?: string;
  confirmPassword?: string;
  agreeToTerms?: string;
}

const formData = ref<FormData>({
  firstName: '',
  lastName: '',
  email: '',
  password: '',
  confirmPassword: '',
  agreeToTerms: false
});

const errors = ref<FormErrors>({});
const isLoading = ref(false);

const validateForm = () => {
  errors.value = {};

  if (!formData.value.firstName.trim()) {
    errors.value.firstName = 'First name is required';
  }

  if (!formData.value.lastName.trim()) {
    errors.value.lastName = 'Last name is required';
  }

  if (!formData.value.email.trim()) {
    errors.value.email = 'Email is required';
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email)) {
    errors.value.email = 'Please enter a valid email';
  }

  if (!formData.value.password) {
    errors.value.password = 'Password is required';
  } else if (formData.value.password.length < 8) {
    errors.value.password = 'Password must be at least 8 characters';
  }

  if (formData.value.password !== formData.value.confirmPassword) {
    errors.value.confirmPassword = 'Passwords do not match';
  }

  if (!formData.value.agreeToTerms) {
    errors.value.agreeToTerms = 'You must agree to the terms and conditions';
  }

  return Object.keys(errors.value).length === 0;
};

const handleSubmit = async () => {
  if (!validateForm()) return;

  isLoading.value = true;

  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 1000));

    // Success - you can add your actual signup logic here
    console.log('Form submitted:', formData.value);

    // Reset form
    formData.value = {
      firstName: '',
      lastName: '',
      email: '',
      password: '',
      confirmPassword: '',
      agreeToTerms: false
    };

  } catch (error) {
    console.error('Signup error:', error);
  } finally {
    isLoading.value = false;
  }
};
</script>

<template>
  <div class="max-w-md mx-auto">
    <div class="card">
      <div class="text-center mb-8">
        <h2 class="text-3xl font-bold text-white mb-2">Create Account</h2>
        <p class="text-black-300">Join us today and start your journey</p>
      </div>

      <form @submit.prevent="handleSubmit" class="space-y-6">
        <!-- Name Fields -->
        <div class="grid grid-cols-2 gap-4">
          <div class="form-group">
            <label class="form-label">First Name</label>
            <input v-model="formData.firstName" type="text" class="input"
              :class="{ 'border-red-500': errors.firstName }" placeholder="John" />
            <p v-if="errors.firstName" class="form-error">{{ errors.firstName }}</p>
          </div>

          <div class="form-group">
            <label class="form-label">Last Name</label>
            <input v-model="formData.lastName" type="text" class="input" :class="{ 'border-red-500': errors.lastName }"
              placeholder="Doe" />
            <p v-if="errors.lastName" class="form-error">{{ errors.lastName }}</p>
          </div>
        </div>

        <!-- Email Field -->
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input v-model="formData.email" type="email" class="input" :class="{ 'border-red-500': errors.email }"
            placeholder="john@example.com" />
          <p v-if="errors.email" class="form-error">{{ errors.email }}</p>
        </div>

        <!-- Password Fields -->
        <div class="grid grid-cols-2 gap-4">
          <div class="form-group">
            <label class="form-label">Password</label>
            <input v-model="formData.password" type="password" class="input"
              :class="{ 'border-red-500': errors.password }" placeholder="••••••••" />
            <p v-if="errors.password" class="form-error">{{ errors.password }}</p>
          </div>

          <div class="form-group">
            <label class="form-label">Confirm Password</label>
            <input v-model="formData.confirmPassword" type="password" class="input"
              :class="{ 'border-red-500': errors.confirmPassword }" placeholder="••••••••" />
            <p v-if="errors.confirmPassword" class="form-error">{{ errors.confirmPassword }}</p>
          </div>
        </div>

        <!-- Terms Checkbox -->
        <div class="flex items-start space-x-3">
          <input v-model="formData.agreeToTerms" type="checkbox" id="agreeToTerms"
            class="h-4 w-4 text-white focus:ring-white border-black-600 rounded bg-black-800" />
          <div class="flex-1">
            <label for="agreeToTerms" class="text-sm text-black-300">
              I agree to the
              <a href="#" class="text-white hover:text-black-300 underline">Terms and Conditions</a>
              and
              <a href="#" class="text-white hover:text-black-300 underline">Privacy Policy</a>
            </label>
            <p v-if="errors.agreeToTerms" class="form-error mt-1">{{ errors.agreeToTerms }}</p>
          </div>
        </div>

        <!-- Submit Button -->
        <button type="submit" :disabled="isLoading" class="w-full btn-primary py-3 text-lg">
          <span v-if="isLoading" class="flex items-center justify-center">
            <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-black-950" xmlns="http://www.w3.org/2000/svg" fill="none"
              viewBox="0 0 24 24">
              <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
              <path class="opacity-75" fill="currentColor"
                d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
              </path>
            </svg>
            Creating Account...
          </span>
          <span v-else>Create Account</span>
        </button>
      </form>

      <div class="mt-6 text-center">
        <p class="text-black-300">
          Already have an account?
          <a href="#" class="text-white hover:text-black-300 font-medium">Sign in</a>
        </p>
      </div>
    </div>
  </div>
</template>
