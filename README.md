<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Eco-Cantine Vaucluse | ODD</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <style>
        body { font-family: sans-serif; background-color: #f4f7f5; text-align: center; padding: 20px; }
        .container { max-width: 600px; margin: auto; background: white; padding: 30px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        h1 { color: #2e7d32; margin-bottom: 5px; }
        .intro { color: #555; margin-bottom: 25px; }
        .poubelle { margin: 12px 0; padding: 12px; border-radius: 8px; color: white; display: flex; justify-content: space-between; align-items: center; font-weight: bold; }
        .p1 { background-color: #d35400; } 
        .p2 { background-color: #7f8c8d; } 
        .p3 { background-color: #f1c40f; color: black; } 
        .p4 { background-color: #2980b9; } 
        .p5 { background-color: #27ae60; } 
        input { width: 100px; padding: 8px; border-radius: 5px; border: none; text-align: center; font-size: 1.1em; font-weight: bold; }
        
        .total-box { margin-top: 25px; padding: 20px; background: #e8f5e9; border: 2px dashed #2e7d32; border-radius: 8px; }
        #total { font-size: 2.5em; font-weight: bold; color: #2e7d32; }
        
        /* Zone du graphique */
        .chart-container { max-width: 400px; margin: 30px auto 10px auto; }
    </style>
</head>
<body>

<div class="container">
    <h1>📊 Anti-Gaspi Collège Vaucluse</h1>
    <p class="intro">Suivi des ODD pour nos 700 demi-pensionnaires (en grammes)</p>
    
    <div class="poubelle p1"><span>🗑️ Déchets Alimentaires</span> <input type="number" class="poids" value="0" min="0" oninput="calculer()"></div>
    <div class="poubelle p2"><span>🧻 Serviettes Papiers</span> <input type="number" class="poids" value="0" min="0" oninput="calculer()"></div>
    <div class="poubelle p3"><span>🥖 Pain (Gaspillage)</span> <input type="number" class="poids" value="0" min="0" oninput="calculer()"></div>
    <div class="poubelle p4"><span>📦 Emballages</span> <input type="number" class="poids" value="0" min="0" oninput="calculer()"></div>
    <div class="poubelle p5"><span>🍎 Fruits Entamés</span> <input type="number" class="poids" value="0" min="0" oninput="calculer()"></div>

    <div class="chart-container">
        <canvas id="graphiqueCamembert"></canvas>
    </div>

    <div class="total-box">
        <h3>TOTAL DES DÉCHETS</h3>
        <div id="total">0 g</div>
        <p id="msg" style="font-weight:bold; margin-top:15px; font-size: 1.1em;"></p>
    </div>
</div>

<script>
// Configuration initiale du graphique vide
let monGraphique;
const ctx = document.getElementById('graphiqueCamembert').getContext('2d');

monGraphique = new Chart(ctx, {
    type: 'pie',
    data: {
        labels: ['Déchets Alim.', 'Serviettes', 'Pain', 'Emballages', 'Fruits'],
        datasets: [{
            data: [0, 0, 0, 0, 0],
            backgroundColor: ['#d35400', '#7f8c8d', '#f1c40f', '#2980b9', '#27ae60']
        }]
    },
    options: {
        responsive: true,
        plugins: {
            legend: { position: 'bottom' }
        }
    }
});

// Fonction qui calcule le total et met à jour le camembert
function calculer() {
    let inputs = document.querySelectorAll('.poids');
    let total = 0;
    let listeValeurs = [];
    
    // On récupère les valeurs pour le total et pour le graphique
    inputs.forEach(i => {
        let valeur = parseFloat(i.value) || 0;
        total += valeur;
        listeValeurs.push(valeur);
    });
    
    // Mettre à jour le texte du total
    document.getElementById('total').innerText = total.toFixed(0) + " g";
    
    // Mettre à jour les parts du camembert
    monGraphique.data.datasets[0].data = listeValeurs;
    monGraphique.update();
    
    // Message d'alerte (Seuil à 35 000 g soit 35 kg)
    let msg = document.getElementById('msg');
    if (total === 0) { msg.innerText = ""; }
    else if (total <= 35000) { msg.innerText = "🌱 Bravo, objectif ODD atteint pour le collège !"; msg.style.color = "green"; }
    else { msg.innerText = "⚠️ Alerte ! Le gaspillage est trop élevé aujourd'hui."; msg.style.color = "red"; }
}
</script>

</body>
</html>
