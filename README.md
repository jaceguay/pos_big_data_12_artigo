---

nome: Calibragem de um modelo de simulação de tráfego, utiliando dados de navegação móvel.
data: 2021-08-16
dados: waze

---

# Calibragem de um modelo de simulação de tráfego, utiliando dados de navegação móvel.

## Introdução

A partir de estimativas obtidas com dados da simulação, criar visualizações que não são possíveis apenas com os dados do feed em tempo real do Waze.

## Modelo de teste

**teste_sim**: Decal QGIS, coordenadas com offset de -700000 (evitar artefatos gráficos na viewport do netedit, coordendas muito distantes da origem)

![fundo_qgis_osm](imgs/testeQGIS_base.jpg)

**dados_waze**:

Considerações relativas a cores/velocidades, Here Maps:

- Green (fast): 85 - 100% of free flow speeds
- Yellow (moderate): 65 - 85%
- Orange (slow); 45 - 65%
- Red (stop and go): 0 - 45%