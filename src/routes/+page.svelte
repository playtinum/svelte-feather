<script lang="ts">
    import Icon from "../lib/icon/Icon.svelte";

    import { fade } from "svelte/transition";

    const featherIcons: string[] = [
        "activity",
        "airplay",
        "alert-circle",
        "alert-octagon",
        "alert-triangle",
        "align-center",
        "align-justify",
        "align-left",
        "align-right",
        "anchor",
        "aperture",
        "archive",
        "arrow-down-circle",
        "arrow-down-left",
        "arrow-down-right",
        "arrow-down",
        "arrow-left-circle",
        "arrow-left",
        "arrow-right-circle",
        "arrow-right",
        "arrow-up-circle",
        "arrow-up-left",
        "arrow-up-right",
        "arrow-up",
        "at-sign",
        "award",
        "bar-chart-2",
        "bar-chart",
        "battery-charging",
        "battery",
        "bell-off",
        "bell",
        "bluetooth",
        "bold",
        "book-open",
        "book",
        "bookmark",
        "box",
        "briefcase",
        "calendar",
        "camera-off",
        "camera",
        "cast",
        "check-circle",
        "check-square",
        "check",
        "chevron-down",
        "chevron-left",
        "chevron-right",
        "chevron-up",
        "chevrons-down",
        "chevrons-left",
        "chevrons-right",
        "chevrons-up",
        "chrome",
        "circle",
        "clipboard",
        "clock",
        "cloud-drizzle",
        "cloud-lightning",
        "cloud-off",
        "cloud-rain",
        "cloud-snow",
        "cloud",
        "code",
        "codepen",
        "codesandbox",
        "coffee",
        "columns",
        "command",
        "compass",
        "copy",
        "corner-down-left",
        "corner-down-right",
        "corner-left-down",
        "corner-left-up",
        "corner-right-down",
        "corner-right-up",
        "corner-up-left",
        "corner-up-right",
        "cpu",
        "credit-card",
        "crop",
        "crosshair",
        "database",
        "delete",
    "disc",
    "divide-circle",
    "divide-square",
    "divide",
    "dollar-sign",
    "download-cloud",
    "download",
    "dribbble",
    "droplet",
    "edit-2",
    "edit-3",
    "edit",
    "external-link",
    "eye-off",
    "eye",
    "facebook",
    "fast-forward",
    "feather",
    "figma",
    "file-minus",
    "file-plus",
    "file-text",
    "file",
    "film",
    "filter",
    "flag",
    "folder-minus",
    "folder-plus",
    "folder",
    "framer",
    "frown",
    "gift",
    "git-branch",
    "git-commit",
    "git-merge",
    "git-pull-request",
    "github",
    "gitlab",
    "globe",
    "grid",
    "hard-drive",
    "hash",
    "headphones",
    "heart",
    "help-circle",
    "hexagon",
    "home",
    "image",
    "inbox",
    "info",
    "instagram",
    "italic",
    "key",
    "layers",
    "layout",
    "life-buoy",
    "link-2",
    "link",
    "linkedin",
    "list",
    "loader",
    "lock",
    "log-in",
    "log-out",
    "mail",
    "map-pin",
    "map",
    "maximize-2",
    "maximize",
    "meh",
    "menu",
    "message-circle",
    "message-square",
    "mic-off",
    "mic",
    "minimize-2",
    "minimize",
    "minus-circle",
    "minus-square",
    "minus",
    "monitor",
    "moon",
    "more-horizontal",
    "more-vertical",
    "mouse-pointer",
    "move",
    "music",
    "navigation-2",
    "navigation",
    "octagon",
    "package",
    "paperclip",
    "pause-circle",
    "pause",
    "pen-tool",
    "percent",
    "phone-call",
    "phone-forwarded",
    "phone-incoming",
    "phone-missed",
    "phone-off",
    "phone-outgoing",
    "phone",
    "pie-chart",
    "play-circle",
    "play",
    "plus-circle",
    "plus-square",
    "plus",
    "pocket",
    "power",
    "printer",
    "radio",
    "refresh-ccw",
    "refresh-cw",
    "repeat",
    "rewind",
    "rotate-ccw",
    "rotate-cw",
    "rss",
    "save",
    "scissors",
    "search",
    "send",
    "server",
    "settings",
    "share-2",
    "share",
    "shield-off",
    "shield",
    "shopping-bag",
    "shopping-cart",
    "shuffle",
    "sidebar",
    "skip-back",
    "skip-forward",
    "slack",
    "slash",
    "sliders",
    "smartphone",
    "smile",
    "speaker",
    "square",
    "star",
    "stop-circle",
    "sun",
    "sunrise",
    "sunset",
    "table",
    "tablet",
    "tag",
    "target",
    "terminal",
    "thermometer",
    "thumbs-down",
    "thumbs-up",
    "toggle-left",
    "toggle-right",
    "tool",
    "trash-2",
    "trash",
    "trello",
    "trending-down",
    "trending-up",
    "triangle",
    "truck",
    "tv",
    "twitch",
    "twitter",
    "type",
    "umbrella",
    "underline",
    "unlock",
    "upload-cloud",
    "upload",
    "user-check",
    "user-minus",
    "user-plus",
    "user-x",
    "user",
    "users",
    "video-off",
    "video",
    "voicemail",
    "volume-1",
    "volume-2",
    "volume-x",
    "volume",
    "watch",
    "wifi-off",
    "wifi",
    "wind",
    "x-circle",
    "x-octagon",
    "x-square",
    "x",
    "youtube",
    "zap-off",
    "zap",
    "zoom-in",
    "zoom-out",
    ];

    let copiedIcon = '';

     function setCopiedIcon(icon: string) {
        copiedIcon = icon;
        setTimeout(() => {
            copiedIcon = '';
        }, 3000);
    }

     function fallbackCopyTextToClipboard(icon: string) {
        const textArea = document.createElement("textarea");
        textArea.value = icon;

        // Avoid scrolling to bottom
        textArea.style.top = "0";
        textArea.style.left = "0";
        textArea.style.position = "fixed";

        document.body.appendChild(textArea);
        textArea.focus();
        textArea.select();

        try {
            document.execCommand('copy');
            setCopiedIcon(icon)
        } catch (err) {
            console.error('Fallback: Oops, unable to copy', err);
        }

        document.body.removeChild(textArea);
    }

    function copyTextToClipboard(icon: string) {
        if (!navigator.clipboard) {
            fallbackCopyTextToClipboard(icon);
            return;
        }
        navigator.clipboard.writeText(icon).then(function() {
            setCopiedIcon(icon);
        }, function(err) {
            console.error('Async: Could not copy text: ', err);
        });
    }
</script>

<h1>Svelte feather icons test page</h1>

<p>Icons are from <a href="https://feathericons.com/">Feather Icons</a> and are licensed under <a href="https://github.com/feathericons/feather/blob/master/LICENSE">MIT License</a>.</p>

<div class="icons-container">
    {#each featherIcons as icon}
        <div class="icon-card" on:click={() => copyTextToClipboard(icon)} on:keydown={() => copyTextToClipboard(icon)} role="button" tabindex="0">
            <div class="icon">
                <Icon {icon} />
            </div>
            {#if copiedIcon === icon}
                <span style="font-weight: bold; color: yellowgreen">copied!</span>
                {:else}
                <span>{icon}</span>
            {/if}
        </div>
    {/each}
</div>

<style>
    .icons-container {
        display: flex;
        flex-wrap: wrap;
        flex-direction: row;
        gap: 1rem;
    }

    .icon-card {
        background-color: var(--theme-ui-colors-border);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
        gap: 2rem;
        padding: 3rem 1rem;
        width: 8rem;
        border-radius: 1rem;
    }

    .icon-card:focus {
        outline: 2px solid var(--theme-ui-colors-primary);
    }

    .icon {
        font-size: 18px;
    }
</style>

