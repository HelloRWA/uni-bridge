<script setup lang="ts">
const links = [
  {
    label: "Resources",
    children: [
      {
        label: "Help center",
      },
      {
        label: "Docs",
      },
      {
        label: "Roadmap",
      },
      {
        label: "Changelog",
      },
    ],
  },
  {
    label: "Features",
    children: [
      {
        label: "Affiliates",
      },
      {
        label: "Portal",
      },
      {
        label: "Jobs",
      },
      {
        label: "Sponsors",
      },
    ],
  },
  {
    label: "Company",
    children: [
      {
        label: "About",
      },
      {
        label: "Pricing",
      },
      {
        label: "Careers",
      },
      {
        label: "Blog",
      },
    ],
  },
];

const toast = useToast();

const email = ref("");
const loading = ref(false);

function onSubmit() {
  loading.value = true;

  setTimeout(() => {
    toast.add({
      title: "Subscribed!",
      description: "You've been subscribed to our newsletter.",
    });

    loading.value = false;
  }, 1000);
}

const appConfig = useAppConfig();
</script>

<template>
  <UFooter :ui="{ wrapper: 'pt-20' }">
    <template #top v-if="appConfig.showFooterTop">
      <UFooterColumns :links="links">
        <template #right>
          <form @submit.prevent="onSubmit">
            <UFormGroup label="Subscribe to our newsletter" :ui="{ container: 'mt-3' }">
              <UInput
                v-model="email"
                type="email"
                placeholder="Enter your email"
                :ui="{ icon: { trailing: { pointer: '' } } }"
                required
                size="xl"
                autocomplete="off"
                class="max-w-sm"
                input-class="rounded-full"
              >
                <template #trailing>
                  <UButton type="submit" size="xs" color="primary" :label="loading ? 'Subscribing' : 'Subscribe'" :loading="loading" />
                </template>
              </UInput>
            </UFormGroup>
          </form>
        </template>
      </UFooterColumns>
    </template>

    <template #left>
      <p class="text-sm text-gray-500 dark:text-gray-400">Copyright © {{ new Date().getFullYear() }}. All rights reserved.</p>
    </template>

    <template #right>
      <!-- <UColorModeButton size="sm" /> -->

      <UButton to="/awesome-ao" icon="i-material-symbols-auto-awesome" aria-label="AO Toolbox" color="gray" variant="ghost" />
      <UButton to="/toolbox" icon="i-material-symbols-light-service-toolbox-rounded" aria-label="AO Toolbox" color="gray" variant="ghost" />
      <UButton
        to="https://t.me/+ZpbsSCB5x4U4NTk1"
        target="_blank"
        icon="i-simple-icons-telegram"
        aria-label="Telegram"
        color="gray"
        variant="ghost"
      />
      <UButton to="https://github.com/HelloRWA" target="_blank" icon="i-simple-icons-github" aria-label="GitHub" color="gray" variant="ghost" />
      <UButton to="https://twitter.com/HelloRWA" target="_blank" icon="i-ri-twitter-x-line" aria-label="Twitter" color="gray" variant="ghost" />
    </template>
  </UFooter>
</template>
