# Beam Designer

## Purpose
An educational single-page tool for plotting shear, moment, and deflection
for a simply supported steel beam and checking bending stress and
deflection against user-supplied criteria.

## MVP scope and assumptions
- Simply supported, prismatic steel W-shapes; section properties are
  entered by the user. No built-in shape database.
- Downward point loads and uniform loads; multiple loads are allowed.
- Linear-elastic Euler-Bernoulli beam analysis with small deflections and
  superposition. Shear deformation is ignored.
- No shear-strength check and no code-based design claims.
- Continuous beams, cantilevers, lumber, and buckling are deferred.

## Inputs and conventions
- US customary units: span and load positions in ft, forces in kip,
  uniform loads in kip/ft, E and allowable bending stress in ksi,
  Ix in in^4, and Sx in in^3.
- User supplies E, Ix, Sx, and allowable bending stress Fb.
- Load magnitudes are positive downward. Positions are measured from the
  left support. Reactions are upward; positive moment is sagging;
  positive deflection is downward. Positive shear is upward on the left
  face.
- Uniform loads have a start and end position within the span.

## Calculations and checks
- Reactions, shear, and moment from statics.
- Elastic deflection under the sum of all entered loads.
- Maximum bending stress fb = max(|M|) / Sx, compared with user-supplied
  Fb.
- Maximum absolute deflection compared with L/360, using the total
  entered load.
- Report units, reactions, maximum shear and moment, maximum deflection,
  bending stress, and pass/fail for bending and deflection.

## Look and feel
Clean and professional, with the example beam loaded when the page opens.
Show the beam and loads, plus shear, moment, and deflection diagrams.

## Validation
Use E = 29,000 ksi and Ix = 204 in^4 for the sample W12x26 analysis.
These are example analysis properties; users must verify their own
section properties and allowable stress. Use Sx = 33.4 in^3 and
Fb = 24 ksi only as illustrative values for demonstrating the bending
check, not as a code-prescribed design value.

| Case | Span and loads | Expected results |
|---|---|---|
| Full-span uniform load | 20 ft; 1 kip/ft from 0 to 20 ft | Reactions 10 kip each; max shear 10 kip; max moment 50 kip-ft; max deflection about 0.609 in |
| Center point load | 20 ft; 10 kip at 10 ft | Reactions 5 kip each; max shear 5 kip; max moment 25 kip-ft; max deflection about 0.487 in |
| Partial uniform load | 20 ft; 1 kip/ft from 5 to 15 ft | Reactions 5 kip each; max shear 5 kip; max moment 37.5 kip-ft |

For each case, compare reactions and diagram extrema with hand
calculations. The example full-span load has an L/360 limit of 0.667 in.

## Intended use
For preliminary or educational use only; not a substitute for
code-compliant design or professional review.
