<script>
    import {Button, Input, Label} from 'flowbite-svelte'
    import {  Heading, P, A } from 'flowbite-svelte'
    import {get} from '$lib/utils.js'

    function divide(n1, n2) {
        let result = n1 / n2
        alert(result)
        result_preview = result
    }
    let n1;
    let n2;
    let result_preview;

    async function calculate(){
      let result = await get(`/divide?input_a=${n1}&input_b=${n2}`)
      document.location.href = `/result/${result.task_id}`
    }

    $: { if (n1 && n2) 
      {result_preview = n1/n2}
      }
</script>

    <div>
    <Heading tag="h2" customSize="text-4xl font-extrabold ">Payments tool for companies</Heading>
  <P class="my-4 text-gray-500">Start developing with an open-source library of over 450+ UI components, sections, and pages built with the utility classes from Tailwind CSS and designed in Figma.</P>
  <P class="mb-4">Deliver great service experiences fast - without the complexity of traditional ITSM solutions. Accelerate critical development work, eliminate toil, and deploy changes with ease.</P>
  </div>
  <div class="border-2 rounded-lg m-3 p-3 ">
   <div>
    <Label for="n1" class="mb-2">첫번째 숫자</Label>
    <Input type="number" id="n1" bind:value={n1}  required  />
  </div>
  <div>
    <Label for="n2" class="mb-2">두번째 숫자</Label>
    <Input type="number" id="n2" bind:value={n2} required />
  </div>

  <div class="mt-5">
    <Label class="mb-2">result_preview</Label>
    <P>{result_preview}</P>
  </div>

  <div class="flex justify-center">
  <Button class="m-5" on:click={() => {divide(n1,n2)}}> 나누자!</Button></div>

  <div class="flex justify-center">
    <Button class="m-5" on:click={() => {calculate()}}> backend 나누자!</Button></div>
</div>