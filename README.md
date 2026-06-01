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
