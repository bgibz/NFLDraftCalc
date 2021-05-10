<template>
    <div>
        <label for="teamA-picks">Team A Pick Numbers</label>
        <input type="text" id="teamA-picks" :picks="tradePicks"/>
    </div> 
</template>
<script>
  export default {
      props: {
            tradePicks: { default: "", type: String} 
        },
        data() {
            return {
                teamAPicks: this.tradePicks
            }
        }
  };
</script>