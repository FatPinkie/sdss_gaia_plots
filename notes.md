# Notes

## Research

## Queries

#### Gaia sources, SDSS cross-match and photometrics
```
SELECT gs.source_id, sdss.clean_sdssdr13_oid, sdss.original_ext_source_id, sdss.angular_distance, gs.ra, gs.dec, gs.phot_g_mean_mag, gs.bp_g, gs.g_rp
FROM gaiadr3.xp_summary xp
JOIN gaiadr3.sdssdr13_best_neighbour sdss ON sdss.source_id = xp.source_id
JOIN gaiadr3.gaia_source gs ON gs.source_id = xp.source_id
WHERE xp.bp_n_contaminated_transits = 0 AND xp.rp_n_contaminated_transits = 0
AND gs.phot_g_mean_mag < 20.5
AND gs.ra > 60 AND gs.ra < 300 AND dec > -1.67 AND dec < 1.67
```
- the last line is a ra/dec filter for Stripe 82