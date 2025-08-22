# SD_LAB_1 — MergeSort Paralelo (Processos vs Threads)

## Requisitos

- Python 3.13
- Bibliotecas:
  - `numpy`
  - `pandas`
  - `matplotlib`

pip install numpy pandas matplotlib
O restante usa apenas biblioteca padrão.

 Como executar (modo manual)
O ponto de entrada é main.py. Principais argumentos aceitos:

--run  Executa o pipeline completo.

--backend process,thread

process

thread 

-k, --k <int>  Número de segmentos.

-n, --n <int>  Tamanho da lista quando gerada sinteticamente.

--input <arquivo.json>  Caminho para uma lista de inteiros em JSON.

--seed <int>  Semente para geração dos dados.

--tag <str>  Rótulo livre para identificar a execução (vai para CSV/JSON).

--print-result Imprime o vetor final ordenado.

--save <arquivo.json> Salva/atualiza também um arquivo JSON (lista de execuções).

Também é possível passar k e n como posicionais ao final:
python main.py --run --backend process 8 200000
python main.py --run --backend process --k 8 --n 200000
Comandos prontos para testar
1) Linha de base (sem paralelismo) — k=1

python main.py --run --backend process --k 1 --n 100000 --seed 42 --tag k1_baseline
2) Paralelismo moderado — k=4

python main.py --run --backend process --k 4 --n 100000 --seed 42 --tag k4_proc
3) Paralelismo alto — k=8

python main.py --run --backend process --k 8 --n 200000 --seed 123 --tag k8_proc
4) Comparação processos × threads (mesmos parâmetros)

python main.py --run --backend process --k 8 --n 200000 --seed 123 --tag p8_200k
python main.py --run --backend thread  --k 8 --n 200000 --seed 123 --tag t8_200k
5) Usando os dados do professor (JSON da raiz)

python main.py --run --backend process --k 5 --input dados_prof.json --print-result --tag prof_example
6) Salvando também em JSON (acumula execuções em lista)

python main.py --run --backend process --k 8 --n 200000 --seed 123 --tag big_8x200k --save results_big.json
Todas as execuções acrescentam uma linha em results.csv. 
