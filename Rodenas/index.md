```<?php require_once 'dbconfig.php'; ?>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    table, th, td {
      border: 1px solid black;
    }
  </style>
</head>
<body>

  <?php
  $query = "SELECT name, join_date FROM members";
  $stmt = $pdo->prepare(query: $query);
  $executeQuery = $stmt->execute();

  if ($executeQuery) {
    $members = $stmt->fetchAll();
  } else {
    echo "Query failed";
  }
  ?>

  <table>
    <tr>
      <th>Name</th>
      <th>Join Date</th>
    </tr>
    <?php foreach ($members as $row) { ?>
      <tr>
        <td><?php echo $row['name']; ?></td>
        <td><?php echo $row['join_date']; ?></td>
      </tr>
    <?php } ?>
  </table>

</body>
</html>```
