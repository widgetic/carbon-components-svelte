<script>
  /**
   * Set to `true` to toggle the expanded state
   * @type {boolean} [expanded]
   */
  export let expanded = false;

  /**
   * Specify the text
   * @type {string} [text]
   */
  export let text = undefined;

  /**
   * Specify the icon props
   * @type {{ render: typeof import("carbon-icons-svelte/lib/Add16").default; skeleton: boolean; }} [icon]
   */
  export let icon = undefined;

  import ChevronDown16 from "carbon-icons-svelte/lib/ChevronDown16";
  import { Icon } from "../../Icon";
</script>

<li class:bx--side-nav__item="{true}" class:bx--side-nav__item--icon="{icon}">
  <button
    type="button"
    aria-expanded="{expanded}"
    class:bx--side-nav__submenu="{true}"
    {...$$restProps}
    on:click
    on:click="{() => {
      expanded = !expanded;
    }}"
  >
    {#if icon}
      <div class:bx--side-nav__icon="{true}">
        <Icon {...icon} />
      </div>
    {/if}
    <span class:bx--side-nav__submenu-title="{true}">{text}</span>
    <div
      class:bx--side-nav__icon="{true}"
      class:bx--side-nav__icon--small="{true}"
      class:bx--side-nav__submenu-chevron="{true}"
    >
      <Icon title="Open Menu" tabindex="0" render="{ChevronDown16}" />
    </div>
  </button>
  <ul role="menu" class:bx--side-nav__menu="{true}">
    <slot />
  </ul>
</li>
