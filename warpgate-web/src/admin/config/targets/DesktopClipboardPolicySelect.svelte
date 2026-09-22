<script lang="ts">
    import { FormGroup, Input } from '@sveltestrap/sveltestrap'
    import { DesktopClipboardPolicy } from 'admin/lib/api'
    import HelpText from 'admin/lib/HelpText.svelte'

    interface Props {
        clipboard: DesktopClipboardPolicy
    }

    let { clipboard = $bindable() }: Props = $props()
</script>

<h4 class="mt-4">Clipboard</h4>
<FormGroup floating label="Clipboard between the user and the target">
    <Input type="select" bind:value={clipboard}>
        <option value={DesktopClipboardPolicy.Bidirectional}>Both directions</option>
        <option value={DesktopClipboardPolicy.ToTarget}>
            Paste into the target only
        </option>
        <option value={DesktopClipboardPolicy.FromTarget}>
            Copy from the target only
        </option>
        <option value={DesktopClipboardPolicy.Disabled}>Disabled</option>
    </Input>
</FormGroup>
<HelpText>
    Enforced by Warpgate where it talks to the target, so it applies to the
    in-browser desktop and to native clients alike. "Paste into the target
    only" lets users bring text in while nothing copied on the target leaves it.
</HelpText>
