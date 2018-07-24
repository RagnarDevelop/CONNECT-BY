# CONNECT-BY

- em oracle 

SELECT LEVEL,LPAD(' ',2*(LEVEL -1)) || TESTE_lig_id,TESTE_id,TESTE_enc_TESTE
     FROM TESTE
START WITH TESTE_enc_TESTE = ''
CONNET BY PRIOR TESTE_lig_id = TESTE_id;
-- em postgress

WITH RECURSIVE q AS (
   SELECT po.TESTE_lig_id,po.TESTE,po.TESTE_enc_TESTE
     FROM TESTE po
    WHERE po.TESTE_enc_TESTE = 'SASDAS'
   UNION ALL
   SELECT po.TESTE_lig_id,po.TESTE,po.TESTE_enc_TESTE
     FROM TESTE po
     JOIN q ON q.TESTE_lig_id= po.TESTE
)
SELECT * FROM q;


https://www.enterprisedb.com/docs/en/9.5/eeguide/EDB_Postgres_Enterprise_Guide.1.036.html
