<script>
    let display = $state('')
    let cparA = $state(0)
    let cparF = $state(0)
    let i = 1
    let backdisp = $state()


    function press(c){
        display += c
    }

    function clear(){
        display = ''
    }

    function calc(){ 
        backdisp = display
        if (backdisp.includes)
        display = eval(display);
        display = String(display);

    }

    function backspace(){
        if (display.length > 0) {
            display = display.slice(0, display.length - 1)
        }
    }

    function invert(){
        display = display *= -1
    }

</script>
<div class="text-center mt-2">
<input class="form-control" readonly bind:value={display}/>
<table class="table table-sm table-borderless">
    <tbody>
        <tr>
            <td><button type="button" class="btn btn-danger w-100"  onclick={() => clear()}>C</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => invert()}>+-</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('%')}>MOD</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('Math.log10(')}>Log</button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-danger w-100"  onclick={() => backspace()}>CE</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('(')}>&lpar;</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press(')')}>&rpar;</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('/')}>/</button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press(`Math.sqrt(`)}>√</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('Math.round(')}>RND</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('**3')}>X³</button></td>
            <td><button type="button" class="btn btn-info w-100"  onclick={() => press('/100')}>%</button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(7)}>7</button></td>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(8)}>8</button></td>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(9)}>9</button></td>
            <td><button type="button" class="btn btn-warning w-100"  onclick={() => press('*')}>x</button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(4)}>4</button></td>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(5)}>5</button></td>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(6)}>6</button></td>
            <td><button type="button" class="btn btn-warning w-100"  onclick={() => press('-')}>-</button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(1)}>1</button></td>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(2)}>2</button></td>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(3)}>3</button></td>
            <td rowspan="2" style="height: 0;"><button type="button" class="btn btn-warning w-100 h-100" onclick={() => press('+')}>+</button></td>
        </tr>
        <tr>
            <td><button type="button" class="btn btn-primary w-100"  onclick={() => press(0)}>0</button></td>
            <td><button type="button" class="btn btn-warning w-100"  onclick={() => press('.')}>&sdot;</button></td>
            <td><button type="button" class="btn btn-warning w-100"  onclick={() => calc()}>=</button></td>
        </tr>
    </tbody>
</table>
</div>