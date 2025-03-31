# Consultas-Database

## 1. Crie uma consulta que mostre todos as pessoas que compraram medicamentos e são da cidade de Belém.

SELECT DISTINCT P.pac_nome

FROM tbl_receituario R

JOIN tbl_paciente P ON R.rec_paciente = P.pac_identidade

JOIN tbl_cidade C ON P.pac_cidade = C.cid_codigo

WHERE C.cid_nome = 'Belém';

## 2. Mostre uma relação com nome completo do médico, CRM e Cidade daqueles que prescreveram o medicamento Rivotril.

SELECT DISTINCT MEDICO.medico_nome, MEDICO.medico_crm, MEDICO.medico_cidade

FROM tbl_receituario R

JOIN tbl_medico MEDICO ON R.rec_medico = MEDICO.medico_crm

JOIN tbl_medicamento MEDICAMENTO ON R.rec_prescricao = MEDICAMENTO.medicamento_codigo

WHERE MEDICAMENTO.medicamento_nome = 'Rivotril'

## 3. Mostre todos os medicamentos que foram vendidos sob a supervisão do Farmacêutico “José Tranquilino da Conceição”.

SELECT DISTINCT MEDICAMENTO.medicamento_nome

FROM tbl_receituario R

JOIN tbl_medicamento MEDICAMENTO ON R.rec_prescricao = MEDICAMENTO.medicamento_codigo

JOIN tbl_farmaceutico F ON R.rec_fornecedor = F.far_codigo

WHERE F.far_nome = 'José Tranquilino da Conceição';

## 4. Mostre uma relação com Nome do Emitente (Médico), CRM, Nome do Comprador (Paciente) e Telefone do Comprador.

SELECT MEDICO.medico_nome, MEDICO.medico_crm, P.pac_nome, P.pac_telefone

FROM tbl_receituario R

JOIN tbl_medico MEDICO ON R.rec_medico = MEDICO.medico_crm

JOIN tbl_paciente P ON R.rec_paciente = P.pac_identidade
