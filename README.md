<div align="center">

## online users


</div>

### Description

Very easy script the stores the amount of users browsing the page and prints it out on the screen.
 
### More Info
 
the number of users browsing the page during a by you specified amount of time.

none known at this stage.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[reggie\_mv](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/reggie-mv.md)
**Level**          |Beginner
**User Rating**    |3.7 (11 globes from 3 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__8-1.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/reggie-mv-online-users__8-790/archive/master.zip)

### API Declarations

Use it as you please!


### Source Code

```
online_usr.php:
<?
		/*******************/
		/* coded by reggie */
		/* date: 31/10/02 */
/**************//*-----------------*//**************/
/* file name: online_usr.php			 */
/*						 */
/* script description: online users-script	 */
/*						 */
/* junk info:					 */
/* This funktion was first written by me in a	 */
/* project in school, it was integrated in the */
/* which you also can find laying around here... */
/*						 */
/* general info:				 */
/* Ive seen a so many humongously big scripts for */
/* this sole function. But theyr all really based */
/* on this 'skelleton' therefor i wrote this code */
/* so that everybody that wishes to develope their */
/* own super-scripts got a base. the script is two */
/* separate pages (see here over), the		 */
/* create_db.php only needs to be executed once, */
/* for creation of the mysql-db.		 */
/***************************************************/
// set the amount of secounds before the page
// refresh (0 for non-refreshing page)
$ref_sek=60;
// the html head and refresh...
print "<html><head>";
if($ref_sek!=0) print "<meta http-equiv=refresh content=\"$ref_sek\">";
print "</head><body>";
// enter the correct info...
$server="xxx";
$db_usr="xxx";
$db_pass="xxx";
// if you dunno php, make a back-up copy before messing with the following code
$ip=$REMOTE_ADDR;
$tid_nu=time();
$tid_2=$tid_nu-$ref_sek;
$conn=mysql_connect($server, $db_usr,$db_pass);
$ins="insert usr_tb values ('$tid_nu','$ip')";
mysql_db_query('online_usr',"$ins");
$del="delete from usr_tb where tid_nu<$tid_2";
mysql_db_query('online_usr',"$del");
$hamta="select distinct ip from usr_tb";
$res=mysql_db_query('online_usr',"$hamta");
$online_usr=mysql_num_rows($res);
mysql_close($conn);
// print the amount of online users
print "your ip: ".$ip."<br>";
if($online_usr==1) print $online_usr." user online";
else print $online_usr." users online";
print "</body></html>";
//EOF
?>
create_db.php:
<?
		/*******************/
		/* coded by reggie */
		/* date: 31/10/02 */
/**************//*-----------------*//**************/
/* file name: create_db.php			 */
/*						 */
/* script description: create db for online-users */
/* script					 */
/*						 */
/* general info:				 */
/* this file only needs to be executed once. my */
/* suggestion is that you u/l it yourself, run it, */
/* and delete it. it cant do much harm executed */
/* more than once... but hey not much good either! */
/***************************************************/
// prolly the same as above
$server="xxx";
$db_usr="xxx";
$db_pass="xxx";
// db, table, creating table querys...
$db="online_usr";
$tb="usr_tb";
$ctbl="create table $tb
	(
		tid_nu int,
		ip int
	)";
// connecting to mysql
$conn=mysql_connect($server, $db_usr,$db_pass) or die (mysql_error());
print "connected...<br>";
// creating db
mysql_create_db($db) or die (mysql_error());
print "db $db created...<br>";
// selecting db
mysql_select_db($db) or die (mysql_error());
print "db $db selected...<br>";
// creating table
mysql_query($ctbl) or die (mysql_error());
print "table, $tb created in db $db <br>";
// closing connection to mysql
mysql_close($conn);
//EOF
?>
```

