<!-- App.svelte -->
<script>
    import Contoh1 from './Buttons.svelte' //Contoh 1
    // import component from Buttons.svelte as "Tombol"
    import Container from './Container.svelte'
    let showContext = false;

    // Contoh 2
    import EmojiButton from './EmojiButton.svelte'
    const emojis=[
        {value:"😄",expression:"Happy Face"},
        {value:"😢",expression:"Sad Face"},
        {value:"🎮",expression:"EPIC GAMERS MOMENT TIME"},
        {value:"😡",expression:"Angrwy Face"}
    ]
    let emoji='❌';
    let text='no emotion';
    
    // Contoh 3
    import EmojiReactivity from './EmojiReactivity.svelte'
    import story from './story.js'
    import ReactivityButton from './ReactivityButton.svelte' 
    let reactbutton = story[0].buttons //buttons reffer to 'buttons' array
    let score = 0;
    $: smileySays="Hi there, your score is: " + score;
    
</script>
<!-- This is your View -->
<!-- {console.log({score})} -->
<Container>
    <section class="item">
        <h3>1. Button with Dispatcher</h3>
    <div class = "Menu">
        <Contoh1 on:NamaEventDiMainApp={(eventVar)=>{showContext=eventVar.detail}}/>
        <!-- eventVar.detail refers to data passed from Buttons.svelte component-->
    </div>    
    {#if showContext}
        <p>
	True value dispatched ✅
        </p>
    {:else}
        <p>
	False value dispatched ❌
        </p> 
    {/if}   
    </section>
    <section class="item">
        <h3>2. Button with Dispatcher + Pass Data</h3>
        <p class="explainer">this one dispatch some <strong>value from main</strong> to component button then take that value to button component then pass 2nd value to another text/var in main<p>
        <p>My mood right now : {emoji}
        <div class="row">
            <EmojiButton {emojis} on:clickEmoji={(asdf)=> {emoji=asdf.detail.value}}/>
        </div>
    </section>
    <section class="item">
        <h2>3. Reactivity using $:</h2>
        <h3>{smileySays}</h3>
        <!-- "reacbutton" from ReactivityButton should be exported as a same name to main -->
        <div class="row">
            <EmojiReactivity/>
            <ReactivityButton {reactbutton} on:emojireactive={(bab3)=> {score+=bab3.detail.value}}/>
        </div>
    </section>
</Container>
<!-- End of View -->
<style>
	div{
		font-weight: bold;
		width : 100%;
		text-align:center;
	}
	:global(*){
		box-sizing:border-box;
	}
	:global(body,html){
		margin:0;
        padding:0;
		height:100vh;
    }
    :global(button){
        border-radius: 5px;
        border : 1px solid white;
        /* background-color: #2F2F2F; */
        color:black;
    }
    :global(button:hover){
        background-color:#464646;
        color:white;
    }
    .row{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .item{
        height: auto;
        margin-bottom: 10px;
        border:1px solid white;
        border-radius:5px;
        padding:10px;
        width: 50vw;
    }
    .explainer{
        background-color: white;
        border-radius: 5px;
        padding:4px;
    }
    P{
        text-align:center;
    }
    h3{
        text-align:center;
    }
    h2{
        text-align:center;
    }
</style>