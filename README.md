# **Análisis de Datos de Críquet utilizando PySpark**

## **Descripción del Proyecto**
Este proyecto utiliza **PySpark** para realizar un análisis exhaustivo de datos de críquet. A través de un enfoque basado en consultas SQL, funciones de ventana y visualización de datos, exploramos múltiples aspectos como rendimiento de jugadores, impacto del sorteo en los resultados y eficiencia de los lanzadores en overs de **powerplay**.

Además, el proyecto emplea **Matplotlib** y **Seaborn** para visualizar tendencias, distribuciones y patrones en los datos. 

## **Objetivo**
El objetivo principal de este proyecto es analizar datos históricos de partidos de críquet para proporcionar insights valiosos, como:
- Desempeño de bateadores y lanzadores.
- Impacto del sorteo en los resultados de los partidos.
- Análisis por sedes, temporadas y rendimiento en overs específicos.

---

## **Estructura del Proyecto**
### 1. **Esquemas de Datos**
- **Team.csv**: Información sobre los equipos.  
- **Player.csv**: Detalles de los jugadores.  
- **Player_match.csv**: Rendimiento individual de los jugadores en cada partido.  
- **Match.csv**: Información de partidos con resultados y estadísticas relevantes.  
- **Ball_by_ball.csv**: Datos a nivel de bola para cada partido.

### 2. **Análisis y Transformaciones Realizadas**
#### **1. Preprocesamiento de Datos**
- Filtrado de datos para excluir anchos y no bolas.
- Normalización de nombres de jugadores y manejo de valores nulos.
- Cálculo de categorías basadas en márgenes de victoria y estatus de jugadores.

#### **2. Análisis Avanzado con SQL y PySpark**
- **Análisis de Bateadores por Temporada**: Ranking de los mejores anotadores por temporada.  
- **Eficiencia de los Lanzadores en Powerplay**: Identificación de los lanzadores más económicos.  
- **Impacto del Sorteo**: Evaluación de cómo afecta ganar el sorteo al resultado del partido.  
- **Análisis de Carreras por Sede**: Comparación de puntajes promedio en cada estadio.  
- **Tipos de Despidos**: Análisis de los tipos más comunes de outs.

#### **3. Visualización de Resultados**
- **Matplotlib y Seaborn** para crear gráficos de:
  - Lanzadores más eficientes en **powerplay**.
  - Rendimiento de equipos al ganar el sorteo.
  - Tipos de despidos más frecuentes.
  - Promedio de carreras anotadas por los mejores bateadores en partidos ganados.

---

## **Código Destacado**
### **Consulta SQL - Mejor Bateador por Temporada**
"""sql
SELECT 
    p.player_name,
    m.season_year,
    SUM(b.runs_scored) AS total_runs 
FROM ball_by_ball b
JOIN match m ON b.match_id = m.match_id   
JOIN player_match pm ON m.match_id = pm.match_id AND b.striker = pm.player_id     
JOIN player p ON p.player_id = pm.player_id
GROUP BY p.player_name, m.season_year
ORDER BY m.season_year, total_runs DESC;
"""

# IPL_DA_Apache-Spark_Project
