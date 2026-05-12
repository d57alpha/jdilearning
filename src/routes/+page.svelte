
<script>
    import { getContext } from 'svelte';
    let eduplatform = getContext("eduplatform");
    let jdilearning = getContext("jdilearning");

    console.log('in jdilearning, whats eduplatform', eduplatform)
    console.log('in jdilearning, whats jdilearning', jdilearning)

    import { onMount } from "svelte";

  	onMount(() => {
      window.parent.postMessage({ type: 'IFRAME_READY' }, eduplatform);
	  });

    function sendmsg1(){
      window.parent.postMessage("Message 1 from plugin to parent", eduplatform);
    }
    function sendmsg2(){
      window.parent.postMessage("Message 2 from plugin to parent", eduplatform);
    }

</script>

<!-- Svelte 5 style -->
<svelte:window onmessage={(event) => {
  console.log('plugin, try to get eduplatform message', event.origin, event.data);
  if (event.origin !== eduplatform) return;
  console.log('plugin, got eduplatform message', event.data);
 }}
 />

<h1>JDI Learning</h1>
<div class="flex flex-col">
  <!--
  <button class="btn btn-sm btn-soft btn-primary m-1"  onclick={sendmsg1}>msg 1 to parent</button>
  <button class="btn btn-sm btn-soft btn-primary m-1"  onclick={sendmsg2}>msg 1 to parent</button>
  -->
  <button class="btn btn-sm btn-soft btn-primary m-1"  >Dashboard</button>
  <button class="btn btn-sm btn-soft btn-primary m-1"  >Explain Highlighted text</button>
  <textarea class="textarea" placeholder="Question?"></textarea>
</div>
<!--

// This is for plugin in separate window
//window.opener.postMessage({ type: 'IFRAME_READY' }, eduplatform);
// This is for plugin in separate window
/*
function sendmsg1(){
  window.opener.postMessage("Message 1 from plugin to parent", eduplatform);
}
function sendmsg2(){
  window.opener.postMessage("Message 2 from plugin to parent", eduplatform);
}
*/
-->