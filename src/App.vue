<script setup>
import { computed, ref } from "vue";

const courseList = ["chees", "chocolate", "meet", "daunculship"];

const addToEnd = computed(() => {
  const result = courseList.slice();

  result.push("potato");

  return result;
});

const addToStart = computed(() => {
  const result = courseList.slice();

  result.unshift("salt");

  return ["salt", ...courseList];
});

const mergeArray = computed(() => {
  const secondCourseList = ["sugar", "flour"];
  /*
  const result = courseList.slice();

  const secondCourseList = ["sugar", "flour"];

  result.concat(secondCourseList);

   */

  return [...secondCourseList, ...courseList];
});

let courselistCopy = ref([...courseList]);

function deleteCourseListElement(index) {
  courselistCopy.value.splice(index, 1);
}

const addValueObject = computed(() => {
  const color = { color: "red" };
  return { brand: "Apple", model: "iPhone X", ...color };
});

const addValueConditionalyToObject = computed(() => {
  const color = "red";

  return {
    brand: "Apple",
    model: "iPhone X",
    ...(color === "red" && { color }),
  };
});

const updateValueInObject = computed(() => {
  const model = { model: "S22" };

  return {
    brand: "Apple",
    model: "iPhone X",
    ...model,
  };
});

const mergeToObject = computed(() => {
  const object1 = { brand: "Apple", model: "iPhone X" };
  const object2 = { color: "S22", price: 100 };

  return {
    ...object1,
    ...object2,
  };
});

const destructureObject = computed(() => {
  const axiosResponse = {
    config: {
      url: "https://example.com",
      method: "get",
    },
    data: {
      id: 10,
      attributes: [
        {
          name: "name1",
          value: "John",
          comments: {
            id: 1,
            attributes: [
              {
                name: "comment",
                value: "Hello",
              },
            ],
          },
          category: {
            id: 1,
            attributes: [
              {
                name: "comment",
              },
            ],
          },
        },
        {
          name: "name2",
          value: "John",
          comments: {
            id: 1,
            attributes: [
              {
                name: "comment",
                value: "Hello",
              },
            ],
          },
          category: {
            id: 1,
            attributes: [
              {
                name: "comment",
              },
            ],
          },
        },
        {
          name: "name3",
          value: "John",
          comments: {
            id: 1,
            attributes: [
              {
                name: "comment",
                value: "Hello",
              },
            ],
          },
          category: {
            id: 1,
            attributes: [
              {
                name: "comment",
              },
            ],
          },
        },
        {
          name: "name4",
          value: "John",
          comments: {
            id: 1,
            attributes: [
              {
                name: "comment",
                value: "Hello",
              },
              {
                name: "comment",
                value: "Hello",
              },
              {
                name: "comment",
                value: "Hello",
              },
              {
                name: "comment",
                value: "Hello",
              },
              {
                name: "comment",
                value: "Hello",
              },
            ],
          },
          category: {
            id: 1,
            attributes: [
              {
                name: "comment",
              },
            ],
          },
        },
        {
          name: "name5",
          value: "John",
          comments: {
            id: 1,
            attributes: [
              {
                name: "comment",
                value: "Hello",
              },
            ],
          },
          category: {
            id: 1,
            attributes: [
              {
                name: "comment",
              },
            ],
          },
        },
      ],
    },
    headers: {
      "content-type": "application/json",
    },
  };

  const { attributes } = axiosResponse.data;

  return attributes;
});
</script>

<template>
  <article>
    <section>
      <h2>Base List</h2>
      <p>{{ courseList }}</p>
    </section>

    <section>
      <h2>Add element to end</h2>
      <p>{{ addToEnd }}</p>
    </section>

    <section>
      <h2>Add element to start</h2>
      <p>{{ addToStart }}</p>
    </section>

    <section>
      <h2>Merge two Array</h2>
      <p>{{ mergeArray }}</p>
    </section>

    <section>
      <h2>Delete an element</h2>
      <ul>
        <li
          v-for="(element, index) in courselistCopy"
          :key="element"
          @click="deleteCourseListElement(index)"
        >
          {{ element }}
        </li>
      </ul>
    </section>

    <section>
      <h2>Add value to object</h2>
      <p>{{ addValueObject }}</p>
    </section>

    <section>
      <h2>Add value conditionaly to object</h2>
      <p>{{ addValueConditionalyToObject }}</p>
    </section>

    <section>
      <h2>Update value in object</h2>
      <p>{{ updateValueInObject }}</p>
    </section>

    <section>
      <h2>Merge to object</h2>
      <p>{{ mergeToObject }}</p>
    </section>

    <section>
      <aside
        v-for="(blog, index) in destructureObject"
        :key="index"
        style="margin: auto"
      >
        <h2>{{ blog.name }}</h2>
        <p>
          {{ blog.value }}
        </p>
        <span> Comments: {{ blog.comments.attributes }} </span>
      </aside>
    </section>
  </article>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

article {
  max-width: 1000px;
  margin: 0 auto;
}

section {
  background: #c4c3c3;
  padding: 40px;
  margin: 40px;
  border-radius: 30px;
}
</style>
