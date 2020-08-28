```tsx
<VimePlayer
  controls
  autoplay
  muted
  ref={player}
  currentTime={currentTime}
  on:vCurrentTimeChange={onTimeUpdate}
  on:vFullscreenChange={onFullscreenChange}
>
  <!-- Provider component is placed here. -->

  <VimeUi><!-- UI components are placed here. --></VimeUi>
</VimePlayer>
```

```html {2}
<script lang="ts">
  import { VimePlayer, VimeUi, usePlayerStore } from '@vime/svelte';

  let player: VimePlayer;
  let currentTime = 0;

  // OPTIONAL: If we prefer we could use the player store.
  const { paused } = usePlayerStore(player);
  $paused = false;
  $: console.log($paused);

  // Example function to showcase updating property.
  const seekForward = () => {
    currentTime += 5;
  };

  // Example function to showcase calling player method.
  const enterFullscreen = () => {
    player.enterFullscreen();
  };

  const onTimeUpdate = (event: CustomEvent<number>) => {
    currentTime = event.detail;
  };

  const onFullscreenChange = (event: CustomEvent<boolean>) => {
    const isFullscreen = event.detail;
    // ...
  };
</script>
```