<template>
  <div v-for="style in styles" style="margin-bottom: 30px">
    <h3>Class: '{{style}}'</h3>
    <table :class="style">
      <thead>
        <tr>
            <th>Name</th>
            <th>Price</th>
            <th>In Stock</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <td>Item #1</td>
          <td>$10.11</td>
          <td>101</td>
        </tr>
        <tr>
          <td>Item #2</td>
          <td>$8.88</td>
          <td>34</td>
        </tr>
        <tr>
          <td>Item #3</td>
          <td>$0.15</td>
          <td>1670</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data () {
    return {
      styles: [
        '',
        'inner-delimiter',
        'bordered',
        'striped',
        'highlight',
        'centered',
        'compact'
      ]
    }
  }
}
</script>
