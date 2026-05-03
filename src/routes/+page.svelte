<script>
    import { onMount } from "svelte";

  	onMount(() => {
 		  console.log('jdi learning (child) component has mounted');

      //  Let the Parent (Education system) know the plugin is active

        // This is for plugin in iframe
        //window.parent.postMessage({ type: 'IFRAME_READY' }, 'http://localhost:5174/');
        window.parent.postMessage({ type: 'IFRAME_READY' }, 'https://eduplatform-sigma-nine.vercel.app/');

        // This is for plugin in separate window
        //window.opener.postMessage({ type: 'IFRAME_READY' }, 'http://localhost:5174/');

        window.addEventListener('message', (event) => {
          // Security Check: Always verify the origin!
          // if (event.origin !== "https://trusted-domain.com") return;
          //console.log('Received data:', event.data.payload);
          console.log('jdi learning (child) Received data:', event.data, event.origin);
      });
	  });

    // This is for plugin in iframe
    function sendmsg1(){
      //window.parent.postMessage("Message 1 from plugin to parent", 'http://localhost:5174/');
      window.parent.postMessage("Message 1 from plugin to parent", 'https://eduplatform-sigma-nine.vercel.app/');
    }
    function sendmsg2(){
      //window.parent.postMessage("Message 2 from plugin to parent", 'http://localhost:5174/');
      window.parent.postMessage("Message 2 from plugin to parent", 'https://eduplatform-sigma-nine.vercel.app/');
    }

    // This is for plugin in separate window
    /*
    function sendmsg1(){
      window.opener.postMessage("Message 1 from plugin to parent", 'http://localhost:5174/');
    }
    function sendmsg2(){
      window.opener.postMessage("Message 2 from plugin to parent", 'http://localhost:5174/');
    }
    */
   let b = "bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded m-1"
</script>

<h1>JDI Learning</h1>
<button class={b}  onclick={sendmsg1}>Send Message 1 to Parent Education</button>
<button class={b}  onclick={sendmsg2}>Send Message 2 to Parent Education</button>
