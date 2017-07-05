    DROP TABLE IF EXISTS `z_migu_monthnotice_1`;

    CREATE TABLE z_migu_monthnotice_1  SELECT sign,id FROM z_migu_monthnotice GROUP  BY sign HAVING(COUNT(sign)>1);

    DELETE FROM z_migu_monthnotice  WHERE sign in (SELECT sign FROM z_migu_monthnotice_1 ) 
    AND id not in (SELECT id FROM z_migu_monthnotice_1  );

    DROP TABLE IF EXISTS `z_migu_monthnotice_1`;