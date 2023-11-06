<script>
export let segmentType = "empty";
export let segmentContent = "empty";
export let text = "";
export let done = false;

$: if (text === segmentContent) {
  done = true;
}

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
{#if !done }
  {text}
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
