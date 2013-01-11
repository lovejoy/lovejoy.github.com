---
layout: post
title: "Yii中比较好的insert语句"
date: 2013-01-11 15:44
comments: true
categories: Yii
---

虽然yii提供有插入数据库的功能，但性能上不确定，所以一般我还是自己抽象个出来

    public static function insert($tblName,$props = array()){
        $sql = 'insert into '.$tblName.'(';
        $valuesSql = 'values(';
        foreach($props as $field=>$val){
            $sql .= $field.',';
            $tmp = addslashes($val);
            $valuesSql .= "'$tmp',";
        }
        $sql = rtrim($sql,',');
        $sql .= ') ';
        $valuesSql = rtrim($valuesSql,',');
        $valuesSql .=')';
        $sql .= $valuesSql;
        return Yii::app()->db->createCommand($sql)->execute();
    }

上面的代码基本解决了常见的问题，这里用了addslashes来加转义符号,需要你先用
get_magic_quotes_gpc()函数来看下你自己服务器的配置，为1是用加上转义的操作。
