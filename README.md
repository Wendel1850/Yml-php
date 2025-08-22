<?php
include 'conexao.php';

$nome = 'João';
$email = 'joao@example.com';

$sql = "INSERT INTO usuarios (nome, email) VALUES ('$nome', '$email')";

if ($conn->query($sql) === TRUE) {
  echo "Registro inserido com sucesso!";
} else {
  echo "Erro ao inserir registro: " . $conn->error;
}
?>

<?php
include 'conexao.php';

$sql = "SELECT * FROM usuarios";

$result = $conn->query($sql);

if ($result->num_rows > 0) {
  while($row = $result->fetch_assoc()) {
    echo "Nome: " . $row["nome"]. " - Email: " . $row["email"]. "<br>";
  }
} else {
  echo "Nenhum registro encontrado.";
}
?>




<?php
include 'conexao.php';

if (isset($_POST['enviar'])) {
  $nome = $_POST['nome'];
  $email = $_POST['email'];

  $sql = "INSERT INTO usuarios (nome, email) VALUES ('$nome', '$email')";

  if ($conn->query($sql) === TRUE) {
    echo "Registro inserido com sucesso!";
  } else {
    echo "Erro ao inserir registro: " . $conn->error;
  }
}
?>

<form action="" method="post">
  <label for="nome">Nome:</label>
  <input type="text" id="nome" name="nome"><br><br>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email"><br><br>
  <input type="submit" value="Enviar" name="enviar">
</form>

<?php
$sql = "SELECT * FROM usuarios";

$result = $conn->query($sql);

if ($result->num_rows > 0) {
  while($row = $result->fetch_assoc()) {
    echo "Nome: " . $row["nome"]. " - Email: " . $row["email"]. "<br>";
  }
} else {
  echo "Nenhum registro encontrado.";
}
?>
