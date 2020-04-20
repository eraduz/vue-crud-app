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
        <!-- while -->
      <tr>
        <th scope="row">id</th>
        <td class="foo">name</td>
        <td class="foo">email</td>
        <td class="foo">message</td>
        <td class="foo">
          <a href="delete.php?del=<?= $row['id'] ?>">
            <i class="fas fa-trash-alt text-danger"></i>
          </a>&nbsp;&nbsp;
          <a href="edit.php?id=<?= $row['id'] ?>">
            <i class="fas fa-edit text-primary"></i>
          </a>
        </td>
      </tr>
    <!-- while  -->
    </tbody>
  </table>
</template>
