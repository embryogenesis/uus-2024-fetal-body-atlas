# Uus et al. 2024 — population-averaged 3D T2w fetal body MRI atlas

A **verbatim mirror** of [`10.1038/s41598-024-57087-x`](https://doi.org/10.1038/s41598-024-57087-x), redistributed under the terms of the licence the depositors chose. No file has been modified.

## Attribution

> Uus, Alena; Hall, Megan; Grigorescu, Irina; Avena Zampieri, Carla; Egloff Collado, Alexia; Payette, Kelly; Matthew, Jacqueline; Kyriakopoulou, Vanessa; Hajnal, Joseph V.; Hutter, Jana; Rutherford, Mary A.; Deprez, Maria; Story, Lisa — Centre for the Developing Brain and School of Biomedical Engineering and Imaging Sciences, King's College London. Requested credit: 'SVRTK fetal MRI atlas repository, https://gin.g-node.org/kcl_cdb/fetal_body_mri_atlas'.
>
> Uus A, Hall M, Grigorescu I, et al. Automated body organ segmentation, volumetry and population-averaged atlas for 3D motion-corrected T2-weighted fetal body MRI. Scientific Reports 14, 6637 (2024), doi:10.1038/s41598-024-57087-x.
>
> DOI: [10.1038/s41598-024-57087-x](https://doi.org/10.1038/s41598-024-57087-x) — licensed **CC0 1.0**

Dedicated to the public domain under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/); see [`LICENSE`](LICENSE). You may copy, modify and distribute this material, including commercially, without asking permission and without attribution — though citing the depositors is the decent thing and this README does. **This mirror makes no changes.**

## What this is

A population-averaged 3D T2w template of the fetal body, built at King's College London from DSVR motion-corrected reconstructions of 17 normal fetuses at 3T with TE 180 ms. Four files: the atlas volume, a label volume of ten organ ROIs, a second label volume of a multi-regional lung parcellation, and the ITK-SNAP colourmap for the organ labels. The most permissively licensed deposit this project holds, and as permissive as it will ever find — CC0 waives copyright rather than granting under conditions, so nothing in this mirror constrains onward use.

## Contents

4 file(s), 0.0 MB total.

| File | Size | SHA-256 |
| --- | --- | --- |
| `data/reo-fetal-t2w-body-atlas.nii.gz` | 0.0 MB | `75e234afd07b8dc8…` |
| `data/reo-fetal-t2w-body-atlas-mask-body_organs-10.nii.gz` | 0.0 MB | `4b7bade32fac95a8…` |
| `data/reo-fetal-t2w-body-atlas-mask-lungs_multi-10.nii.gz` | 0.0 MB | `5d81b6f91bcc2a6d…` |
| `data/ITK-SNAP-colourmap-body-organs-10.txt` | 0.0 MB | `259bdb67442cc9d9…` |

Full checksums, original filenames and the source article id for every file are in [`MANIFEST.json`](MANIFEST.json).

## Notes for anyone using this

- IMPORTANT: there is no heart and no body outline. The ten ROIs, read verbatim from the deposit's own `ITK-SNAP-colourmap-body-organs-10.txt`, are 1 lungs, 2 liver, 3 stomach, 4 spleen, 5 kidney pelvis, 6 kidney parenchyma, 7 bladder, 8 thymus, 9 gallbladder, 10 adrenal glands. That is thoracic and abdominal organ volumetry, and neither of the two surfaces docs/ROADMAP.md item 4 wants at every age is among them.
- It is one averaged template, not a weekly series. There is a single atlas volume and no per-gestational-age timepoints, so it supplies a shape and not a trajectory — and the repository states no gestational age or age range for the seventeen fetuses behind it, so the template's own position on a developmental timeline is not given.
- Two different tens, which are not the same ten. `…mask-body_organs-10` carries the ten organ ROIs above. `…mask-lungs_multi-10` is the separate lung-lobe parcellation protocol (Uus et al., PIPPI MICCAI Workshop 2024), and the deposit ships no colourmap for its labels: `structural_3t_t2w/` holds exactly these four files and the only colourmap among them is the organ one.
- A population average, not a specimen. It files at the warrant the CRP phantoms get rather than the one a Carnegie specimen gets: a real object that is nobody's body.
- No checksums are published and GIN answers HEAD without a Content-Length, so the pre-download report shows size 0 and md5 stays blank; SHA-256 is computed locally from the downloaded bytes. Sizes read from a full GET are 10,164,394 bytes for the atlas, 206,885 for the organ mask and 59,162 for the lung mask — all far below GitHub's per-file limit.
- The three volumes are real gzip (`1f 8b 08` at offset 0, checked), not git-annex pointer files, which a GIN repository can also serve. Read them with tools/nifti.ts, which has a `gunzip()`.
- The baseUrl pins the `master` branch rather than a commit, so an upstream force-push changes what this mirror fetches. The checksums in MANIFEST.json are what makes that detectable.
- CC0 requires no attribution at all. The depositors ask for credit anyway, naming the repository URL, and the mirror gives it — that is courtesy here, not a licence condition, and an onward user is under no obligation.

## Verifying the mirror

```sh
# every file, against the manifest
python3 -c "import json,hashlib,pathlib;m=json.load(open('MANIFEST.json'));[print(('ok  ' if hashlib.sha256(pathlib.Path(f['path']).read_bytes()).hexdigest()==f['sha256'] else 'BAD ')+f['path']) for f in m['files'] if pathlib.Path(f['path']).exists()]"
```

---

Mirrored 2026-11-23 by `tools/mirror.ts` from [embryogenesis](https://github.com/embryogenesis/embryogenesis). The licence was checked against https://gin.g-node.org/kcl_cdb/fetal_body_mri_atlas/raw/master/README.md before download.
