# R.José Siqueira x Av.Ver.Abrahão João Francisco

Adicionar rota, centro joão goulart e mesmo sentido peso velocidades trecho lombada

## Material base:

- captura google transit

![captura google maps](imgs/2021-08-27-183944_dimensoes.jpg)

27/08/2021 - 17:10

- verde: 70% a 100%
- laranja: 55% a 70%
- vermelho: 30% a 55%
- vermelho escuro: 0% a 30%

(70x8.5)/100 = 5.95

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
nome                                         | km/h | m/s | verde m/s    | laranja m/s   | vermelho m/s  | vermelho escuro m/s
---------------------------------------------|------|-----|--------------|---------------|---------------|--------------------
Av.Ver.Abrahão João Francisco                | 60   | 16  | 11.2 até 16  | 8.8 até 11.19 | 4.8 até 8.79  | 0 até 4.79
Av.Ver.Abrahão João Francisco (próx.lombada) | 30   | 8.5 | 5.95 até 8.5 | 4.67 até 5.94 | 2.55 até 4.66 | 0 até 2.54
R.Estud.Renato Victorino                     | 40   | 11  | 7.7 até 11   | 6.05 até 7.69 | 3.3 até 6.04  | 0 até 3.29
R.José Siqueira                              | 40   | 11  | 7.7 até 11   | 6.05 até 7.69 | 3.3 até 6.04  | 0 até 3.29
R.Pres.João Goulart                          | 40   | 11  | 7.7 até 11   | 6.05 até 7.69 | 3.3 até 6.04  | 0 até 3.29

### Gráfico

1. filtrar linhas
2.


## 2. Rotas

origen | destino | prioridade

## 3. Sensores

Induction Loops Detectors (E1): Simple detector that measure properties of vehicles as they passed through.

Lanearea Detectors (E2): Similar to a vehicle tracking cameras, tailored for measuring queues of standing/jammed vehicles and it keeps track of all vehicles which currently are on its area.