<script>
import * as esprima from 'esprima';

import Token from './components/token.svelte'; 

let writtenText = '';

const code = 'const answer = 42';
const tokens = esprima.tokenize(code);
let currentId = 0;


function handleDone(e){
  if(e.detail.done){
    currentId++;
    console.log(currentId);
    writtenText = '';
  }
}



</script>

{#each tokens as token, i }
<Token 
    segmentType = {token.type}
    segmentContent = {token.value}
    {writtenText}
    id = {i}
    {currentId}
    on:done={handleDone}
  />

{/each}
<br>
<input type="text" bind:value={writtenText}>
<h1>{writtenText}</h1>

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
