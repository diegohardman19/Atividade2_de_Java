<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Situação do Aluno</title>
</head>
<body>
  <h1>Situação Final do Aluno</h1>

  <form id="formulario">
    <label for="aulas">Número de aulas do semestre:</label><br>
    <input type="number" id="aulas" required><br><br>

    <label for="faltas">Número de faltas do aluno:</label><br>
    <input type="number" id="faltas" required><br><br>

    <label for="p1">Primeira nota (P1):</label><br>
    <input type="number" step="0.01" id="p1" required><br><br>

    <label for="p2">Segunda nota (P2):</label><br>
    <input type="number" step="0.01" id="p2" required><br><br>

    <label for="recuperacao">Nota da recuperação (se necessário):</label><br>
    <input type="number" step="0.01" id="recuperacao"><br><br>

    <button type="submit">Calcular Situação</button>
  </form>

  <div id="resultado"></div>

  <script>
    document.getElementById("formulario").addEventListener("submit", function (event) {
      event.preventDefault();

      const aulas = parseInt(document.getElementById("aulas").value);
      const faltas = parseInt(document.getElementById("faltas").value);
      const p1 = parseFloat(document.getElementById("p1").value);
      const p2 = parseFloat(document.getElementById("p2").value);
      const recuperacaoInput = document.getElementById("recuperacao").value;

      const presenca = ((aulas - faltas) / aulas) * 100;
      const media = (p1 + p2) / 2;

      let situacao = "";
      let notaRecuperacao = null;

      if (presenca < 75) {
        situacao = "❌ Reprovado por falta";
      } else if (media >= 7) {
        situacao = "✅ Aprovado";
      } else if (media >= 5) {
        notaRecuperacao = parseFloat(recuperacaoInput);
        const mediaFinal = (media + notaRecuperacao) / 2;

        if (mediaFinal >= 5) {
          situacao = "✅ Aprovado na recuperação";
        } else {
          situacao = "❌ Reprovado na recuperação";
        }
      } else {
        situacao = "❌ Reprovado por nota";
      }

      document.getElementById("resultado").innerHTML = `
        <h2>Resultado Final</h2>
        <p><strong>Presença:</strong> ${presenca.toFixed(2)}%</p>
        <p><strong>Média:</strong> ${media.toFixed(2)}</p>
        ${notaRecuperacao !== null ? `<p><strong>Recuperação:</strong> ${notaRecuperacao.toFixed(2)}</p>` : ""}
        <p><strong>Situação:</strong> ${situacao}</p>
      `;
    });
  </script>
</body>
</html>

