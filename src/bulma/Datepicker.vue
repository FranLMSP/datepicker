<template>
    <core-datepicker v-bind="$attrs"
        v-on="$listeners">
        <template v-slot:default="{ timeOnly, clearButton, clearEvents, inputBindings, readonly }">
            <div class="control"
                :class="{'has-icons-left has-icons-right': !readonly}">
                <input class="input"
                    :class="[{ 'is-danger': isDanger }, { 'is-warning': isWarning }]"
                    type="text"
                    :placeholder="placeholder"
                    v-bind="inputBindings">
                <span class="icon is-small is-left"
                    v-if="!readonly">
                    <fa icon="clock"
                        v-if="timeOnly"/>
                    <fa icon="calendar-alt"
                        v-else/>
                </span>
                <span class="icon is-small is-right clear-button"
                    v-on="clearEvents"
                    v-if="clearButton">
                    <a class="delete is-small"/>
                </span>
            </div>
        </template>
    </core-datepicker>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core';
import { faClock, faCalendarAlt } from '@fortawesome/free-solid-svg-icons';
import CoreDatepicker from '../renderless/CoreDatepicker.vue';

library.add(faClock, faCalendarAlt);

export default {
    name: 'Datepicker',

    components: { CoreDatepicker },

    props: {
        placeholder: {
            type: String,
            default: 'Select Date',
        },
        isDanger: {
            type: Boolean,
            default: false,
        },
        isWarning: {
            type: Boolean,
            default: false,
        },
    },
};
</script>

<style lang="scss">
    .control.has-icons-right .clear-button {
        pointer-events: all;
    }
</style>
