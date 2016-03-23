<?php
function __autoload($class){require_once"{$class}.class.php";}

abstract class ConDB
{
		private static $cnx;

		private function setConn()
		{
			return
			is_null(self::$cnx)?
					self::$cnx=new PDO("mysql:host=localhost;dbname=DevPHP","root"):
					self::$cnx;
		}
		public function getConn()
		{
			return $this->setConn();
		}
}
$crud=new CRUD;
$sel=$crud->select('*','user','WHERE idUser=?',array(3));
foreach($sel as $reg)
{
	$_SESSION['user']=$reg;
}
?>
