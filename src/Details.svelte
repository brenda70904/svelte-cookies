<script>
  const items = [
    { id: 1, imgSrc: 'https://placehold.co/400', text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.' },
    { id: 2, imgSrc: 'https://placehold.co/400', text: 'Curabitur vel odio vitae augue tincidunt cursus vitae ac eros.' },
    { id: 3, imgSrc: 'https://placehold.co/400', text: 'Suspendisse vestibulum nisl non fringilla malesuada.' },
    { id: 4, imgSrc: 'https://placehold.co/400', text: 'Fusce non odio ut erat tincidunt facilisis in ac elit.' },
  ];
</script>

<style>
  .details {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1rem;
    justify-items: center;
  }

  .detail-item {
    text-align: center;
    padding: 1rem;
  }

  .detail-item img {
    max-width: 100%;
    height: auto;
    margin-bottom: 1rem;
  }
</style>

<div class="details">
  {#each items as { id, imgSrc, text }}
    <div class="detail-item">
      <img src={imgSrc} alt="Placeholder image" />
      <p>{text}</p>
    </div>
  {/each}
</div>
