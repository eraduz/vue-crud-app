<template>
  <table class="table table-striped">
    <thead>
      <tr>
        <th scope="col">ID</th>
        <th scope="col">Name</th>
        <th scope="col">E-mail</th>
        <th scope="col">Message</th>
        <th scope="col">Update / delete</th>
      </tr>
    </thead>
    <tbody>
      <tr class="container" v-for="item in messages" :key="item.id">
        <th scope="row">{{ item.id }}</th>
        <td class="foo">{{ item.name }}</td>
        <td class="foo">{{ item.email }}</td>
        <td class="foo">{{ item.message }}</td>
        <td class="foo">
          <a href="delete.php?del=<?= $row['id'] ?>">❌</a>&nbsp;&nbsp;
          <a href="edit.php?id=<?= $row['id'] ?>">🔩</a>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
import db from '../components/firebaseInit'

export default {
  data () {
    return {
      messages: [],
      loading: true
    }
  },
  mounted () {
    db.collection('messages')
      .get()
      .then(querySnapshot => {
        this.loading = false
        querySnapshot.forEach(doc => {
          const data = {
            id: doc.data().id,
            name: doc.data().name,
            email: doc.data().email,
            message: doc.data().message
          }
          this.messages.push(data)
        })
      })
  }
}
</script>
