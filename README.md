
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
    import streamlit as st

# 1. Le Titre du site
st.title("📊 Observatoire du Gaspillage - Collège du Vaucluse")
st.subheader("Objectif ODD n°12 : 700 demi-pensionnaires engagés !")

st.write("Entrez les pesées du jour effectuées à la cantine :")

# 2. Les 5 cases pour tes 5 poubelles
dechets_alim = st.number_input("🗑️ Déchets alimentaires (restes d'assiettes) en kg", min_value=0.0, value=0.0, step=0.5)
serviettes = st.number_input("🧻 Serviettes papiers en kg", min_value=0.0, value=0.0, step=0.1)
pain = st.number_input("🥖 Pain gaspillé en kg", min_value=0.0, value=0.0, step=0.5)
emballages = st.number_input("📦 Emballages en kg", min_value=0.0, value=0.0, step=0.1)
fruits = st.number_input("🍎 Fruits entamés en kg", min_value=0.0, value=0.0, step=0.1)

# 3. Le calcul automatique
total = dechets_alim + serviettes + pain + emballages + fruits

st.markdown("---")

# 4. L'affichage du résultat
st.metric(label="TOTAL DES DÉCHETS AUJOURD'HUI", value=f"{total:.2f} kg")

# 5. Le message intelligent (Alerte ODD)
if total > 0:
    if total <= 35: # Limite fixée à 50g par élève pour 700 élèves
        st.success("🌱 Bravo ! Objectif ODD atteint. Faible impact sur la planète aujourd'hui.")
    else:
        st.error("⚠️ Alerte Gaspillage ! Attention, nous dépassons l'objectif fixé pour le collège.")
    <div id="resultat">0 kg</div>
  </div>
</div>
