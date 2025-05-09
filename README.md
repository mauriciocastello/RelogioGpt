
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Relógio e Calendário Interativo</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
      color: white;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      min-height: 100vh;
    }
    h1 {
      margin-top: 20px;
      font-size: 2.5rem;
    }
    #clock {
      font-size: 4rem;
      margin: 20px;
    }
    #calendar {
      background-color: rgba(255, 255, 255, 0.1);
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
    }
    th, td {
      text-align: center;
      padding: 10px;
      border: 1px solid #ccc;
      color: white;
    }
    .today {
      background-color: #ff9800;
      color: black;
      border-radius: 50%;
    }
    #curiosidade, #tempo {
      margin: 20px;
      font-size: 1.2rem;
      text-align: center;
      max-width: 500px;
      padding: 10px;
      background-color: rgba(255, 255, 255, 0.2);
      border-radius: 10px;
    }
    .social {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
    .social a {
      text-decoration: none;
      color: white;
      padding: 10px 15px;
      border: 1px solid white;
      border-radius: 5px;
      transition: background 0.3s;
    }
    .social a:hover {
      background: white;
      color: #2c5364;
    }
    .ads {
      margin-top: 30px;
      background-color: rgba(255,255,255,0.15);
      padding: 10px;
      border-radius: 10px;
      min-height: 90px;
      width: 320px;
    }
  </style>
</head>
<body>
  <h1>Relógio e Calendário Interativo</h1>
  <div id="clock"></div>
  <div id="calendar"></div>
  <div id="curiosidade">Carregando curiosidade do dia...</div>
  <div id="tempo">Carregando previsão do tempo...</div>
  <div class="social">
    <a href="https://api.whatsapp.com/send?text=Veja%20esse%20site%20interativo!%20https://seusite.com" target="_blank">Compartilhar no WhatsApp</a>
    <a href="https://www.facebook.com/sharer/sharer.php?u=https://seusite.com" target="_blank">Compartilhar no Facebook</a>
  </div>

  <div class="ads">
    <!-- Bloco de anúncio Google AdSense -->
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" crossorigin="anonymous"></script>
    <ins class="adsbygoogle"
         style="display:block"
         data-ad-client="ca-pub-xxxxxxxxxxxxxxxx"
         data-ad-slot="1234567890"
         data-ad-format="auto"
         data-full-width-responsive="true"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>

  <script>
    function updateClock() {
      const now = new Date();
      const time = now.toLocaleTimeString('pt-BR');
      document.getElementById('clock').textContent = time;
    }
    setInterval(updateClock, 1000);
    updateClock();

    function generateCalendar() {
      const calendar = document.getElementById('calendar');
      const now = new Date();
      const year = now.getFullYear();
      const month = now.getMonth();
      const today = now.getDate();
      const months = ['Janeiro','Fevereiro','Março','Abril','Maio','Junho','Julho','Agosto','Setembro','Outubro','Novembro','Dezembro'];
      const firstDay = new Date(year, month, 1).getDay();
      const lastDate = new Date(year, month + 1, 0).getDate();
      let html = `<h2>${months[month]} ${year}</h2><table><tr>`;
      const days = ['Dom','Seg','Ter','Qua','Qui','Sex','Sáb'];
      days.forEach(day => html += `<th>${day}</th>`);
      html += '</tr><tr>';
      for (let i = 0; i < firstDay; i++) html += '<td></td>';
      for (let day = 1; day <= lastDate; day++) {
        const cls = day === today ? 'today' : '';
        html += `<td class="${cls}">${day}</td>`;
        if ((day + firstDay) % 7 === 0) html += '</tr><tr>';
      }
      html += '</tr></table>';
      calendar.innerHTML = html;
    }
    generateCalendar();

    const curiosidades = [
      "Você sabia que um dia em Vênus é mais longo que um ano em Vênus?",
      "O primeiro relógio mecânico foi criado no século XIII.",
      "Calendários maias previam eclipses com grande precisão.",
      "O calendário gregoriano foi introduzido em 1582.",
      "Relógios atômicos são tão precisos que erram apenas 1 segundo a cada 100 milhões de anos."
    ];
    function mostrarCuriosidade() {
      const index = new Date().getDate() % curiosidades.length;
      document.getElementById('curiosidade').textContent = curiosidades[index];
    }
    mostrarCuriosidade();

    function mostrarPrevisaoTempo() {
      document.getElementById('tempo').textContent = 'Previsão do tempo: Sol com algumas nuvens. Máx: 28°C, Mín: 17°C (exemplo fixo).';
    }
    mostrarPrevisaoTempo();
  </script>
</body>
</html>
  
