<script>
    import SkillBar from './components/SkillBar.svelte';

    const frameworksRank = [
        {
            framework: 'Svelte',
            percent: 95,
            color: 'coral',
            delay: 1000
        },
        {
            framework: 'Vue',
            percent: 70,
            color: 'lime',
            delay: 750
        },
        {
            framework: 'React',
            percent: 25,
            color: 'cornflowerblue',
            delay: 500
        },
        {
            framework: 'Angular',
            percent: 40,
            color: 'crimson',
            delay: 250
        }
    ];
</script>

<!-- MarkUp -->
<section>
    <h2>Frameworks rank</h2>

    {#each frameworksRank as { framework, percent, color, delay }}
        <SkillBar {framework} {percent} {color} {delay} />
    {/each}
</section>

<!-- <p>Vue</p>
<div class="container">
  <div class="skills vue">60%</div>
</div>

<p>React</p>
<div class="container">
  <div class="skills react">25%</div>
</div>

<p>Angular</p>
<div class="container">
  <div class="skills angular">20%</div>
</div> -->

<style>
    section {
        padding: 2rem 10%;
    }

/* .vue {width: 60%; background-color: #2196F3;} 
.react {width: 25%; background-color: #f44336;} 
.angular {width: 20%; background-color: #808080;}  */

</style>