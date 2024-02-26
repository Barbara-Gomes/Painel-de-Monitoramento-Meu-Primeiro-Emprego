<div align="justify">
  
# :chart_with_upwards_trend: [Painel de Monitoramento e Avaliação do Qualifica-SP | Meu Primeiro Emprego](https://app.powerbi.com/view?r=eyJrIjoiYmM5OWM2OWYtNzRkMi00MGU1LWE3YjgtMDIwYzRjNjM4Nzk4IiwidCI6IjNhNzhiMGNkLTdjOGUtNDkyOS04M2Q1LTE5MGE2Y2MwMTM2NSJ9)
  
## Qualifica-SP | Meu Primeiro Emprego
O Meu Primeiro Emprego é um programa de qualificação profissional gratuito, destinado a jovens entre 16 e 24 anos com Ensino Fundamental Completo. Uma iniciativa do Governo do Estado de São Paulo para impulsionar este público a alcançar sua primeira oportunidade no mercado de trabalho. As inscrições acontecem semestralmente, com duração aproximada de um mês. Os cursos são ofertados em instituições técnicas públicas e privadas de todo o estado, alcançando todas as Regiões Administrativas de São Paulo.

## Necessidades do Projeto
Durante o período de inscrições, a equipe responsável pelo programa e outros atores aplicam diversas estratégias de divulgação, que variam de acordo com a localidade. Por isso, era necessária uma ferramenta para monitorar o número de inscrições e avaliar se as estratégias aplicadas estavam funcionando do modo esperado. A direção técnica do programa optou por um painel construído no Power-BI.

## Objetivos
* Manipular dados extraídos via SGCP da base de dados da Coordenadoria de Ensino Técnico, Tecnológico e Profissionalizante (CETTPRO).
* Criar um painel de visualização de dados utilizando o Power BI, para monitoramento e avaliação das inscrições no Programa Meu Primeiro Emprego.

## 📝 Solução
> Os dados extraídos via SGCP estavam em formato .xlsx e, por isso, decidimos realizar a limpeza e manipulação dos dados no Excel.

**:white_check_mark: Conferimos os dados, verificando possíveis lacunas e erros.**

**:white_check_mark: Segmentações**
O trabalho de divulgação é realizado pela equipe CETTPRO, SECOM, prefeituras, unidades de ensino, residentes e outros parceiros. Por isso, era necessário criar uma painel com segmentações por Município, Regiões Administrativa, Unidade de Ensino e Centro Regional. Os dados extraídos já possuíam todas as identificações, exceto por Centro Regional. Para isso, utilizamos outra planinha com as segmentações. 

Primeiro, relacionamos os nomes dos municípios ao número do IBGE através da função PROCV, para verificar se havia alguma inconsistência entre as planilhas. Após a verificação e correção dos dados, relacionamos o nome do Município ao seu Centro Regional, utilizando as funções PROCV para criar as referências necessárias; e SEERRO para substituir os erros gerados por cursos remotos, que têm oferta em todos os municípios.
> =PROCV(C2,'Municípios CR'!A:B,2,0)  |   =SEERRO(PROCV(C2,'Municípios CR'!A:G,6,0), "Oferta em todos os municípios")

**:white_check_mark: Métrica**
Para realizar a avaliação, a direção técnica solicitou a inclusão de uma medida baseada na experiência com edições anteriores. Ainda no Excel, criamos a métrica através da função SE.
> =SE(O2<(K2*0.4),"Péssimo",SE(O2<(K2*0.8),"Ruim",SE(O2<(K2*1.3),"Bom",SE(O2<(K2*2),"Muito bom",SE(O2>=(K2*2),"Ótimo")))))

> Métrica utilizada: abaixo de 40% de inscritos por turma - péssimo; 40% a 79% – ruim; 80% a 129% – bom; entre 130% e 200% – muito bom; mais que 200% – ótimo.

**:white_check_mark: Construção do Painel**
* Realizamos o upload da planilha, conferimos se o Power-BI reconhecia todos os dados e seus respectivos formatos.


**:white_check_mark: Tabela**

**:white_check_mark: Filtros**
>Adicionamos filtros para criar as segmentações por localidade e unidade de ensino.
> Acrescentamos também segmentações por Curso e Turno, para tornar possível comparar a adesão entre eixos e horários.

**:white_check_mark: Total de Vagas, Inscritos e Turmas**

**:white_check_mark: Gráfico por Executora**

**:white_check_mark: Publicação e Atualização**


<div>
