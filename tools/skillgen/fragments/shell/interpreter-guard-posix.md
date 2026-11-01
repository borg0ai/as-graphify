```bash
if [ ! -f .graphify/.graphify_python ]; then
    GRAPHIFY_BIN=$(which graphify 2>/dev/null)
    if [ -n "$GRAPHIFY_BIN" ]; then
        PYTHON=$(head -1 "$GRAPHIFY_BIN" | tr -d '#!')
        case "$PYTHON" in *[!a-zA-Z0-9/_.@-]*) PYTHON="python3" ;; esac
    else
        PYTHON="python3"
    fi
    mkdir -p .graphify
    "$PYTHON" -c "import sys; open('.graphify/.graphify_python', 'w', encoding='utf-8').write(sys.executable)"
fi
```
