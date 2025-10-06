<template>
  <UPageHero
    id="home"
    headline="Hi, I’m"
    title="Philip van Tonder"
    description="A passionate software developer who loves building clean, modern applications that solve real-world problems."
    :links="links"
  >
    <template #top>
      <HeroBackground />
    </template>
  </UPageHero>

  <UPageSection class="mt-6">
    <UMarquee :overlay="false">
      <UIcon name="i-simple-icons-mysql" class="size-12 text-blue-600" />
      <UIcon name="i-simple-icons-html5" class="size-12 text-orange-600" />
      <UIcon name="i-simple-icons-css3" class="size-12 text-blue-500" />
      <UIcon name="i-simple-icons-nuxtdotjs" class="size-12 text-green-500" />
      <UIcon name="i-simple-icons-php" class="size-12 text-indigo-500" />
      <UIcon name="i-simple-icons-vuedotjs" class="size-12 text-emerald-500" />
      <UIcon name="i-simple-icons-tailwindcss" class="size-12 text-sky-500" />
      <UIcon name="i-simple-icons-typescript" class="size-12 text-blue-500" />
      <UIcon name="i-simple-icons:nodedotjs" class="size-12 text-green-600" />
      <UIcon name="i-simple-icons-terraform" class="size-12 text-purple-600" />
      <UIcon name="i-simple-icons-docker" class="size-12 text-blue-400" />
      <UIcon name="i-simple-icons-amazonaws" class="size-12 text-orange-400" />
      <UIcon
        name="i-simple-icons-github"
        class="size-12 text-gray-800 dark:text-white"
      />
    </UMarquee>
  </UPageSection>

  <USeparator :ui="{ border: 'border-primary/30' }" />

  <UPageSection
    id="services"
    title="Services"
    description="Here's how I can help bring your ideas to life with modern, reliable, and scalable solutions."
  >
    <div
      class="absolute rounded-full -left-10 top-10 size-[300px] z-10 bg-primary opacity-30 blur-[200px]"
    />
    <div
      class="absolute rounded-full -right-10 -bottom-10 size-[300px] z-10 bg-primary opacity-30 blur-[200px]"
    />
    <UPageGrid>
      <UPageCard
        icon="heroicons:code-bracket"
        title="Development"
        description="I offer website development services that can be customized to your unique needs. I use off-the-shelf templates, and can also create fully custom websites from scratch, depending on the project requirements."
        spotlight
      />

      <UPageCard
        icon="heroicons:cloud-arrow-up"
        title="Hosting"
        description="I have experience hosting applications across a variety of technologies and needs. Whether it's a static website or a dynamic web application. I can provide reliable hosting solutions tailored to your specific requirements."
        spotlight
      />

      <UPageCard
        icon="heroicons:chart-bar"
        title="SEO"
        description="I offer SEO services for websites, utilizing proven strategies and techniques to increase their online presence and drive traffic."
        spotlight
      />

      <UPageCard
        icon="heroicons:lifebuoy"
        title="Support"
        description="I pride myself on delivering high-quality customer support to all of my clients."
        spotlight
      />

      <UPageCard
        icon="heroicons:sparkles"
        title="UI & Tailwind CSS"
        description="I design clean, modern UIs using Nuxt UI and Tailwind CSS v4, ensuring your site looks great and performs well."
        spotlight
      />

      <UPageCard
        icon="heroicons:server"
        title="Backend Integration"
        description="I can connect your frontend to APIs, databases, or third-party services, making your application dynamic and scalable."
        spotlight
      />
    </UPageGrid>
  </UPageSection>

  <USeparator :ui="{ border: 'border-primary/30' }" />

  <UPageSection
    id="projects"
    title="Projects"
    description="A selection of my recent work, showcasing my experience with modern technologies."
  >
    <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
      <UBlogPost
        title="Van Vuuren Urology"
        description=" Urologist / Robotics & Laser Prostatectomy Surgeon"
        image="/images/vanvuuren.png"
        to="https://vanvuurenurology.co.za/"
        target="_blank"
      />

      <UBlogPost
        title="Next Phase Rugby"
        description="Join South Africa's leading rugby clinic in Middelburg."
        image="/images/nextphaserugby.png"
        to="https://nextphaserugby.co.za"
        target="_blank"
      />

      <UBlogPost
        title="Castle Kids"
        description="A unique Preschool and ECD center"
        image="/images/castlekids.png"
        to="https://castlekids.co.za/"
        target="_blank"
      />
    </div>
  </UPageSection>

  <UPageSection
    id="contact"
    title="Get in Touch"
    description="Have a project in mind or just want to say hi? Fill in the form below and I’ll get back to you."
  >
    <div class="flex justify-center">
      <UForm
        :schema="schema"
        :state="submitForm"
        class="w-full max-w-lg space-y-6"
        @submit="onSubmit"
      >
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <UFormField label="Full Name" name="fullName">
            <UInput v-model="submitForm.fullName" class="w-full" />
          </UFormField>

          <UFormField label="Phone" name="phone">
            <UInput v-model="submitForm.phone" class="w-full" />
          </UFormField>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <UFormField label="Email" name="email">
            <UInput v-model="submitForm.email" class="w-full" />
          </UFormField>

          <UFormField label="Message" name="message">
            <UInput v-model="submitForm.message" class="w-full" />
          </UFormField>
        </div>

        <div
          class="g-recaptcha"
          data-sitekey="6LcOqeArAAAAAMF29B1GKuESIZUgzkDBbvKmdYfR"
          data-action="LOGIN"
        ></div>

        <UButton type="submit"> Submit </UButton>
      </UForm>
    </div>
    <LazyStarsBg />
  </UPageSection>
</template>

<script setup lang="ts">
import type { FormSubmitEvent } from "@nuxt/ui";
import * as z from "zod";

useHead({
  script: [
    {
      src: "https://www.google.com/recaptcha/api.js",
      async: true,
      defer: true,
    },
  ],
});

useSeoMeta({
  title: "Philip van Tonder | Software Developer",
  ogTitle: "Philip van Tonder | Software Developer",
  description:
    "Portfolio of Philip van Tonder, a passionate software developer building modern, scalable applications with Nuxt.js, Vue, Tailwind, Node.js, and AWS.",
  ogDescription:
    "Portfolio of Philip van Tonder, a passionate software developer building modern, scalable applications with Nuxt.js, Vue, Tailwind, Node.js, and AWS.",
  ogType: "website",
  ogUrl: "https://philipvtonder.co.za",
});

const links: any = ref([
  {
    label: "Get In Touch",
    to: "#contact",
    icon: "i-lucide-mail",
  },
]);

const submitForm = reactive({
  fullName: "",
  email: "",
  phone: "",
  message: "",
});

const schema = z.object({
  fullName: z.string().min(2, "Full name is required"),
  email: z.email("Invalid email"),
  phone: z.string().regex(/^\d{10}$/, "Phone number must be exactly 10 digits"),
  message: z.string().min(2, "Message must be at least 2 characters"),
});
type Schema = z.output<typeof schema>;

const toast = useToast();

const { $recaptchaLoaded, $recaptcha } = useNuxtApp();

async function onSubmit(event: FormSubmitEvent<Schema>) {
  // Get reCAPTCHA token from widget
  const token = (window as any).grecaptcha.getResponse();

  console.log("Token: ", token);

  if (!token) {
    toast.add({
      title: "Validation error",
      description: "Please check the reCAPTCHA box.",
      color: "error",
    });
    return;
  }

  try {
    // Send form data + token to your backend
    await $fetch("https://api.philipvtonder.co.za/contact-form", {
      method: "POST",
      body: {
        ...event.data, // fullName, email, phone, message
        token,
      },
    });

    toast.add({
      title: "Success",
      description: "The form has been submitted.",
      color: "success",
    });

    // Reset reCAPTCHA widget
    (window as any).grecaptcha.reset();
  } catch (err) {
    toast.add({
      title: "Error",
      description: "Something went wrong. Please try again.",
      color: "error",
    });
    console.error(err);
  }
}
</script>
