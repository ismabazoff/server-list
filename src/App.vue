<template>
    <div class="app">
        <div class="list">
            <ul>
                <li
                    v-for="(model, index) in models"
                    :key="index"
                    @click="selectModel(index)"
                    :class="{ active: selectedModelIndex === index }"
                >
                    {{ model.server_name }}
                </li>
            </ul>
        </div>
        <div class="form">
            <div v-if="selectedModelIndex !== null">
                <div class="server">
                    <label for="serverName">Server Name:&nbsp;</label>
                    <input
                        id="serverName"
                        class="border-solid border-2 border-indigo-600 w-44 pl-1"
                        v-model="selectedModel.server_name"
                    />
                </div>
                <div class="server">
                    <label for="serverType">Server Type:&nbsp;</label>
                    <select
                        id="serverType"
                        class="border-solid border-2 border-indigo-600 w-44"
                        v-model="selectedModel.server_type"
                    >
                        <option value="vds">VDS</option>
                        <option value="dedicated">Dedicated</option>
                        <option value="hosting">Hosting</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
    <pre>models - {{ models }}</pre>
</template>

<script>
export default {
    data() {
        return {
            models: [
                {
                    customer_id: 'user1',
                    server_name: 'server7',
                    server_type: 'vds',
                },
                {
                    customer_id: 'user5',
                    server_name: 'server2',
                    server_type: 'dedicated',
                },
                {
                    customer_id: 'user3',
                    server_name: 'server4',
                    server_type: 'hosting',
                },
            ],
            selectedModelIndex: null,
        }
    },
    computed: {
        selectedModel() {
            if (this.selectedModelIndex !== null) {
                return this.models[this.selectedModelIndex]
            }
            return null
        },
    },
    methods: {
        selectModel(index) {
            this.selectedModelIndex = index
        },
    },
}
</script>

<style lang="scss">
.app {
    display: flex;
    align-items: center;
}
.server {
    margin-bottom: 5px;
    display: flex;
    justify-content: space-between;
}
.form {
    margin-left: 20px;
}
.active {
    background-color: #ccc;
}
ul {
    padding-left: 0;
    display: inline-block;
    li {
        list-style-type: none;
        outline: 1px solid black;
        padding: 5px;
        cursor: pointer;
    }
}
pre {
    margin: 5px;
}
</style>
