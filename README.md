<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Anti-Gaspi : Collège du Vaucluse</title>
    <style>
        body { font-family: sans-serif; background-color: #f4f4f4; color: #333; text-align: center; }
        .container { width: 80%; margin: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
        h1 { color: #2e7d32; }
        .poubelle-list { display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; }
        .card { border: 2px solid #2e7d32; border-radius: 8px; padding: 15px; width: 180px; }
        .footer { margin-top: 30px; font-size: 0.9em; color: #666; }
    </style>
</head>
<body>

<div class="container">
    <h1>Stop au Gaspillage Alimentaire 🍎</h1>
    <p>Projet ODD - Suivi des déchets pour 700 élèves</p>

    <div class="poubelle-list">
        <div class="card"><h3>Déchets Alimentaires</h3><p id="tri">En attente...</p></div>
        <div class="card"><h3>Serviettes Papier</h3><p id="serviettes">En attente...</p></div>
        <div class="card"><h3>Pain</h3><p id="pain">En attente...</p></div>
        <div class="card"><h3>Emballages</h3><p id="emballages">En attente...</p></div>
        <div class="card"><h3>Fruits Entamés</h3><p id="fruits">En attente...</p></div>
    </div>

    <div class="footer">
        <p>Collège du Vaucluse - Engagement pour la planète</p>
    </div>
</div>

</body>
</html>
