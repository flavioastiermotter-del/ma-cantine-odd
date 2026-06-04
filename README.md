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
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Eco-Cantine Vaucluse | Bilan Semaine</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <style>
        body { font-family: sans-serif; background-color: #f4f7f5; text-align: center; padding: 20px; }
        .container { max-width: 700px; margin: auto; background: white; padding: 30px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        h1 { color: #2e7d32; margin-bottom: 5px; }
        .intro { color: #555; margin-bottom: 20px; }
        
        /* Sélecteur de jour */
        .select-jour { margin-bottom: 20px; padding: 10px; font-size: 1.1em; border-radius: 5px; border: 2px solid #2e7d32; font-weight: bold; }
        
        .poubelle { margin: 12px 0; padding: 12px; border-radius: 8px; color: white; display: flex; justify-content: space-between; align-items: center; font-weight: bold; }
        .p1 { background-color: #d35400; } 
        .p2 { background-color: #7f8c8d; } 
        .p3 { background-color: #f1c40f; color: black; } 
        .p4 { background-color: #2980b9; } 
        .p5 { background-color: #27ae60; } 
        input { width: 100px; padding: 8px; border-radius: 5px; border: none; text-align: center; font-size: 1.1em; font-weight: bold; }
        
        .charts-grid { display: flex; flex-wrap: wrap; gap: 20px; justify-content: center; margin-top: 20px; }
        .chart-box { width: 300px; }
        
        .total-box { margin-top: 25px; padding: 20px; background: #e8f5e9; border: 2px dashed #2e7d32; border-radius: 8px; }
        #total-jour { font-size: 2em; font-weight: bold; color: #2e7d32; }
        #total-semaine { font-size: 1.5em; font-weight: bold; color: #1b5e20; margin-top: 10px; }
        
        .btn-clear { margin-top: 20px; background-color: #c0392b; color: white; border: none; padding: 8px 15px; border-radius: 5px; cursor: pointer; }
    </style>
</head>
<body>

<div class="container">
    <h1>📊 Observatoire ODD - Collège du Vaucluse</h1>
    <p class="intro">Suivi hebdomadaire pour nos 700 demi-pensionnaires (en grammes)</p>
    
    <label for="choix-jour">📅 <strong>Choisir le jour à saisir :</strong> </label>
    <select id="choix-jour" class="select-jour" onchange="changerJour()">
        <option value="Lundi">Lundi</option>
        <option value="Mardi">Mardi</option>
        <option value="Jeudi">Jeudi</option>
        <option value="Vendredi">Vendredi</option>
    </select>

    <div class="poubelle p1"><span>🗑️ Déchets Alimentaires</span> <input type="number" id="input-p1" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
    <div class="poubelle p2"><span>🧻 Serviettes Papiers</span> <input type="number" id="input-p2" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
    <div class="poubelle p3"><span>🥖 Pain (Gaspillage)</span> <input type="number" id="input-p3" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
    <div class="poubelle p4"><span>📦 Emballages</span> <input type="number" id="input-p4" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
    <div class="poubelle p5"><span>🍎 Fruits Entamés</span> <input type="number" id="input-p5" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>

    <div class="charts-grid">
        <div class="chart-box">
            <h4>🍰 Répartition du jour</h4>
            <canvas id="graphCamembert"></canvas>
        </div>
        <div class="chart-box">
            <h4>📈 Évolution de la semaine</h4>
            <canvas id="graphBarres"></canvas>
        </div>
    </div>

    <div class="total-box">
        <div>Total du jour sélectionné : <span id="total-jour">0 g</span></div>
        <div id="total-semaine">Total cumulé de la semaine : 0 g</div>
        <p id="msg" style="font-weight:bold; margin-top:15px;"></p>
    </div>

    <button class="btn-clear" onclick="reinitialiserSemaine()">🔄 Effacer toute la semaine</button>
</div>

<script>
// Structure pour stocker les données de la semaine
let donneesSemaine = JSON.parse(localStorage.getItem('donneesCantine')) || {
    Lundi: [0, 0, 0, 0, 0],
    Mardi: [0, 0, 0, 0, 0],
    Jeudi: [0, 0, 0, 0, 0],
    Vendredi: [0, 0, 0, 0, 0]
};

// Initialisation du graphique en Camembert (du jour)
const ctxPie = document.getElementById('graphCamembert').getContext('2d');
let graphCamembert = new Chart(ctxPie, {
    type: 'pie',
    data: {
        labels: ['Déchets Alim.', 'Serviettes', 'Pain', 'Emballages', 'Fruits'],
        datasets: [{ data: [0, 0, 0, 0, 0], backgroundColor: ['#d35400', '#7f8c8d', '#f1c40f', '#2980b9', '#27ae60'] }]
    },
    options: { responsive: true, plugins: { legend: { position: 'bottom' } } }
});

// Initialisation du graphique en Barres (de la semaine)
const ctxBar = document.getElementById('graphBarres').getContext('2d');
let graphBarres = new Chart(ctxBar, {
    type: 'bar',
    data: {
        labels: ['Lundi', 'Mardi', 'Jeudi', 'Vendredi'],
        datasets: [{
            label: 'Total déchets (g)',
            data: [0, 0, 0, 0],
            backgroundColor: '#2e7d32'
        }]
    },
    options: { responsive: true, scales: { y: { beginAtZero: true } } }
});

// Charger le jour par défaut au démarrage
changerJour();

function changerJour() {
    let jourActuel = document.getElementById('choix-jour').value;
    let valeursJour = donneesSemaine[jourActuel];
    
    // Mettre à jour les cases de saisie avec les anciennes valeurs stockées
    document.getElementById('input-p1').value = valeursJour[0];
    document.getElementById('input-p2').value = valeursJour[1];
    document.getElementById('input-p3').value = valeursJour[2];
    document.getElementById('input-p4').value = valeursJour[3];
    document.getElementById('input-p5').value = valeursJour[4];
    
    calculerTout();
}

function sauvegarderEtCalculer() {
    let jourActuel = document.getElementById('choix-jour').value;
    
    // Enregistrer les saisies dans notre structure
    donneesSemaine[jourActuel] = [
        parseFloat(document.getElementById('input-p1').value) || 0,
        parseFloat(document.getElementById('input-p2').value) || 0,
        parseFloat(document.getElementById('input-p3').value) || 0,
        parseFloat(document.getElementById('input-p4').value) || 0,
        parseFloat(document.getElementById('input-p5').value) || 0
    ];
    
    // Sauvegarder dans la mémoire du navigateur
    localStorage.setItem('donneesCantine', JSON.stringify(donneesSemaine));
    
    calculerTout();
}

function calculerTout() {
    let jourActuel = document.getElementById('choix-jour').value;
    
    // 1. Calcul du jour sélectionné
    let valeursJour = donneesSemaine[jourActuel];
    let totalJour = valeursJour.reduce((a, b) => a + b, 0);
    document.getElementById('total-jour').innerText = totalJour.toFixed(0) + " g";
    
    // Mettre à jour le camembert du jour
    graphCamembert.data.datasets[0].data = valeursJour;
    graphCamembert.update();
    
    // 2. Calcul des totaux pour chaque jour de la semaine
    let totalLundi = donneesSemaine.Lundi.reduce((a, b) => a + b, 0);
    let totalMardi = donneesSemaine.Mardi.reduce((a, b) => a + b, 0);
    let totalJeudi = donneesSemaine.Jeudi.reduce((a, b) => a + b, 0);
    let totalVendredi = donneesSemaine.Vendredi.reduce((a, b) => a + b, 0);
    
    let totalSemaine = totalLundi + totalMardi + totalJeudi + totalVendredi;
    document.getElementById('total-semaine').innerText = "Total cumulé de la semaine : " + totalSemaine.toFixed(0) + " g";
    
    // Mettre à jour le graphique en barres de la semaine
    graphBarres.data.datasets[0].data = [totalLundi, totalMardi, totalJeudi, totalVendredi];
    graphBarres.update();
    
    // 3. Message d'alerte ODD pour la journée (Seuil à 35 000 g)
    let msg = document.getElementById('msg');
    if (totalJour === 0) { msg.innerText = ""; }
    else if (totalJour <= 35000) { msg.innerText = "🌱 Objectif ODD atteint pour " + jourActuel + " !"; msg.style.color = "green"; }
    else { msg.innerText = "⚠️ Alerte Gaspillage le " + jourActuel + " !"; msg.style.color = "red"; }
}

function reinitialiserSemaine() {
    if (confirm("Voulez-vous vraiment effacer les données de toute la semaine ?")) {
        localStorage.removeItem('donneesCantine');
        donneesSemaine = { Lundi: [0,0,0,0,0], Mardi: [0,0,0,0,0], Jeudi: [0,0,0,0,0], Vendredi: [0,0,0,0,0] };
        changerJour();
    }
}
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Eco-Cantine Vaucluse | Tableau de Bord</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <style>
        body { font-family: sans-serif; background-color: #f4f7f5; text-align: center; padding: 20px; }
        .container { max-width: 650px; margin: auto; background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        h1 { color: #2e7d32; margin-bottom: 5px; font-size: 1.8em; }
        .intro { color: #555; margin-bottom: 20px; font-size: 0.9em; }
        
        /* 1. LE RÉCAPITULATIF SEMAINE (EN HAUT) */
        .recap-semaine-box { background: #e8f5e9; border: 2px dashed #2e7d32; border-radius: 8px; padding: 15px; margin-bottom: 25px; }
        #total-semaine { font-size: 1.6em; font-weight: bold; color: #1b5e20; margin-bottom: 10px; }
        .chart-box-semaine { max-width: 450px; margin: auto; height: 160px; }

        /* 2. LES 5 BOUTONS SUR LA MÊME LIGNE */
        .jours-container { display: flex; justify-content: space-between; gap: 8px; margin-bottom: 25px; }
        .btn-jour { flex: 1; padding: 12px 5px; font-size: 1em; font-weight: bold; border: 2px solid #2e7d32; border-radius: 8px; background-color: white; color: #2e7d32; cursor: pointer; transition: all 0.2s; }
        .btn-jour.active { background-color: #2e7d32; color: white; box-shadow: 0 3px 6px rgba(0,0,0,0.2); }
        
        /* 3. FORMULAIRE DE SAISIE DU JOUR */
        .saisie-box { border: 1px solid #ddd; padding: 15px; border-radius: 8px; background-color: #fafafa; }
        .poubelle { margin: 10px 0; padding: 12px; border-radius: 8px; color: white; display: flex; justify-content: space-between; align-items: center; font-weight: bold; }
        .p1 { background-color: #d35400; } 
        .p2 { background-color: #7f8c8d; } 
        .p3 { background-color: #f1c40f; color: black; } 
        .p4 { background-color: #2980b9; } 
        .p5 { background-color: #27ae60; } 
        input { width: 90px; padding: 8px; border-radius: 5px; border: none; text-align: center; font-size: 1.1em; font-weight: bold; }
        
        .chart-box-jour { max-width: 260px; margin: 20px auto 0 auto; }
        #total-jour { font-size: 1.4em; font-weight: bold; margin-top: 10px; color: #333; }
        #msg { font-weight: bold; margin-top: 5px; }

        .btn-clear { margin-top: 25px; background-color: #c0392b; color: white; border: none; padding: 8px 15px; border-radius: 5px; cursor: pointer; font-size: 0.9em; }
    </style>
</head>
<body>

<div class="container">
    <h1>📊 Anti-Gaspi Collège Vaucluse</h1>
    <p class="intro">Suivi ODD pour nos 700 demi-pensionnaires</p>
    
    <div class="recap-semaine-box">
        <div id="total-semaine">Total Semaine : 0 g</div>
        <div class="chart-box-semaine">
            <canvas id="graphBarres"></canvas>
        </div>
    </div>

    <div class="jours-container">
        <button type="button" class="btn-jour active" id="btn-Lundi" onclick="changerJour('Lundi')">Lundi</button>
        <button type="button" class="btn-jour" id="btn-Mardi" onclick="changerJour('Mardi')">Mardi</button>
        <button type="button" class="btn-jour" id="btn-Mercredi" onclick="changerJour('Mercredi')">Merc.</button>
        <button type="button" class="btn-jour" id="btn-Jeudi" onclick="changerJour('Jeudi')">Jeudi</button>
        <button type="button" class="btn-jour" id="btn-Vendredi" onclick="changerJour('Vendredi')">Vend.</button>
    </div>

    <div class="saisie-box">
        <h3 id="titre-saisie">Saisie du Lundi</h3>
        
        <div class="poubelle p1"><span>🗑️ Déchets Alimentaires</span> <input type="number" id="input-p1" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
        <div class="poubelle p2"><span>🧻 Serviettes Papiers</span> <input type="number" id="input-p2" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
        <div class="poubelle p3"><span>🥖 Pain (Gaspillage)</span> <input type="number" id="input-p3" class="poids" value="0" min="0" oninput="sauvegarderEtCalculer()"></div>
        <div class="poubelle p4"><span>📦 Emballages</span> <input type="number" id="input-p
