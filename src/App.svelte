<script lang="ts">
let win = 1000;
let bet = 100
const emoji = ['B', 'I', 'G']
let random = emoji
const roll = () => {
    random = [
        emoji[Math.round(Math.random() * 2)],
        emoji[Math.round(Math.random() * 2)],
        emoji[Math.round(Math.random() * 2)]
    ]
    if (random[0] === emoji[0] && random[1] === emoji[1] && random[2] === emoji[2]) win += bet * 20
    else if (random[0] === random[1] && random[1] === random[2]) win += bet * 4
    else win -= bet
}
</script>

<main class="w-full h-screen grid place-items-center">
    <div class="w-96 flex flex-col justify-center items-center text-white">
        <h2 class="font-semibold text-4xl">{win}</h2>
        
        <div class="relative mt-6 w-full">
            <div class="absolute top-12 left-[-32px] h-8 w-1 bg-white rounded-lg"></div>
            <div class="absolute top-12 right-[-32px] h-8 w-1 bg-white rounded-lg"></div>
            
            <div class="flex flex-row justify-around items-center w-full h-32 px-4 border-white border-4 rounded-lg">
                <h1 class="font-bold text-7xl text-center w-20">{random[0]}</h1>
                <div class="h-16 w-1 bg-white rounded-lg"></div>
                <h1 class="font-bold text-7xl text-center w-20">{random[1]}</h1>
                <div class="h-16 w-1 bg-white rounded-lg"></div>
                <h1 class="font-bold text-7xl text-center w-20">{random[2]}</h1>
            </div>
        </div>
        
        <div class="mt-2 w-full flex flex-row justify-between items-center">
            <button on:click={() => bet -= 10} disabled={bet <= 10} class="font-semibold text-xl w-32 py-3 border-white disabled:border-gray disabled:text-gray border-4 rounded-lg">-10</button>
            <p class="font-semibold text-xl">{bet}</p>
            <button on:click={() => bet += 10} class="font-semibold text-xl w-32 py-3 border-white border-4 rounded-lg">+10</button>
        </div>

        <button 
            class="mt-2 w-full p-3 font-semibold text-xl border-white border-4 rounded-lg"
            on:click={() => roll()}
        >Roll</button>
    </div>

    <h2 class="fixed bottom-10 text-white font-semibold opacity-30">99% of gamblers quit before their big win*</h2>
</main>
