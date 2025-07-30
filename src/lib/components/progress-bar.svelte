<script lang="ts">
  // Props declaration
  export let current: number;
  export let goal: number;
  export let label: string;

  // Reactive declaration for percentage
  $: percentage = Math.min((current / goal) * 100, 100);
</script>

<div class="w-full">
  <div class="flex justify-between items-center mb-2">
    <span class="text-sm font-medium text-foreground">{label}</span>
    <span class="text-sm text-muted-foreground">
      ${current.toLocaleString()} / ${goal.toLocaleString()}
    </span>
  </div>
  <div class="w-full bg-secondary rounded-full h-3 overflow-hidden">
    <div
      class="h-full bg-gradient-primary rounded-full transition-all duration-1000 ease-out shadow-glow"
      style="width: {percentage}%;"
    >
    </div>
  </div>
  <div class="text-xs text-muted-foreground mt-1">
    {percentage.toFixed(0)}% funded
  </div>
</div>