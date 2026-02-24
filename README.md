# Mess-Muncher
Digital clutter eater
import streamlit as st
import random
import time

st.set_page_config(page_title="Mess Muncher", page_icon="🗑️", layout="wide")

# Fake scan for demo (we'll make it real later)
def fake_scan():
    time.sleep(1.5)  # pretend it's thinking
    return {
        "emails": random.randint(80, 300),
        "tabs": random.randint(12, 87),
        "files": random.randint(45, 200),
        "subs": random.randint(2, 9),
        "savings": round(random.uniform(20, 150), 2)
    }

st.title("Mess Muncher 🗑️🍴")
st.markdown("Your personal digital trash panda. Let me eat your junk—fast, no mercy.")

# Sidebar for fun tweaks
with st.sidebar:
    st.header("Options")
    speed = st.slider("How aggressive?", 1, 5, 3, help="1 = gentle, 5 = nuclear")
    keep_memories = st.checkbox("Save cute pics & memes", value=True)
    st.markdown("---")
    st.caption("Pro tip: connect Gmail later for real magic.")

# The big button
if st.button("Declutter Me!", type="primary", use_container_width=True):
    with st.spinner("Sniffing around..."):
        time.sleep(2)
        results = fake_scan()

    st.success("Done! I just munched:")
    col1, col2, col3 = st.columns(3)
    col1.metric("Emails archived", results , delta="—all spam")
    col2.metric("Tabs closed", results , delta="—your brain thanks me")
    col3.metric("Subscriptions canceled", results , delta=f"${results } saved")

    if keep_memories:
        st.balloons()
        st.markdown("Kept your cat pics. You're welcome.")

    st.markdown("**Want more?** Upgrade to pro—unlimited scans, mood-based delete. Coming soon.")

st.markdown("---")
st.caption("Mess Muncher v0.1 • Built by you & Leo • No data stored—just vibes.")
