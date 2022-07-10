<script lang="ts">
  let value = ``;
  let items = [];

  function addItem() {
    const id = Date.now();
    items = [
      ...items,
      {
        id,
        value,
      },
    ];
    value = ``;
  }

  function delItem(id) {
    items = items.filter((v) => v.id !== id);
  }
</script>

<main class="w-full p-6">
  <h1 class="text-red-400 text-4xl">Hello World!</h1>
  <h2>TODO APP</h2>
  <form on:submit|preventDefault={addItem} class="py-6">
    <input type="text" bind:value />
    <button type="submit">追加</button>
  </form>

  <div class="items">
    <ul>
      {#each items as item}
        <li class="flex mb-2">
          <p class="mr-2">{item.value}</p>
          <button on:click={delItem(item.id)}>削除</button>
        </li>
      {/each}
    </ul>
  </div>
</main>

<style lang="postcss" global>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
