# ELTON VOICE

Estúdio de voz IA 100% local e grátis. Gera narração em português e clona qualquer voz com 10 segundos de áudio.

Motor: [Chatterbox Multilingual](https://github.com/resemble-ai/chatterbox) da Resemble AI, licença MIT, 23 idiomas. Roda na GPU do Apple Silicon (MPS) com fallback pra CPU.

## Instalação

- **Windows**: dois cliques em `INSTALAR.bat` (detecta placa NVIDIA sozinho). Depois abra com `INICIAR.bat`
- **Mac**: dois cliques em `INSTALAR.command`. Depois abra com `INICIAR.command`

Mínimo: 8 GB de RAM, 6 GB de disco livre. Internet só no primeiro uso (baixa o modelo de 3 GB), depois roda 100% offline.

## Como usar

Abra com `INICIAR.bat` (Windows) ou `INICIAR.command` (Mac). O navegador abre sozinho em `http://127.0.0.1:8765`.

1. **Voz**: use a padrão, envie um áudio, ou grave 10 a 20 segundos no microfone
2. **Roteiro**: cole o texto e ajuste emoção e fidelidade
3. **Gerar**: o áudio toca na hora e fica salvo em `saidas/` como mp3

## Instalação (só na primeira vez)

```bash
python3.12 -m venv .venv
.venv/bin/pip install chatterbox-tts fastapi "uvicorn[standard]" python-multipart "setuptools<81"
```

O pin `setuptools<81` é obrigatório: o watermarker Perth do Chatterbox ainda usa `pkg_resources`, removido nas versões novas do setuptools.

Requisitos: Python 3.12, ffmpeg, ~4 GB livres (modelo baixa sozinho no primeiro uso).

## Estrutura

- `app.py`: servidor FastAPI + motor TTS
- `static/index.html`: interface
- `vozes/`: biblioteca de vozes de referência (wav 24 kHz mono)
- `saidas/`: áudios gerados
- `teste_motor.py`: teste de fumaça do motor
