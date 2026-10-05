from flask import Flask, jsonify
from datetime import datetime

app = Flask(__name__)

tarefas = []
agentes = []

@app.route("/")
def inicio():
    return jsonify({
        "sistema": "V17 1.000 Tarefas",
        "status": "ONLINE",
        "hora": datetime.now().isoformat(),
        "tarefas": len(tarefas),
        "agentes": len(agentes)
    })

@app.route("/status")
def status():
    return jsonify({
        "status": "ONLINE",
        "tarefas_total": len(tarefas),
        "agentes_ativos": len(agentes)
    })

@app.route("/tarefas")
def listar_tarefas():
    return jsonify(tarefas)

@app.route("/agentes")
def listar_agentes():
    return jsonify(agentes)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)