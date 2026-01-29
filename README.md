
import streamlit as st
import random
import time
import pandas as pd

# Ρύθμιση Σελίδας
st.set_page_config(page_title="Quantum Command Center", page_icon="💎", layout="wide")

# --- CUSTOM CSS ΓΙΑ QUANTUM LOOK ---
st.markdown("""
    <style>
    .main { background-color: #0e1117; color: #00ffcc; }
    .stMetric { background-color: #1a1c24; padding: 15px; border-radius: 10px; border: 1px solid #00ffcc; }
    div.stButton > button:first-child { background-color: #00ffcc; color: black; font-weight: bold; width: 100%; }
    </style>
    """, unsafe_allow_html=True)

st.title("💎 Ternary Quantum Mesh - Command Center v1.0")
st.write("Σύστημα Διαχείρισης Τριαδικού Πλέγματος σε Πραγματικές Συνθήκες")
st.write("---")

# --- SIDEBAR: ΠΡΑΓΜΑΤΙΚΕΣ ΣΥΝΘΗΚΕΣ ---
st.sidebar.header("🌍 Περιβάλλον Κόμβων (Real-time)")
temp = st.sidebar.slider("Θερμοκρασία (Kelvin)", 273, 315, 298)
pressure = st.sidebar.slider("Βαρομετρική Πίεση (bar)", 0.5, 2.0, 1.0)

st.sidebar.divider()
st.sidebar.subheader("🤖 AI Stabilizer Status")
st.sidebar.code("ACTIVE - Shielding Qutrits")

# --- ΚΥΡΙΩΣ ΠΙΝΑΚΑΣ (3 ΠΥΛΩΝΕΣ) ---
col1, col2, col3 = st.columns(3)

# 🔐 ΠΥΛΩΝΑΣ 1: ΑΣΦΑΛΕΙΑ (Quantum Vault)
with col1:
    st.header("🔐 Ασφάλεια")
    # Υπολογισμός ακεραιότητας βάσει θερμοκρασίας
    fidelity = max(0.0, 1.0 - (temp - 298) * 0.015)
    st.metric(label="Quantum Fidelity (Ακεραιότητα)", value=f"{fidelity*100:.2f}%")
    if fidelity > 0.85:
        st.success("🔒 Network Status: SECURE")
    else:
        st.error("⚠️ Decoherence Detected: High Noise")

# 🔬 ΠΥΛΩΝΑΣ 2: ΕΠΙΣΤΗΜΗ (3D Lattice Simulation)
with col2:
    st.header("🔬 Επιστήμη")
    # Προσομοίωση προόδου
    progress_val = st.slider("Ανάλυση Μοριακής Δομής", 0, 100, 65)
    st.progress(progress_val)
    st.write(f"Στόχος: Σύνθεση Υλικού σε 3D Πλέγμα")
    st.caption("Υπολογισμός αλληλεπιδράσεων σε Qutrits...")

# 💰 ΠΥΛΩΝΑΣ 3: ΟΙΚΟΝΟΜΙΑ (Resource Monetization)
with col3:
    st.header("💰 Οικονομία")
    profit = (temp * 0.5) + (progress_val * 10) # Εικονική φόρμουλα κέρδους
    st.metric(label="Daily Revenue (Q-Credits)", value=f"{profit:,.2f} QC", delta="+8.4%")
    st.write("Node Renting: **ACTIVE**")

st.divider()

# --- ΤΡΙΑΔΙΚΗ ΑΠΕΙΚΟΝΙΣΗ (0-1-2) ---
st.subheader("🌐 Live Ternary Grid Stream (Node 0-1-2)")
if st.button("SCAN QUANTUM LATTICE"):
    symbols = ["🔴", "🟢", "🔵"]
    with st.empty():
        for _ in range(3):
            grid_lines = []
            for _ in range(6):
                line = "".join([random.choice(symbols) for _ in range(25)])
                grid_lines.append(line)
            st.code("\n".join(grid_lines))
            time.sleep(0.3)
    st.success("Το πλέγμα σταθεροποιήθηκε από το AI.")

# --- ΙΣΤΟΡΙΚΟ ΔΕΔΟΜΕΝΩΝ ---
st.write("---")
st.subheader("📈 Απόδοση Δικτύου")
chart_data = pd.DataFrame(np.random.randn(20, 3), columns=['Node A', 'Node B', 'Node C'])
st.line_chart(chart_data)

# --- AI ACTIONS ---
if st.sidebar.button("RECALIBRATE ENTAGLEMENT"):
    with st.spinner("Επαναφορά εμπλοκής μέσω AI..."):
        time.sleep(2)
    st.sidebar.balloons()
    st.sidebar.success("Σταθεροποίηση Ολοκληρώθηκε!")
