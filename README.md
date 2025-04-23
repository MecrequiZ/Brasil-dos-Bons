<script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
        </script><!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Brasil dos Bons: Voto Livre, Cidadania Forte</title>
    <meta name="description" content="Acabe com o voto obrigatório e implemente educação cívica para transformar o Brasil em uma referência global. Junte-se ao movimento!">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: #333;
        }

        header {
            background: linear-gradient(90deg, #009c3b, #ffdf00);
            color: white;
            text-align: center;
            padding: 60px 20px;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        header p {
            font-size: 1.2em;
        }

        nav {
            background-color: #002776;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        nav ul {
            list-style: none;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: bold;
            padding: 10px;
        }

        nav a:hover {
            background-color: #ffdf00;
            color: #002776;
            border-radius: 5px;
        }

        section {
            max-width: 1000px;
            margin: 40px auto;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        section h2 {
            color: #009c3b;
            font-size: 2em;
            margin-bottom: 20px;
        }

        section p, section ul {
            font-size: 1.1em;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        section ul {
            list-style: disc;
            padding-left: 20px;
        }

        .cta-button {
            display: inline-block;
            background-color: #ffdf00;
            color: #002776;
            padding: 15px 30px;
            text-decoration: none;
            font-weight: bold;
            border-radius: 5px;
            margin: 20px 0;
            transition: background-color 0.3s;
        }

        .cta-button:hover {
            background-color: #e6c700;
        }

        form {
            display: flex;
            flex-direction: column;
            gap: 15px;
            max-width: 500px;
            margin: 0 auto;
        }

        form input, form textarea {
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }

        form button {
            background-color: #009c3b;
            color: white;
            border: none;
            padding: 15px;
            font-size: 1.1em;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        form button:hover {
            background-color: #007a2f;
        }

        .share-buttons {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 20px;
        }

        .share-buttons a {
            background-color: #002776;
            color: white;
            padding: 10px 20px;
            text-decoration: none;
            border-radius: 5px;
            font-size: 0.9em;
        }

        .share-buttons a:hover {
            background-color: #001a4d;
        }

        footer {
            background-color: #002776;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 40px;
        }

        footer a {
            color: #ffdf00;
            text-decoration: none;
        }

        @media (max-width: 768px) {
            header h1 {
                font-size: 1.8em;
            }

            nav ul {
                flex-direction: column;
                align-items: center;
            }

            section {
                margin: 20px;
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Brasil dos Bons: Voto Livre, Cidadania Forte</h1>
        <p>Junte-se ao movimento para acabar com o voto obrigatório e ensinar cidadania nas escolas, transformando o Brasil em uma referência global!</p>
    </header>

    <nav>
        <ul>
            <li><a href="#problema">O Problema</a></li>
            <li><a href="#solucao">A Solução</a></li>
            <li><a href="#beneficios">Benefícios</a></li>
            <li><a href="#participe">Participe</a></li>
        </ul>
    </nav>

    <section id="problema">
        <h2>O Problema: Por que o Brasil precisa mudar?</h2>
        <p>A corrupção e a ineficiência política impedem o Brasil de ser uma referência global. A raiz do problema está:</p>
        <ul>
            <li><strong>Voto Obrigatório</strong>: Força milhões de eleitores desinteressados a votar, facilitando a compra de votos e a eleição de políticos corruptos.</li>
            <li><strong>Falta de Educação Cívica</strong>: Escolas não ensinam ética, transparência ou como fiscalizar políticos, perpetuando a tolerância à corrupção.</li>
            <li><strong>Clientelismo</strong>: Políticos trocam favores (ex.: cestas básicas) por votos, mantendo um ciclo de corrupção e desigualdade.</li>
        </ul>
        <p>Resultado: Um país com alta corrupção (94º no Índice de Percepção da Corrupção 2023), desconfiança nas urnas (30% dos brasileiros, Datafolha 2022) e serviços públicos precários.</p>
    </section>

    <section id="solucao">
        <h2>A Solução: Voto Facultativo e Educação Cívica</h2>
        <p>Duas medidas simples podem transformar o Brasil a longo prazo:</p>
        <ul>
            <li><strong>Fim do Voto Obrigatório</strong>: Tornar o voto facultativo, permitindo que apenas eleitores engajados escolham representantes. Isso reduz a manipulação e melhora a qualidade dos eleitos.</li>
            <li><strong>Educação Cívica Obrigatória</strong>: Incluir a disciplina “Cidadania e Ética” nas escolas, ensinando transparência, responsabilidade e como combater a corrupção.</li>
        </ul>
        <p>Essas mudanças são fáceis de implementar, baratas e respeitam a democracia, criando cidadãos conscientes e um sistema político mais ético.</p>
        <a href="#participe" class="cta-button">Quero Apoiar!</a>
    </section>

    <section id="beneficios">
        <h2>Benefícios: Como o Brasil será melhor?</h2>
        <p>Com voto facultativo e educação cívica, o Brasil pode se tornar uma referência global:</p>
        <ul>
            <li><strong>Em 5 anos</strong>: Menos políticos corruptos, com 20% menos compra de votos e eleições mais transparentes.</li>
            <li><strong>Em 10 anos</strong>: 30 milhões de jovens formados em ética, exigindo transparência e reduzindo a corrupção em 30%.</li>
            <li><strong>Em 20 anos</strong>: Brasil no top 30 do Índice de Percepção da Corrupção, com confiança pública (80%) e crescimento econômico (PIB per capita de US$ 15.000).</li>
        </ul>
        <p>Um Brasil de “pessoas boas” liderando, com segurança, prosperidade e orgulho nacional!</p>
    </section>

    <section id="participe">
        <h2>Participe do Movimento!</h2>
        <p>Assine nossa petição para acabar com o voto obrigatório e implementar educação cívica. Compartilhe com amigos e ajude a transformar o Brasil!</p>
        <form action="https://formspree.io/f/your-form-id" method="POST">
            <input type="text" name="name" placeholder="Seu Nome" required>
            <input type="email" name="email" placeholder="Seu E-mail" required>
            <textarea name="message" placeholder="Por que você apoia essa causa?" rows="4"></textarea>
            <button type="submit">Assinar Petição</button>
        </form>
        <div class="share-buttons">
            <a href="https://x.com/intent/tweet?text=Transforme o Brasil com voto livre e cidadania forte! Junte-se ao movimento: brasil-dos-bons.com #VotoFacultativo" target="_blank">Compartilhar no X</a>
            <a href="https://api.whatsapp.com/send?text=Transforme o Brasil com voto livre e cidadania forte! Confira: brasil-dos-bons.com" target="_blank">Compartilhar no WhatsApp</a>
            <a href="mailto:?subject=Transforme o Brasil!&body=Conheça o movimento para acabar com o voto obrigatório e ensinar cidadania: brasil-dos-bons.com" target="_blank">Enviar por E-mail</a>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 Brasil dos Bons. Todos os direitos reservados.</p>
        <p>Contato: <a href="mailto:contato@brasil-dos-bons.com">contato@brasil-dos-bons.com</a> | Siga-nos no <a href="https://x.com/brasildosbons" target="_blank">X</a></p>
    </footer>

    <script>
        // Smooth scroll para links da navegação
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href').substring(1);
                document.getElementById(targetId).scrollIntoView({ behavior: 'smooth' });
            });
        });

        // Confirmação de envio do formulário
        document.querySelector('form').addEventListener('submit', function(e) {
            alert('Obrigado por apoiar! Sua assinatura foi enviada.');
        });
    </script>
</body>
</html>
