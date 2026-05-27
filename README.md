# PytoolsSolyd

Ferramentas básicas de segurança ofensiva em Python com foco em port scanning.

## Conteúdo

- `portscanner/portscan.py`: scanner TCP multi-threaded para os 1.000 ou 10.000 ports mais comuns.

## Requisitos

- Python 3.x
- `pythonping` opcional para auto-ajuste de timeout no `portscanner`.

Instalação mínima:

```bash
python3 -m pip install dnspython pythonping
```

## `portscanner/portscan.py`

Scanner TCP baseado em `socket.connect_ex`.

Parâmetros principais:

- `-t`, `--target`: alvo (IP ou hostname)
- `--timeout`: timeout em milissegundos
- `--threads`: número de threads de varredura
- `--output`: arquivo de saída para portas abertas
- `--top-1k`: usa a lista dos 1.000 ports mais comuns
- `--top-10k`: usa a lista dos 10.000 ports mais comuns

Uso:

```bash
python3 portscanner/portscan.py -t example.com --threads 50 --top-1k --output open_ports.txt
```

Com `pythonping` instalado, o scanner tenta calcular um timeout baseado na latência ICMP. Sem `pythonping`, usa um timeout padrão de 2000 ms.


## Observações

- `portscan.py` realiza apenas varredura TCP padrão (`connect_ex`).
- Erros de resolução de domínio geram falha controlada e encerra o scan.

## Estrutura do projeto

```text
│   └── portscan.py
```
