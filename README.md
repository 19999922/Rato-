# Rato-
Modelo do Rato da Caixa de Skinner 
import streamlit as st
import random

st.title("🐭 Rato na Caixa de Skinner 🧀")

st.image("https://i.imgur.com/sM0p94l.png", width=200)

if 'tentativas' not in st.session_state:
    st.session_state.tentativas = 0
if 'comidas' not in st.session_state:
    st.session_state.comidas = 0

def puxar_alavanca():
    st.session_state.tentativas += 1
    if random.random() < 0.5:
        st.session_state.comidas += 1
        st.success(f"O rato recebeu comida! 🧀 Total: {st.session_state.comidas}")
        st.image("https://i.imgur.com/RNMR8gJ.png", width=150)
    else:
        st.error("Sem comida dessa vez 🚫")
        st.image("https://i.imgur.com/2NqxtIj.png", width=150)

    if st.session_state.tentativas >= 10:
        st.info(f"Fim! O rato conseguiu {st.session_state.comidas}/10 comidas.")
        st.session_state.tentativas = 0
        st.session_state.comidas = 0

st.button("Puxar Alavanca", on_click=puxar_alavanca)

st.sidebar.markdown("""
## 📖 Sobre o jogo
Este jogo demonstra o **Condicionamento Operante** proposto por B.F. Skinner.

- **Reforço Positivo**: comportamento seguido de recompensa (comida).
- O rato aprende a associar a alavanca ao recebimento de comida.
""")
