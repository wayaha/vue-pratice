<template>
    <section class="slotSection">
        <h2>Slot</h2>
        <slot-content title="插槽内容1">
            <h3>this is test...</h3>
        </slot-content>

        <slot-content title="具名插槽">
            <template slot="slot1">
                <h3>Here might be a page title</h3>
            </template>
            <p slot="slot2">啦啦啦啦啦啦啦啦。。。。</p>
        </slot-content>

        <hr>

        <slot-scope :list="list" title="作用域插槽">
            <template slot-scope="slotProps">
                <span v-text="slotProps.item.name"></span>
            </template>
        </slot-scope>

        <hr>

        <h3>This is a tab in order to trying to pratice with the attribute named 'is'.</h3>
        <nav>
            <button @click="currentComponent='slot-content'" v-text="'slot-content'"></button>
            <button @click="currentComponent='slot-scope'" v-text="'slot-scope'"></button>
        </nav>
        <component :is="currentComponent" :list="list" title="插槽">
            <template slot-scope="slotProps">
                <span v-text="slotProps.item && slotProps.item.name"></span>
            </template>
        </component>

        <r-footer
			from="transfer Data"
			to=""
			previousPath="/transferData"
			nextPath=""
		></r-footer>
    </section>
</template>

<script>
    import SlotContent from './SlotContent';
    import SlotScope from './SlotScope';
    import Footer from '../common/Footer';

    export default {
        name: 'slotSection',
        data: function () {
            return {
                list: [{name: 'ddsf'}, {name: 'fff'}, {name: 'ggg'}],
                currentComponent: 'slot-content'
            }
        },
        components: {
            'slot-content': SlotContent,
            'slot-scope': SlotScope,
            'r-footer': Footer
        }
    }
</script>

<style scoped>
    .slotSection {
        background-color: lightblue;
        padding: 10px;
    }
</style>

