# Build Function Examples (Escher)

This file provides usage examples for the `build_*` functions in the ORPT notebook.

## Prerequisites

Run the setup and FBA cells first so these variables exist:

- `model`
- `df_fluxes`
- `df_shadow_prices`
- `solution_index`

---

## 1) Build around one reaction

```python
builder_orpt = build_reaction_escher_builder(
    reaction_name="ORPT",
    df_fluxes=df_fluxes,
    df_shadow_prices=df_shadow_prices,
    model=model,
    solution_index=solution_index,
    search_depth=1,
    expansion_mode="both",  # both | reactants_only | products_only
    nonzero_only=True,
    flux_threshold=1e-9,
    keep_seed_reaction=True,
    hide_secondary_metabolites=False,
    map_json_path="H:/ROBOT_SCIENTIST/E_coli/iML1515.ORPT_map.json",
    verbose=True,
)
builder_orpt
```

---

## 2) Build shortest path between two reactions

```python
builder_orpt_to_pyk = build_path_between_reactions_escher_builder(
    start_reaction_name="ORPT",
    end_reaction_name="PYK",
    df_fluxes=df_fluxes,
    df_shadow_prices=df_shadow_prices,
    model=model,
    solution_index=solution_index,
    nonzero_only=True,
    flux_threshold=1e-9,
    keep_endpoints=True,
    hide_secondary_metabolites=False,
    map_json_path="H:/ROBOT_SCIENTIST/E_coli/iML1515.ORPT_to_PYK.path.json",
    verbose=True,
)
builder_orpt_to_pyk
```

---

## 3) Build around one metabolite (or exchange)

You can pass either:
- a metabolite ID (example: `orot5p_c`)
- or a single-metabolite exchange/sink/demand reaction ID

```python
builder_orot5p = build_metabolite_escher_builder(
    metabolite_name="orot5p_c",
    df_fluxes=df_fluxes,
    df_shadow_prices=df_shadow_prices,
    model=model,
    solution_index=solution_index,
    search_depth=1,
    nonzero_only=True,
    flux_threshold=1e-9,
    keep_seed_metabolite=True,
    exclude_metabolites=["h_c", "h2o_c", "pi_c", "atp_c", "adp_c"],
    hide_secondary_metabolites=False,
    map_json_path="H:/ROBOT_SCIENTIST/E_coli/iML1515.orot5p_c.depth1.json",
    verbose=True,
)
builder_orot5p
```

---

## 4) Build shortest path between two metabolites (or exchanges)

You can pass metabolite IDs, exchange IDs, or a mix.

```python
builder_orot5p_to_pyr = build_path_between_metabolites_escher_builder(
    start_metabolite_name="orot5p_c",
    end_metabolite_name="pyr_c",
    df_fluxes=df_fluxes,
    df_shadow_prices=df_shadow_prices,
    model=model,
    solution_index=solution_index,
    nonzero_only=True,
    flux_threshold=1e-9,
    keep_endpoints=True,
    exclude_metabolites=["h_c", "h2o_c", "pi_c", "atp_c", "adp_c"],
    hide_secondary_metabolites=False,
    map_json_path="H:/ROBOT_SCIENTIST/E_coli/iML1515.orot5p_c_to_pyr_c.path.json",
    verbose=True,
)
builder_orot5p_to_pyr
```

---

## 5) Build around one gene

Provide either `gene_id` or `gene_name` (if both are provided, `gene_id` wins).

```python
builder_gene = build_gene_escher_builder(
    gene_id="b0150",
    # gene_name="pyrE",
    df_fluxes=df_fluxes,
    df_shadow_prices=df_shadow_prices,
    model=model,
    solution_index=solution_index,
    search_depth=1,
    expansion_mode="both",  # both | reactants_only | products_only
    nonzero_only=True,
    flux_threshold=1e-9,
    keep_seed_reactions=True,
    hide_secondary_metabolites=False,
    map_json_path="H:/ROBOT_SCIENTIST/E_coli/iML1515.gene.b0150.depth1.both.json",
    verbose=True,
)
builder_gene
```

---

## 6) Compare WT vs perturbed fluxes

Select one of these comparison modes:
- `wt_nonzero_pert_zero`
- `pert_nonzero_wt_zero`
- `diff_above`

```python
builder_cmp = build_flux_comparison_escher_builder(
    model=model,
    df_fluxes_wt=df_fluxes_wt,
    df_shadow_prices_wt=df_shadow_prices_wt,
    wt_index=0,
    df_fluxes_pert=df_fluxes_pert,
    df_shadow_prices_pert=df_shadow_prices_pert,
    pert_index=0,
    comparison_mode="diff_above",
    flux_threshold=1e-9,
    diff_threshold=1e-6,
    shadow_mode="diff",  # wt | pert | diff
    hide_secondary_metabolites=False,
    map_json_path="H:/ROBOT_SCIENTIST/E_coli/iML1515.compare.diff_above.json",
    verbose=True,
)
builder_cmp
```

---

## Common quick tweaks

- Show all metabolites: `hide_secondary_metabolites=False`
- Hide less relevant reactions: `nonzero_only=True` + tune `flux_threshold`
- Reduce shortcut paths: use `exclude_metabolites=[...]`
- Generate map file automatically: omit `map_json_path`
