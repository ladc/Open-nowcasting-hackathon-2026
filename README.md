# Open Nowcasting Hackathon 2026

Introductory notebooks on nowcasting, developed for the EUMETCAL training materials
hackathon held at KNMI in 2026.

The notebooks are based on training material by Ruben, Jenna, Mats and colleagues. This
version was created by Lars and colleagues during the hackathon.

## Contents

| Notebook | Description |
| --- | --- |
| [`Nowcasting.ipynb`](Nowcasting.ipynb) | Student notebook with deliberately incomplete code |
| [`Nowcasting_solutions.ipynb`](Nowcasting_solutions.ipynb) | Worked solutions and full design rationale |

## About the exercise

**Module 4: Introduction to Nowcasting — the incident review, or could the festival have
been warned?**

On the evening of 19 June 2021 an open-air music festival was running on the banks of the
Meuse at Namur, Belgium. A mesoscale convective system moved north out of France and put
more than 30 mm of rain per hour over the festival site. The exercise puts you on the
post-event review panel, which must decide whether a warning was possible, and from what
time.

Working with 5-minute radar-gauge merged rain rate data (RADCLIM, Belgian Lambert 2008
grid) and [pysteps](https://pysteps.github.io/), the six steps build up the evidence:

1. Obtain the data and select the frames — establishing the ceiling on any warning.
2. Estimate motion by eye.
3. Compute the optical flow three ways.
4. Compare two frames against three.
5. Run the deterministic nowcast and verify it.
6. Run the probabilistic (STEPS) nowcast and reach the final verdict.

Wherever you meet `...` in the student notebook, you supply the value. Almost every blank
asks for a forecasting decision rather than a piece of Python: a rain rate threshold, an
area, a number of radar frames, a probability at which you would act. The surrounding code
is already written. Check your work against `Nowcasting_solutions.ipynb`.

## Requirements

The notebooks install their own dependencies in the first cell:

```python
%pip install -q mlcast-datasets pysteps cartopy opencv-python-headless
```

`opencv` is required by the Lucas–Kanade optical flow inside pysteps; without it,
`motion.get_method("LK")` raises `MissingOptionalDependency`. The data are read lazily from
the MLCast datasets catalog, so an internet connection is needed for the first run.

## Running

```bash
git clone git@github.com:ladc/Open-nowcasting-hackathon-2026.git
cd Open-nowcasting-hackathon-2026
jupyter lab Nowcasting.ipynb
```

Run the cells from the top: the setup cell defines the event, the festival site and the
domain used by every later step.

## References

The full reference list is at the end of `Nowcasting.ipynb`. Key sources include
Pulkkinen et al. (2019) on the pysteps library, Bowler et al. (2006) on STEPS, Germann and
Zawadzki (2002, 2004) on the predictability of precipitation, and Hersbach (2000) on CRPS.
