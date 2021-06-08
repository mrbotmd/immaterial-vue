<template>
  <button
    style="display: flex; justify-content: center; align-items: center"
    :class="[
      `button`,
      variant === undefined ? `clear` : variant,
      color === undefined ? `default` : color,
      variant === undefined && color === `primary` && `clearPrimary`,
      variant === undefined && color === `secondary` && `clearSecondary`,
      variant === undefined && color === `warning` && `clearWarning`,
      variant === undefined && color === `info` && `clearInfo`,
      variant === undefined && color === `error` && `clearError`,
      variant === undefined && color === `success` && `clearSuccess`,
      size === undefined ? `medium` : size,
      disabled && `disabled`,
      circle && `circle`,
      rounded && `rounded`,
      !circle && !rounded && `square`,
      !elevation && `elevation`,
    ]"
    :disabled="disabled"
    v-on="$listeners"
  >
    <font-awesome-icon v-if="icon !== undefined" :icon="icon" class="icon" />
    <span
      :class="icon !== undefined && this.$slots.default !== undefined && `text`"
    >
      <slot></slot>
    </span>
  </button>
</template>

<script>
export default {
  props: {
    elevation: Boolean,
    size: String,
    variant: String,
    color: String,
    circle: Boolean,
    rounded: Boolean,
    icon: String,
    disabled: Boolean,
  },
  created() {
    console.log(this.$slots.default);
  },
};
</script>

<style scoped>
.button {
  --padding-small: 4px 10px;
  --padding-medium: 6px 16px;
  --padding-large: 8px 22px;
  position: relative;
  overflow: hidden;
  text-transform: uppercase;
  width: max-content;
  outline: 0;
  border: 0;
  box-sizing: border-box;
  cursor: pointer;
  background-position: center;
  transition: background 0.8s, color 0.8s;
}

.button:hover {
  box-shadow: 0px 2px 4px -1px rgb(0 0 0 / 20%),
    0px 4px 5px 0px rgb(0 0 0 / 14%), 0px 1px 10px 0px rgb(0 0 0 / 12%);
}

.small {
  padding: var(--padding-small);
}

.medium {
  padding: var(--padding-medium);
}

.large {
  padding: var(--padding-large);
}

.elevation {
  box-shadow: 0px 3px 1px -2px rgb(0 0 0 / 20%),
    0px 2px 2px 0px rgb(0 0 0 / 14%), 0px 1px 5px 0px rgb(0 0 0 / 12%);
}

.clear {
  border: none;
  outline: 0;
  background-color: rgba(0, 0, 0, 0);
  box-shadow: none;
}

.primary {
  color: var(--text-dark-primary);
  background-color: var(--primary-main);
  outline: 1px solid var(--primary-main);
}

.secondary {
  color: var(--text-dark-primary);
  background-color: var(--secondary-main);
  outline: 1px solid var(--secondary-main);
}

.warning {
  color: var(--text-dark-primary);
  background-color: var(--warning-main);
  outline: 1px solid var(--warning-main);
}
.info {
  color: var(--text-dark-primary);
  background-color: var(--info-main);
  outline: 1px solid var(--info-main);
}
.error {
  color: var(--text-dark-primary);
  background-color: var(--error-main);
  outline: 1px solid var(--error-main);
}
.success {
  color: var(--text-dark-primary);
  background-color: var(--success-main);
  outline: 1px solid var(--success-main);
}

.default {
  color: var(--text-light-primary);
  background-color: var(--button-default);
  outline: 1px solid var(--button-default);
}

.disabled {
  color: var(--button-default);
  background-color: var(--button-light-disabled-background);
}

.solid {
  border: none;
  outline: none;
  color: var(--text-dark-primary);
}

.outline {
  color: var(--text-light-primary);
  background-color: rgba(0, 0, 0, 0);
}

.clearPrimary {
  color: var(--primary-dark);
  background-color: rgba(0, 0, 0, 0);
  border: none;
  outline: 0;
}

.clearSecondary {
  color: var(--secondary-dark);
  background-color: rgba(0, 0, 0, 0);
  border: none;
  outline: 0;
}

.clearSuccess {
  color: var(--success-dark);
  background-color: rgba(0, 0, 0, 0);
  border: none;
  outline: 0;
}

.clearError {
  color: var(--error-dark);
  background-color: rgba(0, 0, 0, 0);
  border: none;
  outline: 0;
}

.clearWarning {
  color: var(--warning-dark);
  background-color: rgba(0, 0, 0, 0);
  border: none;
  outline: 0;
}

.clearInfo {
  color: var(--info-dark);
  background-color: rgba(0, 0, 0, 0);
  border: none;
  outline: 0;
}

.default:hover {
  background: var(--button-light-hover)
    radial-gradient(circle, transparent 1%, var(--button-light-active) 1%)
    center/15000%;
}

.default:active {
  background-color: var(--button-light-acive);
  background-size: 100%;
  transition: background 0s;
}

.primary:hover {
  color: var(--text-dark-primary);
  background: var(--primary-light)
    radial-gradient(circle, transparent 1%, var(--primary-dark) 1%)
    center/15000%;
}

.primary:active {
  color: var(--text-dark-primary);
  background-color: var(--primary-dark);
  background-size: 100%;
  transition: background 0s;
}

.secondary:hover {
  color: var(--text-dark-primary);
  background: var(--secondary-light)
    radial-gradient(circle, transparent 1%, var(--secondary-dark) 1%)
    center/15000%;
}

.secondary:active {
  color: var(--text-dark-primary);
  background-color: var(--secondary-dark);
  background-size: 100%;
  transition: background 0s;
}

.warning:hover {
  color: var(--text-dark-primary);
  background: var(--warning-light)
    radial-gradient(circle, transparent 1%, var(--warning-dark) 1%)
    center/15000%;
}

.warning:active {
  color: var(--text-dark-primary);
  background-color: var(--warning-dark);
  background-size: 100%;
  transition: background 0s;
}

.error:hover {
  color: var(--text-dark-primary);
  background: var(--error-light)
    radial-gradient(circle, transparent 1%, var(--error-dark) 1%) center/15000%;
}

.error:active {
  color: var(--text-dark-primary);
  background-color: var(--error-dark);
  background-size: 100%;
  transition: background 0s;
}

.success:hover {
  color: var(--text-dark-primary);
  background: var(--success-light)
    radial-gradient(circle, transparent 1%, var(--success-dark) 1%)
    center/15000%;
}

.success:active {
  color: var(--text-dark-primary);
  background-color: var(--success-dark);
  background-size: 100%;
  transition: background 0s;
}

.info:hover {
  color: var(--text-dark-primary);
  background: var(--info-light)
    radial-gradient(circle, transparent 1%, var(--info-dark) 1%) center/15000%;
}

.info:active {
  color: var(--text-dark-primary);
  background-color: var(--info-dark);
  background-size: 100%;
  transition: background 0s;
}

.circle {
  border-radius: 50%;
}

.rounded {
  border-radius: 4px;
}

.square {
  border-radius: 0px;
}

.text {
  margin-left: 5px;
}
</style>
