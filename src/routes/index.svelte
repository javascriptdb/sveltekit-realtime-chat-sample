<script>
    import {DatabaseArray, setServerUrl} from "@jsdb/sdk";
    const msgs = new DatabaseArray('msgs');
    const lastMinuteMessages = msgs.filter(message => message.date > (Date.now() - 60*1000));
</script>
<input on:keyup={e => e.key==='Enter' && msgs.push({text: e.target.value, date: Date.now()}) && (e.target.value = '')}/>
{#each $lastMinuteMessages || [] as msg} <div>{msg.text}</div> {/each}