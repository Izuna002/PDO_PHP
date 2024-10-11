```SHOW CODE DEMONSTRATING FETCH_ALL(). USE PRINT_R(). WITH “<pre>” TAG IN BETWEEN.```


```
 <?php require_once 'core/dbConfig.php'; ?>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

    <?php
    $stmt = $pdo->prepare(query: "SELECT * FROM doctors");

    if ($stmt->execute()) {
        echo "<pre>";
        print_r(value: $stmt->fetchAll());
        echo "</pre>";
    }
    ?>

</body>

</html>
```

```SHOW CODE DEMONSTRATING HOW FETCH() IS USED. USE PRINT_R(). WITH “<pre>” TAG IN BETWEEN.```

```
<?php require_once 'core/dbConfig.php'; ?>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

    <?php
    $stmt = $pdo->prepare(query: "SELECT * FROM doctors");

    if ($stmt->execute()) {
        echo "<pre>";
        print_r(value: $stmt->fetch());
        echo "</pre>";
    }
    ?>

</body>

</html>
```

```SHOW CODE DEMONSTRATING INSERTION OF RECORD TO YOUR DATABASE```

```
<?php

$query = "INSERT INTO patients (patient_id, first_name, last_name, date_of_birth) 
          VALUES (?, ?, ?, ?)";

$stmt = $pdo->prepare(query: $query);

$executeQuery = $stmt->execute(
    params: [4, "Pao", "Fontanilla", "2002-02-07"]
);

if ($executeQuery) {
    echo "Query successful!";
} else {
    echo "Query failed";
}

?>
```
   
 ```SHOW CODE DEMONSTRATING DELETION OF RECORD TO YOUR DATABASE```

```
<?php

$query = "DELETE FROM patients 
          WHERE patient_id = 4";

$stmt = $pdo->prepare(query: $query);

$executeQuery = $stmt->execute();

if ($executeQuery) {
    echo "Deletion successful!";
} else {
    echo "Deletion failed";
}

?>
```
 
```SHOW CODE DEMONSTRATING UPDATING OF RECORD FROM YOUR DATABASE```

```
<?php

$query = "UPDATE patients 
          SET first_name = ?, last_name = ? 
          WHERE patient_id = 3";

$stmt = $pdo->prepare(query: $query);

$executeQuery = $stmt->execute(
    params: ["Pao", "Fontanilla"]
);

if ($executeQuery) {
    echo "Update successful!";
} else {
    echo "Update failed";
}

?>
```

```SHOW CODE DEMONSTRATING AN SQL QUERY’S RESULT SET IS RENDERED ON AN HTML TABLE```

```
<?php require_once 'dbconfig.php'; ?>

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
</html>
```
