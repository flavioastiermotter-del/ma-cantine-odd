# ma-cantine-odd
<div class="site">
  <h1>Indicateur ODD : Cantine du Vaucluse 🌍</h1>
  <p class="intro">Suivi du gaspillage pour nos 700 demi-pensionnaires.</p>

  <div class="ZonePoubelles">
    <div class="bloc p1">
      <h3>Détritus Alimentaires</h3>
      <input type="number" class="valeur" placeholder="Poids en kg" oninput="calculerTotal()">
    </div>

    <div class="bloc p2">
      <h3>Serviettes Papiers</h3>
      <input type="number" class="valeur" placeholder="Poids en kg" oninput="calculerTotal()">
    </div>

    <div class="bloc p3">
      <h3>Pain Perdu</h3>
      <input type="number" class="valeur" placeholder="Poids en kg" oninput="calculerTotal()">
    </div>

    <div class="bloc p4">
      <h3>Emballages</h3>
      <input type="number" class="valeur" placeholder="Poids en kg" oninput="calculerTotal()">
    </div>

    <div class="bloc p5">
      <h3>Fruits Entamés</h3>
      <input type="number" class="valeur" placeholder="Poids en kg" oninput="calculerTotal()">
    </div>
  </div>

  <div class="total-section">
    <h2>Total des déchets aujourd'hui :</h2>
    <div id="resultat">0 kg</div>
  </div>
</div>
body {
  font-family: 'Arial', sans-serif;
  background-color: #f0f4f1;
  padding: 20px;
}

.site {
  max-width: 800px;
  margin: 0 auto;
  background: white;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  text-align: center;
}

h1 { color: #2c3e50; }
.intro { color: #7f8c8d; font-size: 1.1em; }

.ZonePoubelles {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  justify-content: center;
  margin-top: 30px;
}

.bloc {
  width: 180px;
  padding: 15px;
  border-radius: 10px;
  color: white;
}

/* Couleurs des poubelles */
.p1 { background-color: #d35400; } /* Marron/Orange pour le repas */
.p2 { background-color: #7f8c8d; } /* Gris pour le papier */
.p3 { background-color: #f1c40f; color: #2c3e50; } /* Jaune pour le pain */
.p4 { background-color: #2980b9; } /* Bleu pour le recyclage */
.p5 { background-color: #27ae60; } /* Vert pour les fruits */

input {
  width: 80%;
  padding: 8px;
  border: none;
  border-radius: 5px;
  margin-top: 10px;
  text-align: center;
}

.total-section {
  margin-top: 40px;
  padding: 20px;
  background-color: #e8f8f5;
  border-radius: 10px;
}

#resultat {
  font-size: 2.5em;
  font-weight: bold;
  color: #16a085;
}
