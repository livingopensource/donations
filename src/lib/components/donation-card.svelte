<script lang="ts">
  import { Button } from "./ui/button"; // Adjust path as needed
  import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "./ui/card"; // Adjust path as needed
  import { Check } from "@lucide/svelte"; // Assuming lucide-svelte is installed

  // Props declaration in Svelte
  export let title: string;
  export let amount: string;
  export let description: string;
  export let features: string[];
  export let isPopular: boolean = false;
  export let onClick: () => void; // Svelte uses 'on:click' directly on elements, but for a component prop, it's a function
</script>

<Card
  class={`relative transition-all duration-300 hover:shadow-elegant hover:-translate-y-2 ${
    isPopular ? 'border-primary border-2 shadow-glow' : 'hover:border-primary/50'
  }`}
>
  {#if isPopular}
    <div class="absolute -top-3 left-1/2 transform -translate-x-1/2">
      <span class="bg-gradient-primary text-primary-foreground px-4 py-1 rounded-full text-sm font-semibold">
        Most Popular
      </span>
    </div>
  {/if}

  <CardHeader class="text-center pb-4">
    <CardTitle class="text-xl font-bold">{title}</CardTitle>
    <div class="text-3xl font-bold text-primary">{amount}</div>
    <CardDescription class="text-muted-foreground">{description}</CardDescription>
  </CardHeader>

  <CardContent class="space-y-4">
    <ul class="space-y-3">
      {#each features as feature, index (index)}
        <li class="flex items-center gap-3">
          <Check class="w-5 h-5 text-success flex-shrink-0" />
          <span class="text-sm">{feature}</span>
        </li>
      {/each}
    </ul>

    <Button
      variant={isPopular ? "default" : "outline"}
      size="lg"
      class="w-full mt-6"
      onclick={onClick}
    >
      Donate {amount}
    </Button>
  </CardContent>
</Card>