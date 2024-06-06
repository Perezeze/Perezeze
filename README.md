<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Controle de Gastos</title>
</head>
<body>
    <h1>Controle de Gastos</h1>
    <form id="gastoForm">
        <label for="data">Data:</label><br>
        <input type="date" id="data" name="data"><br><br>

        <label for="mes">Mês:</label><br>
        <input type="text" id="mes" name="mes"><br><br>

        <label for="tipoGasto">Tipo de Gasto:</label><br>
        <input type="text" id="tipoGasto" name="tipoGasto"><br><br>

        <label for="cartaoCredito">Cartão de Crédito:</label><br>
        <input type="text" id="cartaoCredito" name="cartaoCredito"><br><br>

        <label for="statusPagamento">Status de Pagamento:</label><br>
        <input type="text" id="statusPagamento" name="statusPagamento"><br><br>

        <input type="submit" value="Enviar">
    </form>

    <script>
        const form = document.getElementById('gastoForm');
        form.addEventListener('submit', async (e) => {
            e.preventDefault();

            const data = new FormData(form);
            const value = Object.fromEntries(data.entries());

            const response = await fetch('https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec', {
                method: 'POST',
                body: JSON.stringify(value),
                headers: {
                    'Content-Type': 'application/json'
                }
            });

            const result = await response.json();
            alert(result.message);
        });
    </script>
</body>
</html>
