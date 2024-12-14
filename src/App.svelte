<script lang="ts">
  import Header from './lib/Header.svelte';
  import Section from './lib/Section.svelte';
  import './App.css';
  import rawData from './data.json';

  interface ItemModel {
    img: string;
    name: string;
    link?: string;
    time?: string;
    duration?: string;
  }

  interface SectionModel {
    title: string;
    type: string;
    items: ItemModel[];
  }

  interface DataModel {
    name: string;
    sections: SectionModel[];
  }

  let data: DataModel = rawData as DataModel;

  let info = {
    name: data.name || "Default Name",
    sections: data.sections || []
  };
</script>
<div class="container">
  <Header name={info.name} />

  {#if info.sections.length > 0}
    {#each info.sections as section (section.title)}
      <Section
              title={section.title}
              type={section.type}
              items={section.items}
      />
    {/each}
  {:else}
    <p>No sections available. Please check the data source.</p>
  {/if}
</div>