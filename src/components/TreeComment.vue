<template>
    <div class="tree-comment">
        <div class="label-wrapper" @click="toggleChildren">
            <div :style="indent" :class="labelClasses">
                {{ label }}
                <br>
                <a class="btn-reply" href="#">reply</a>
            </div>
        </div>
        <tree-comment
            v-if="showChildren" 
            v-for="node in nodes" 
            :nodes="node.nodes" 
            :label="node.label" 
            :depth="depth + 1">
        </tree-comment>
    </div>
</template>

<script>
    export default {
        name: 'TreeComment',
        props: {
            nodes: {
                type: Array,
                required: false
            },
            label: {
                type: String,
                required: true
            },
            depth: {
                type: Number,
                required: true
            }
        },
        data() {
            return {
                showChildren: true
            }
        },
        computed: {
            labelClasses() {
                return { 'has-children': this.nodes }
            },
            indent() {
                return { transform: `translate(${this.depth * 50}px)` }
            }
        },
        methods: {
            toggleChildren() {
                this.showChildren = !this.showChildren;
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
    .tree-comment {
        font-size: 14px;
        .label-wrapper {
            margin-bottom: 10px;
            .has-children {
                cursor: pointer;
            }
        }
        .btn-reply {
            color: #828282;
            text-decoration: underline;
        }
    }
</style>
