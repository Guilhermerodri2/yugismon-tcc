# TCC
Códigos

<!DOCTYPE html>
<html>
    <head> 
        <title>Matrícula</title>
        <link href="css/style.css" rel="stylesheet" />
    </head>
    <body>
        <header>
            <div class="center">
                <div class="logo"><img src="iepa.png" /></div><!--logo-->
                <div class="menu">
                    <a href="index.html">Home</a>
                    <a href="#">Sobre</a>
                    <a href="#">Contato</a>
                </div><!--menu-->
            </div><!--center-->
        </header>
        <section class="matricula">
            <div class="extras">
                <h2>Matrícula</h2>
                <form method="post" action="processa.php">
                    <h3>Dados Pessoais</h3>
                    <div class="form-group">
                        <label for="nome">Nome Completo:</label>
                        <input type="text" id="nome" name="nome" required>
                    </div>
                    <div class="form-group">
                        <label for="email">E-mail:</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="cpf">CPF:</label>
                        <input type="text" id="cpf" name="cpf" required>
                    </div>
                    <h3>Dados do Curso</h3>
                    <div class="form-group">
                        <label for="curso">Curso:</label>
                        <select id="curso" name="curso" required>
                            <option value="">Selecione o Curso</option>
                            <option value="engenharia">Engenharia</option>
                            <option value="medicina">Medicina</option>
                            <option value="direito">Direito</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="turma">Turma:</label>
                        <select id="turma" name="turma" required>
                            <option value="">Selecione a Turma</option>
                            <option value="manha">Manhã</option>
                            <option value="tarde">Tarde</option>
                            <option value="noite">Noite</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="periodo">Período:</label>
                        <select id="periodo" name="periodo" required>
                            <option value="">Selecione o Período</option>
                            <option value="primeiro">1º Semestre</option>
                            <option value="segundo">2º Semestre</option>
                        </select>
                    </div>
                    <h3>Forma de Pagamento</h3>
                    <div class="form-group">
                        <label for="pagamento">Pagamento:</label>
                        <select id="pagamento" name="pagamento" required>
                            <option value="">Selecione a Forma de Pagamento</option>
                            <option value="boleto">Boleto Bancário</option>
                            <option value="cartao">Cartão de Crédito</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <button type="submit name=botao">Enviar</button>
                    </div>
                </form>
            </div><!--extras-->
        </section></html>
<?php
if(isset($_POST["botao"])){
//Fazendo a conexão com o MySQL Query Browser, via código.
$conexao=mysql_connect("localhost:3306","root", "root");
mysql_select_db("iepa",$conexao);
//Criando as variáveis para manipulação dos dados.
$nomeCompleto = $_POST["nome completo"];
$email = $_POST["email"];
$cpf = $_POST["cpf"];
$curso = $_POST["curso"];
$turma = $_POST["turma"];
$periodo = $_POST["periodo"];
$pagamento = $_POST["pagamento"];
//Inserindo os dados na tabela do MySQL Query Browser.
mysql_query("insert into matricula values('$nomeCompleto''$email',$cpf',$curso'$turma',$periodo'$pagamento')",$conexao);
//Exibindo os dados da tabela do MySQL Query Browser.
$consulta = mysql_query("select * from matricula",$conexao);
while($_GET = mysql_fetch_array($consulta)){
echo "<br>Nome Completo:".$_GET['nomeCompleto'];
echo " - Email:".$_GET['email'];
echo " - Cpf:".$_GET['cpf'];
echo " - Curso:".$_GET['curso'];
echo " - Turma:".$_GET['turma'];
echo " - Periodo:".$_GET['periodo'];
echo " - Pagamento:".$_GET['pagamento'];


}
//Encerrando a conexão com o MySQL Query Browser.
mysql_close($conexao);
}
?>
    
    
create table matricula(
nomeCompleto varchar(40),
email varchar(30),
cpf int,
curso varchar(30),
turma varchar(30),
periodo varchar(30),
pagamento varchar(30));


