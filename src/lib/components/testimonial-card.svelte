<script lang="ts">
  import { Card, CardContent } from "$lib/components/ui/card"; 
  import { Quote } from "@lucide/svelte";

  // Svelte uses 'export let' for declaring component props
  export let quote: string;
  export let name: string;
  export let title: string;
  export let location: string;
  export let image: string;
</script>

<Card class="h-full hover:shadow-elegant transition-all duration-300 hover:-translate-y-1">
  <CardContent class="p-6">
    <Quote class="w-8 h-8 text-primary mb-4 opacity-60" />
    <blockquote class="text-gray-700 mb-6 leading-relaxed">
      "{quote}"
    </blockquote>
    <div class="flex items-center gap-4">
      <img
        src={image}
        alt={name}
        class="w-12 h-12 rounded-full object-cover border-2 border-primary/20"
      />
      <div>
        <div class="font-semibold text-foreground">{name}</div>
        <div class="text-sm text-muted-foreground">{title}</div>
        <div class="text-xs text-muted-foreground">{location}</div>
      </div>
    </div>
  </CardContent>
</Card>