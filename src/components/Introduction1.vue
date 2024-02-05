<template>
    <div>
        <h1>Static</h1>
        example1: {{ example1 }}
        <br>
        example2: {{ example2 }}
        <br>
        example3: {{ example3 }}
    </div>

    <div>
        <h1>Reactive</h1>
        count1: {{ count1 }}
        <br>
        <br>
        count2: {{ count2.count }}

        <div>
            <button @click="count1++">count1 ++</button>
            <button @click="count2.count++">count2 ++</button>
        </div>
    </div>

    <div>
        <h1>Directives</h1>
        <div>
            <h2>v-if</h2>
            <!--            <div-->
            <!--                v-if="isRenderBox"-->
            <!--                class="box box-v-if"-->
            <!--            />-->
            <!--            <button @click="isRenderBox = !isRenderBox">show/hide red box</button>-->
            <div
                v-if="boxType === 1"
                class="box box-v-if"
            />
            <div
                v-else-if="boxType === 2"
                class="box box-v-if-green"
            />
            <div
                v-else
                class="box box-v-if-yellow"
            />
            <button @click="boxType++">v-if v-else-if v-else condition ++</button>
        </div>
        <hr>
        <div>
            <h2>v-show</h2>
            <div
                v-show="isShowBox"
                class="box box-v-show"
            />
            <button @click="isShowBox = !isShowBox">show/hide blue box</button>
        </div>
        <hr>
        <div>
            <h2>v-bind (with a shortcut)</h2>
            <!--            v-bind:alt="bindText"-->
            <img
                :alt="bindText"
                width="100px"
                height="100px"
            >
            <!--            <button v-on:click="bindText = 'bird'">change alt</button>-->
            <button @click="bindText = 'bird'">change alt</button>
        </div>
        <hr>
        <div>
            <h2>v-for</h2>
            <h4>Array</h4>
            <ul>
                <!--                <li v-for="(fruit, index) in fruitsList">-->
                <!--                    fruit name: {{ fruit.name }}-->
                <!--                    <br>-->
                <!--                    taste: {{ fruit.taste }}-->
                <!--                    <br>-->
                <!--                    index: {{ fruit.id }}-->
                <!--                    <br>-->
                <!--                    <hr>-->
                <!--                </li>-->
                <li
                    v-for="({ name, taste, id }) in fruitsList"
                    :key="id"
                >
                    fruit name: {{ name }}
                    <br>
                    taste: {{ taste }}
                    <br>
                    index: {{ id }}
                    <br>
                    <hr>
                </li>
            </ul>
            <h4>Object</h4>
            <ul>
                <li
                    v-for="({ name, id, priceList }) in fruitsObject"
                    :key="id"
                >
                    {{ name }}
                    <br>
                    <ul>
                        <li
                            v-for="(price, index) in priceList"
                            :key="index"
                        >
                            {{ price }}
                        </li>
                    </ul>
                </li>
            </ul>
        </div>
        <hr>
    </div>
</template>

<script>
import {
    ref,
    reactive,
    defineComponent
} from 'vue';

export default defineComponent({
    name: 'Introduction1',
    props: ['msg'],
    setup() {
        const count1 = ref(0);

        const count2 = reactive({
            count: 0
        });

        const example1 = 'this is string';
        const example2 = 21;
        const example3 = { a: 'a' };

        // v-if
        const isRenderBox = ref(true);
        const boxType = ref(1);

        // v-show
        const isShowBox = ref(true);

        // v-bind:alt
        const bindText = ref('empty');

        // v-for
        // const fruitsList = ref([
        //     'apple',
        //     'banana',
        //     'peach',
        //     'apricot',
        // ])
        const fruitsList = ref([
            {
                name: 'apple',
                id: 1,
                taste: 'good'
            },
            {
                name: 'banana',
                id: 2,
                taste: 'good'
            },
            {
                name: 'peach',
                id: 3,
                taste: 'awesome'
            },
            {
                name: 'apricot',
                id: 4,
                taste: 'normal'
            }
        ]);

        const fruitsObject = {
            apple: {
                name: 'apple',
                id: 1,
                priceList: ['10$', '2$', '3$']
            },
            banana: {
                name: 'banana',
                id: 2,
                priceList: ['1$']
            },
            peach: {
                name: 'peach',
                id: 3,
                priceList: []
            },
            apricot: {
                name: 'apricot',
                id: 4,
                priceList: []
            }
        };

        return {
            count1,
            count2,
            example1,
            example2,
            example3,
            isRenderBox,
            boxType,
            isShowBox,
            bindText,
            fruitsList,
            fruitsObject
        };
    }
});
</script>

<style>
.box {
    width: 50px;
    height: 50px;
}

.box-v-if {
    background: red;
}

.box-v-if-green {
    background: green;
}

.box-v-if-yellow {
    background: yellow;
}

.box-v-show {
    background: blue;
}
</style>
