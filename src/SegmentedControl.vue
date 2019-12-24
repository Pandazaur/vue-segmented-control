<template>
    <div class="segmented-control" :style="[segmentedControlStyle]">
        <div class="segmented-item" :style="[valuesSelected.includes(option[value]) ? itemSelectedStyle : null, itemStyle]"
            :class="{'is-selected': valuesSelected.includes(option[value])}"
            v-for="option in options" @click="onSelect(option)">
            {{ option[label] }}
        </div>
    </div>
</template>

<script>
export default {
    props: {
        options: {
            type: Array,
            required: true
        },
        label: {
            type: String,
            default: 'label'
        },
        value: {
            type: String,
            default: 'value'
        },
        color: {
            type: String,
            default: '#fff'
        },
        activeColor: {
            type: String,
            default: '#000'
        },
        multiple: {
            type: Boolean,
            default: false
        },
	defaultSelected : {
		type : Object,
		default : {}
	},
    },
    data () {
        return {
            optionsSelected: []
        }
    },
    created(){

	this.onSelect(this.defaultSelected)
    },
    computed: {
        segmentedControlStyle: function () {
            return {
                color: this.activeColor,
                border: `solid 1px ${this.activeColor}`
            }
        },
        itemStyle: function () {
            return {
                borderRight: `solid 1px ${this.activeColor}`
            }
        },
        itemSelectedStyle: function () {
            return {
                color: this.color,
                background: this.activeColor
            }
        },
        valuesSelected: function () {
            return this.optionsSelected.map(option => option[this.value])
        }
    },
    methods: {
        onSelect (option) {
            if (this.multiple === true) {
                if (this.optionsSelected.find(optionSelected => optionSelected.value === option.value)) {
                    this.optionsSelected = this.optionsSelected.filter(optionSelected => optionSelected.value !== option.value)
                } else {
                    this.optionsSelected.push(option)
                }
            } else {
                this.optionsSelected = [option]
            }

            this.$emit('select', this.optionsSelected)
        }
    }
}
</script>

<style>
    .segmented-control {
        display: flex;
        flex-direction: row;
        border-radius: 5px;
    }

    .segmented-item {
        flex: 1;
        padding: 10px;
        transition: all .3s ease;
        text-align: center;
        user-select: none;
    }

    .segmented-item:last-child {
        border: none!important;
    }

    .is-selected {
        color: white;
    }
</style>
