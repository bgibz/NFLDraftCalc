<template>
    <div :id="id">
        <td><strong>{{pickNo}}</strong></td>
        <td>{{value}}</td>
    </div>
</template>

<script>
import uniqueId from 'lodash.uniqueid';
  export default {
      props: {
            pick: { required: true, type: Number },
            value: { default: 1, type: Number }
        },
        data() {
            return {
                pickNo: this.pick,
                value: this.value,
                id: uniqueId('pick-')
            };
        }
  };
</script>