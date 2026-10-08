# Stop 'n' Print

Turns a district's indent workbook into everything a packing hall needs for a
public examination: paper labels, binding charts, bundle slips, check lists and
delivery lists.

Built for the DCEB offices of Telangana. One HTML file. Nothing is uploaded —
the workbook is read in the browser and never leaves the machine.

## Running it

Download `index.html` and open it. That is the whole installation.

It wants a connection the first time it is opened, to fetch the three libraries
it leans on (a spreadsheet reader, a PDF writer and a zipper). After that the
page is cached by the browser and works offline.

**Chrome or Edge** are the best fit — they can be pointed at a folder so every
PDF lands where you want it. Safari and Firefox work; on an iPhone each sheet
opens in its own tab, to be saved through Share.

## What it makes

| Step | Output |
|------|--------|
| 03 Primary labels / 04 High school labels | the label files, two columns to a sheet, ascending copy order |
| 05 Binding chart | one chart a class-pair and medium, with the copy counts |
| 06 Packet aura | how many codes of each medium every centre receives |
| 07 Bundles | a slip for every centre |
| 08 Double bundles | a centre split into parts, each slip ringed 1 of 2 |
| 09 Bulk bundles | the reserve a key centre holds back |
| 10 Check list | the centres in each mandal, with a box against each |
| 11 Delivery list | one sheet a mandal, signed for on receipt |
| 12 Codes | the chart the run is printed against |

**Download the whole run (.zip)** on the labels screen puts every one of them in
a single file, with the computed workbook beside them.

## The workbook it reads

One row a school. It finds its own way around a sheet — a medium banner across
the top, or none at all; `VI`, `6`, `6th`, `C6`, `Class 6 TM` as class labels;
`S.No` as the centre number. Column-numbering rows, blank rows and `GRAND TOTAL`
footers are skipped.

A workbook may carry a second sheet of bulk reserve alongside the strength: it
is recognised and set aside for the bulk slips without being mistaken for the
run.

If a column is read wrongly it can be set by hand on the Load screen.

## Working on it

There is no build step and no dependencies to install. Open `index.html` in an
editor, change it, reload the browser.

The file is laid out in this order:

1. styles
2. the opening page
3. the chart — classes, media, subjects and their codes
4. the reader — how a workbook becomes rows
5. the planner — how rows become label files
6. the sheets — labels, slips, charts, lists, each drawn twice over the same
   geometry: once to the screen as SVG, once to the PDF
7. the screens

The build stamp sits at the foot of the left rail. Raise it when you change
something, so one download can be told from another.

### Two things worth knowing before changing anything

**The preview and the PDF are drawn by the same code.** `svgSurface()` answers
to the same calls as the PDF writer, so a change to a sheet's geometry moves
both. If you add a drawing call to one, add it to the other or the two will
disagree.

**Copy counts climb.** Labels come out in ascending copy order within each file,
because that is how a counter works through a stack. Anything that reorders a
file has to preserve that.

## Licence

Written for the District Common Examination Boards. Use it.
