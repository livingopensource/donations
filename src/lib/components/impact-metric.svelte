<script lang="ts">
  // Props are declared using `export let` in Svelte
  export let number: string;
  export let label: string;
  export let description: string;
</script>

<div class="text-center p-6 rounded-lg bg-gradient-subtle border hover:shadow-card transition-all duration-300 animate-fade-in">
  <div class="text-4xl font-bold text-primary mb-2 animate-scale-in">
    {number}
  </div>
  <h3 class="text-lg font-semibold mb-2">{label}</h3>
  <p class="text-muted-foreground text-sm">{description}</p>
</div>