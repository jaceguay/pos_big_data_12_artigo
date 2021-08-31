# R.José Siqueira x Av.Ver.Abrahão João Francisco

## Material base:

- captura google transit

![captura google maps](imgs/2021-08-27-183944_dimensoes.jpg)

27/08/2021 - 17:10

Base georreferenciada SIRGAS 2000/UTM zone 22S

coordenadas: 730656 x 7019845

## Objetivos

Obtenção da demanda: fluxo de veículos

## Etapas

1. Malha
2. Rotas (código trecho)
3. Sensores
4. Simulação

## 1. Malha

velocidade máxima:
nome | km/h | m/s
--- | --- | ---
Av.Ver.Abrahão João Francisco (próx.lombada) | 30 | 8.5
Av.Ver.Abrahão João Francisco | 60 | 16
R.José Siqueira | 40 | 11
R.Estud.Renato Victorino | 40 | 11
R.Pres.João Goulart | 40 | 11

## 2. Rotas

origen | destino | prioridade

## 3. Sensores

Induction Loops Detectors (E1): Simple detector that measure properties of vehicles as they passed through.

Lanearea Detectors (E2): Similar to a vehicle tracking cameras, tailored for measuring queues of standing/jammed vehicles and it keeps track of all vehicles which currently are on its area.