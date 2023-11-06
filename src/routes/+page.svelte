<script>


import * as esprima from 'esprima';

import Token from './components/token.svelte'; 

let text = '';
const code = 'const answer = 42';

const tokens = esprima.tokenize(code);


</script>



<h1> MEAM </h1>

{#each tokens as token}
<Token segmentType = {token.type} segmentContent = {token.value} {text} />
{/each}
<br>
<input type="text" bind:value={text}>
<h1>{text}</h1>

<style>
h1{
  text-align: center;
  font-size: 50px;
}
input{
  text-align: center;
  font-size: 50px;
  width: 100%;
  height: 100px;
  border-radius: 10px;
  border: 3px solid;
  margin: 5px;
  padding: 5px;
}

</style>
