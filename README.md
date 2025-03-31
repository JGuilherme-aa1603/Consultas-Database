# Consultas-Database

## 1. Crie uma consulta que mostre todos as pessoas que compraram medicamentos e são da cidade de Belém.

SELECT DISTINCT P.pac_nome

FROM tbl_receituario R

JOIN tbl_paciente P ON R.rec_paciente = P.pac_identidade

JOIN tbl_cidade C ON P.pac_cidade = C.cid_codigo

WHERE C.cid_nome = 'Belém';
