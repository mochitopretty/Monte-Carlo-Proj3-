Síntesis de población estelar one-zone con evolución química (closed box e infall) y comparación con la MDF de enanas G del vecindario solar (G-dwarf problem). Curso AST-305 Astrofísica Computacional II, USM.

## Diagrama de flujo
 
```mermaid
flowchart TD
    A[params.py: parámetros y semilla] --> B[Muestrear M_init desde la IMF de Kroupa<br/>transformación inversa por segmentos]
    A --> C[Muestrear t_birth ~ U 0, T_MW]
    B --> D[t_age = T_MW - t_birth<br/>t_MS = 10 Gyr M^-2.5]
    C --> D
    D --> E{t_age < t_MS?}
    E -- Sí --> F[Secuencia principal<br/>M_final = M_init]
    E -- No --> G{M_init}
    G -- "< 9 M☉" --> H[WD: IFMR de Miller+2026]
    G -- "9–15 M☉" --> I[NS: Raithel+2018]
    G -- "≥ 15 M☉" --> J{Rango mixto?}
    J -- Sí --> K[Sorteo u < P_NS → NS, si no → BH]
    J -- No --> L[BH: Raithel+2018, f_ej]
    C --> M{Modelo químico}
    M -- Closed box --> N[Z = y ln 1/μ t_birth]
    M -- Infall --> O[Integrar gas y metales<br/>Z t_birth por interpolación]
    F --> P[Enanas G: 0.8 < M < 1.05 y en MS]
    N --> P
    O --> P
    P --> Q[MDF con bins comunes + métricas<br/>comparación con observaciones]
```
