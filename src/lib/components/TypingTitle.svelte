<script lang="ts">
    import {onMount} from "svelte";
    
    const speed = 140;
    const underscore_speed = 440;

    let title = "";
    let is_writing = false;
    let i = 0;
    let action_index = 0;
    let has_underscore = false;
    let delete_amount = 0;
    
    export let active = true;
    
    function idle_animation() {
        if (active || is_writing) {
            has_underscore = !has_underscore;
        } else {
            has_underscore = false;
        }
        setTimeout(idle_animation, underscore_speed)
    }
    
    onMount(() => {
        idle_animation();
    });
    
    export function beginWriting(new_title: string, idx: number, then: (idx: number) => void) {
        active = true;
        title = new_title;
        i = idx;
        action_index++;
        is_writing = true;
        writeC(idx, action_index, then);
    }
    
    function writeC(idx: number, action_idx: number, then: (idx: number) => void) {
        if (is_writing && action_index === action_idx) {
            i++;
            setTimeout(() => writeC(i, action_idx, then), speed * (title[idx] === " " ? 2 : 1));
        }
        if (idx >= title.length && action_index === action_idx) {
            is_writing = false;
            setTimeout(() => then(idx), speed * 20);
        }
    }
    
    export function deleteCharacters(amount: number, then: (idx: number) => void) {
        active = true;
        delete_amount = amount;
        action_index++;
        is_writing = true;
        deleteC(i, action_index, then)
    }

    function deleteC(idx: number, action_idx: number, then: (idx: number) => void) {
        if (is_writing && action_index === action_idx) {
            i--;
            delete_amount--;
            setTimeout(() => deleteC(i, action_idx, then), speed * (title[idx] === " " ? 2 : 1));
        }
        if (delete_amount == 0 && action_index === action_idx) {
            is_writing = false;
            setTimeout(() => then(idx), speed * 20);
        }
    }
</script>

<span class="inline-block h-6">{title.substring(0, i - 2) + (has_underscore? "_" : title.substring(i - 2, i - 1))}</span>