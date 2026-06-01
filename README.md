
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
