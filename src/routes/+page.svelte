
<!-- Svelte 5 style -->
 <svelte:window onmessage={(event) => {
     //if (event.origin !== 'http://localhost:5174') return;
     console.log('plugin, try to get eduplatform message', event.origin, event.data);
     if (event.origin !== 'https://eduplatform-sigma-nine.vercel.app') return;
     console.log('plugin, got eduplatform message', event.data);
 }} />

 <!--

  Development -> Vercel
    http://localhost:5173/ -> https://jdilearning.vercel.app/
    http://localhost:5174/ -> https://eduplatform-sigma-nine.vercel.app/

  Vercel -> Development
    https://jdilearning.vercel.app/ -> http://localhost:5173/ 
    https://eduplatform-sigma-nine.vercel.app/ -> http://localhost:5174/

 -->

<script>
    import { onMount } from "svelte";

  	onMount(() => {
 		  console.log('jdi learning (child) component has mounted');
      //  Let the Parent (Education system) know the plugin is active
        //localhost
      //window.parent.postMessage({ type: 'IFRAME_READY' }, 'http://localhost:5174/');
      // Vercel
      window.parent.postMessage({ type: 'IFRAME_READY' }, 'https://eduplatform-sigma-nine.vercel.app');
	  });

    function sendmsg1(){
      // localhost
      //window.parent.postMessage("Message 1 from plugin to parent", 'http://localhost:5174/');
      // Vercel
      window.parent.postMessage("Message 1 from plugin to parent", 'https://eduplatform-sigma-nine.vercel.app');
    }
    function sendmsg2(){
      // localhost
      //window.parent.postMessage("Message 2 from plugin to parent", 'http://localhost:5174/');
      // Vercel
      window.parent.postMessage("Message 2 from plugin to parent", 'https://eduplatform-sigma-nine.vercel.app');
    }

</script>

<h1>JDI Learning</h1>
<button class="btn btn-soft btn-primary m-1"  onclick={sendmsg1}>Send Message 1 to Parent Education</button>
<button class="btn btn-soft btn-primary m-1"  onclick={sendmsg2}>Send Message 2 to Parent Education</button>

<!--

// This is for plugin in separate window
//window.opener.postMessage({ type: 'IFRAME_READY' }, 'http://localhost:5174/');
// This is for plugin in separate window
/*
function sendmsg1(){
  window.opener.postMessage("Message 1 from plugin to parent", 'http://localhost:5174/');
}
function sendmsg2(){
  window.opener.postMessage("Message 2 from plugin to parent", 'http://localhost:5174/');
}
*/
-->