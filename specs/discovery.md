# Análise de Discovery

## Contexto

A empresa precisa de uma aplicação web de previsão do tempo para permitir que
usuários consultem rapidamente as condições meteorológicas de uma cidade. A
experiência deve atender tanto consultas pontuais sobre o clima atual quanto o
planejamento dos próximos dias.

O produto inicial deve contemplar busca de cidades, visualização do clima atual,
previsão para cinco dias, alternância entre Celsius e Fahrenheit e uso adequado
em dispositivos móveis.

## Requisitos Funcionais

- **RF01 — Buscar cidade:** permitir que o usuário informe o nome de uma cidade
  e selecione o local correto quando houver cidades com nomes iguais.
- **RF02 — Exibir clima atual:** apresentar, para a cidade selecionada, a
  temperatura, a condição climática e os principais dados disponíveis, como
  sensação térmica, umidade e vento.
- **RF03 — Exibir previsão:** apresentar a previsão dos cinco dias seguintes,
  incluindo temperaturas mínima e máxima e a condição climática de cada dia.
- **RF04 — Alternar unidade:** permitir alternar entre Celsius e Fahrenheit e
  atualizar todas as temperaturas exibidas de forma consistente.
- **RF05 — Informar estados da operação:** indicar ao usuário carregamento,
  ausência de resultados e falhas na busca ou na consulta da previsão.
- **RF06 — Tentar novamente:** oferecer uma ação para repetir a consulta quando
  ocorrer uma falha temporária de rede ou do serviço de previsão.

## Requisitos Não-Funcionais

- **RNF01 — Responsividade:** a aplicação deve funcionar em smartphones,
  tablets e desktops, com prioridade para telas pequenas.
- **RNF02 — Acessibilidade:** controles devem ser utilizáveis por teclado,
  possuir rótulos semânticos e manter contraste suficiente para leitura.
- **RNF03 — Performance:** a busca e a atualização da previsão devem apresentar
  feedback imediato e evitar bloqueios perceptíveis na interface.
- **RNF04 — Resiliência:** indisponibilidade da rede ou do serviço externo deve
  resultar em uma mensagem compreensível, sem deixar a interface em estado
  indefinido.
- **RNF05 — Compatibilidade:** a solução deve funcionar nos navegadores modernos
  mais comuns em dispositivos móveis e desktop.
- **RNF06 — Clareza dos dados:** datas, horários, temperaturas e unidades devem
  ser apresentados de maneira consistente e compreensível para o usuário.

## Riscos

| Risco | Probabilidade | Impacto | Mitigação |
| --- | --- | --- | --- |
| Serviço meteorológico indisponível ou sujeito a limite de requisições | Média | Alto | Definir tratamento de erros, oferecer nova tentativa e considerar cache de curta duração. |
| Cidade com nome ambíguo ou duplicado | Alta | Médio | Exibir informações adicionais, como estado, país e coordenadas, nas opções de resultado. |
| Experiência inadequada em telas pequenas | Média | Alto | Adotar abordagem mobile-first e validar os fluxos principais em diferentes larguras. |
| Conversão incorreta entre Celsius e Fahrenheit | Baixa | Alto | Centralizar a conversão em uma função testável e validar valores representativos. |
| Dados meteorológicos incompletos ou difíceis de interpretar | Média | Médio | Definir um conjunto mínimo de dados e comunicar claramente quando um dado não estiver disponível. |
| Dependência de conexão com a internet | Alta | Médio | Exibir estados de carregamento e erro claros, preservando a última consulta quando isso for suportado. |

## Perguntas em Aberto

1. Qual provedor ou API de dados meteorológicos será utilizado? Há restrições de
   custo, cota ou necessidade de chave de API?
2. A previsão de cinco dias inclui o dia atual ou começa no dia seguinte?
3. Qual deve ser a unidade padrão na primeira visita: Celsius ou Fahrenheit?
4. A aplicação deve detectar automaticamente a localização do usuário ou a
   cidade sempre será informada por busca?
5. Quais dados fazem parte do clima atual e da previsão além de temperatura e
   condição climática?
6. A aplicação precisa suportar localização, idioma e formatos de data além de
   pt-BR?
7. Deve ser possível favoritar cidades ou manter o histórico de buscas?
8. O produto precisa oferecer algum comportamento offline ou apenas comunicar a
   indisponibilidade da rede?
9. Existem requisitos de privacidade, analytics ou retenção de dados de busca?

## Suposições

- A primeira versão será uma aplicação web responsiva, sem necessidade de
  instalação nativa.
- O usuário consultará uma cidade por vez e não precisará criar uma conta.
- A consulta dependerá de um serviço externo de geolocalização e previsão do
  tempo.
- A interface será inicialmente disponibilizada em português do Brasil.
- Os usuários terão conexão com a internet durante a consulta.
- A previsão de cinco dias será exibida em uma visão diária, e não em intervalos
  horários detalhados.
- A alternância de unidade será uma preferência local do dispositivo, sem
  necessidade de sincronização entre usuários ou sessões.