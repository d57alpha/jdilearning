
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
<button class="btn btn-soft btn-primary m-1"  onclick={sendmsg1}>Send Message 1 to Parent Education</button>
<button class="btn btn-soft btn-primary m-1"  onclick={sendmsg2}>Send Message 2 to Parent Education</button>

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