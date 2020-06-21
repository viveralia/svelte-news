<script>
  export let title
  export let description
  export let author
  export let urlToImage
  export let url
  export let source
</script>

<div class="md:flex">
  <div class="md:flex-shrink-0">
    {#if urlToImage}
      <img 
      class="rounded-lg md:w-56 md:h-56 md:object-cover" 
      src={urlToImage} 
      alt={title}>
    {:else}
      <div class="rounded-lg w-full md:w-56 h-40 md:h-56 md:object-cover skeleton-box" />
    {/if}
  </div>
  <div class="mt-4 md:mt-0 md:ml-6">
    <div class="uppercase tracking-wide text-sm text-indigo-600 font-bold">
      {#if source || author}
        <h3>{source && source.name || author}</h3>
      {:else}
        <div class="rounded-md w-32 skeleton-box" style="height: 21px" />
      {/if}
    </div>
    <a 
      href={url}
      target="_blank"
      rel="noopener noreferrer"
      class="block mt-1 text-lg leading-tight font-semibold text-gray-900 hover:underline">
      {#if title}
        <h1>{title}</h1>
      {:else}
        <div class="rounded-md w-48 skeleton-box" style="height: 22px" />
      {/if}
    </a>
    <p class="mt-2 text-gray-600">
      {#if description}
        {description}
      {:else}
        <div class="rounded-md w-full skeleton-box mb-1" style="height: 18px" />
        <div class="rounded-md w-full skeleton-box mb-1" style="height: 18px" />
        <div class="rounded-md w-full skeleton-box" style="height: 18px" />
      {/if}
    </p>
  </div>
</div>

<style>
  .skeleton-box{
    position: relative;
    overflow: hidden;
    background-color: #e2e8f0;
  }

  .skeleton-box::after {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    transform: translateX(-100%);
    background-image: linear-gradient(
      90deg,
      rgba(255, 255, 255, 0) 0,
      rgba(255, 255, 255, 0.2) 20%,
      rgba(255, 255, 255, 0.5) 60%,
      rgba(255, 255, 255, 0)
    );
    animation: shimmer 3s infinite;
    content: '';
  }

  @keyframes shimmer {
    100% {
      transform: translateX(100%);
    }
  }
</style>