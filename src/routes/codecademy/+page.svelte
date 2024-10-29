<script>
  import codecademyData from "../../data/codecademy.json";
</script>

<h2>Codecademy Courses</h2>
<!--TODO: possibly create one JSON with nested objects for courses completed and current courses-->
<p>
  Simply telling you which courses I've taken is not an accurate representation
  of what I know. However, it is still beneficial that I at least show you what
  I've worked and am currently working with so you may have an understanding of
  where I'm at in my learning journey. You'll gain more understanding of my
  skills from my projects but here I'll be able to walk you through what
  knowledge I've aquired and how it benefits me moving forward.
</p>
<div>
  <ol>
    {#each Object.entries(codecademyData) as [key, values]}
      <li>
        <strong>{key}</strong>
        <ul>
          {#each values as value}
            <li>{value}</li>
          {/each}
        </ul>
      </li>
    {/each}
  </ol>
</div>

<style>
  h2,
  p {
    text-align: center;
  }
</style>
