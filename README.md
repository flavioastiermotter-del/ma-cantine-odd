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
<div class="formulaire-cantine">
  <h2>📋 Saisie des données du jour</h2>
  
  <!-- Section Contexte -->
  <div class="section-repas">
    <label for="repas">👥 Nombre de repas servis aujourd'hui :</label>
    <input type="number" id="repas" value="700" min="1">
  </div>
  
  <hr>

  <!-- Section Poubelles -->
  <div class="poubelle p-alim">
    <label>🗑️ Déchets Alimentaires (restes d'assiettes) :</label>
    <input type="number" class="poids" value="0" step="0.1"> kg
  </div>

  <div class="poubelle p-serviettes">
    <label>🧻 Serviettes en Papier :</label>
    <input type="number" class="poids" value="0" step="0.1"> kg
  </div>

  <div class="poubelle p-pain">
    <label>🥖 Pain consommé et jeté :</label>
    <input type="number" class="poids" value="0" step="0.1"> kg
  </div>

  <div class="poubelle p-emballages">
    <label>📦 Emballages (yaourts, plastiques) :</label>
    <input type="number" class="poids" value="0" step="0.1"> kg
  </div>

  <div class="poubelle p-fruits">
    <label>🍎 Fruits entamés ou non consommés :</label>
    <input type="number" class="poids" value="0" step="0.1"> kg
  </div>
</div>
