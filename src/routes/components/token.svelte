<script>
export let segmentType = "empty";
export let segmentContent = "empty";
export let writtenText ;
export let id ;
export let currentId ;
let done = false;


import { createEventDispatcher } from "svelte";
const dispatch = createEventDispatcher();

  function markAsDone(content, input, id, currentId) {
  if (id === currentId) {
    console.log(id, currentId);
    if (content === input && !done) {
      done = true;
      dispatch('done', { id, done });
    }
  }
}

$: markAsDone(segmentContent, writtenText);


const typeToColorVar = {
  'Keyword': 'var(--color-keyword)',
  'Numeric': 'var(--color-numeric)',
  'String': 'var(--color-string)',
  'Punctuator': 'var(--color-punctuator)',
  'Identifier': 'var(--color-identifier)',
  'Boolean': 'var(--color-boolean)',
};

function getColorVar(type) {
  return typeToColorVar[type] || 'black'; // Fallback color if not found
}
</script>

<h1 style="color: {getColorVar(segmentType)};">
  {segmentContent}<br>
  {#if !done  }
  <h1>
  {#if id == currentId}
    {writtenText}
  {/if}
    </h1>
  {/if}
</h1>

<style>
  :root {
    --color-keyword: blue;
    --color-numeric: green;
    --color-string: gray;
    --color-punctuator: orange;
    --color-identifier: red;
    --color-boolean: purple;
    /* Define other colors for different segment types */
  }

  h1 {
    margin: 5px;
    padding: 5px;;
    border: 3px solid;
    border-radius: 10px;
    display: inline-block;
    
  }
</style>
