# Changelog

What has changed in Synphonos, newest version first. Each entry says what changed for
someone using the program, and ends with the date it was made.

## 1.1.0 (2026-10-12)

Everything built on top of 1.0.0 since 2026-09-29.

### In short

- **Program mode:** a second mode for placing the marks a lighting console
  fires as cues, in sequences, with a cue table, copy and paste, BPM paste and
  undo.
- **Tempo:** set, tap or detect a song's BPM, see the beat grid, and snap to it.
- **A tidier window:** settings behind a cog, a zoom bar, stems that size one
  by one, and a Files window for the show and the settings.
- **Cue times:** fade, out fade, delays, cue mode (including Release), a
  command and info for each cue, and an Off time for each sequence, typed in
  the cue table or a right-click menu, drawn as dashed lines over the
  sequences, and exported to both consoles.
- **A new look:** a clearer typeface, outlines and thin rules in place of
  filled boxes, a waveform drawn as glowing grains, and the stems running to
  the window's edges.
- **It remembers:** the window's size and place, and whether you were in Show
  or Program.
- **Export to grandMA2 and grandMA3:** Program mode writes a song's marks
  out as a macro and the timecode it imports, for either console. A few
  commands on the console bring them in. On grandMA2 the import works on
  onPC; on grandMA3 everything was tried on onPC 2.4.2 and 2.5.1. Neither has
  been tried on a real console yet (see Known issues).
- **Safer with files from someone else:** a show file can no longer point
  the program at another computer, or put commands on the console that
  nobody at the desk has read, and a damaged audio file can no longer stop
  playback or take the computer's memory.

### Added

#### Program mode

- **Show | Program switch** beside the file line. Show mode runs the show, as
  before. Program mode keeps the readout, the stems and the transport, and
  turns the lower part of the window into sequences, a cue table and editing
  buttons. (2026-09-29)
- **Sequences.** Each one stands for a sequence on the console: the main cue
  list, a strobe button, a confetti button. A sequence has a name, a colour, a
  function (Goto, Go+, Go-, Top, Pause, Temp, Flash, Swop, Toggle, On, Off),
  an executor number on the song's page, a default hold (Temp, Flash and
  Swop) and a stem to draw behind it. Sequences belong to the show, so every
  song has the same ones. A new show starts with *Main cue* (Goto, executor
  1); later ones are *Sequence 2* and so on, as Temp from executor 101 with a
  0.5 s hold. A show holds up to 32 and always keeps at least one. Deleting
  one that has marks asks where they go. (2026-09-29; called sequences in the
  window, not lanes, since 2026-10-03)
- **The Sequences tab** under the transport (Cues | Sequences) edits them in
  rows: colour, name, function, executor, hold, stem, how many marks, delete,
  and *+ Add sequence*. (2026-09-30)
- **Sequence rows under the stems,** in a framed box of their own headed
  SEQUENCES, with a *+ Sequence* button. Click a row to select it: new marks
  go into the selected sequence. The selected row opens to a stem's height
  and is outlined in the accent colour. (2026-09-29; boxed apart from the
  audio 2026-09-30)
- **Every sequence has its stem's waveform dimmed behind its marks,** not only
  the selected one. A small diamond by each stem's name picks the stem behind
  the selected sequence. (2026-09-29; every sequence since 2026-10-04)
- **Sequence rows size one by one:** Alt+scroll over a row, or drag the line
  under it. Past the room they have, they scroll. (2026-09-30)
- **Marks in sequences.** A press is a diamond on the centre line of its row.
  A Temp, Flash or Swop mark also has a hold bar with a handle at the release.
  - Add with M at the playhead, or by double-clicking in a sequence.
  - Click to select; drag a box to select several; Shift and Ctrl extend.
  - Drag a mark to move it, with every other selected mark; drag a release
    handle to change the hold, of every selected mark when the mark is one
    of them (each release moves by as much, never before its press).
  - Clicking empty space in a sequence selects it and moves the playhead
    there.
  - Marks land on timecode frames. Hold Alt to land on whole seconds.

  (2026-09-29; click moves the playhead 2026-09-30; diamonds on the centre
  line and a much fainter line through each mark 2026-10-04; release handles
  of all the selected marks at once 2026-10-09)
- **Cue numbers.** In a Goto sequence every mark is a cue with a number. A
  new one takes the next whole number; one placed between two cues takes a
  number between them (2.5, then 2.25). Numbers never change by themselves
  and can be typed over. Numbering is per song and per sequence, up to
  9999.999. (2026-09-29)
- **Going back to an earlier cue.** Type a cue number the sequence already
  has (3 on the second Pre) and that mark fires the same cue again, instead
  of being a new cue: a second verse can go back to the verse cue. The mark
  takes the cue's name. In the cue table its number has a small return arrow
  after it, and hovering the number says which mark fires the cue first. On
  export the cue is stored once, labelled with the name of its first mark,
  and every mark that uses it fires it. A new mark added beside a repeated
  cue takes the next whole number, so it never lands among the first pass's
  cues. (2026-10-09)
- **The cue table** (the Cues tab) lists the song's marks in time order: cue,
  name, sequence, time and hold. The selected row can be edited in place.
  With several marks selected, a change made there (or in the right-click
  menu, or Large's selected panel) changes every one of them: the name, the
  sequence, the hold, and the time, which moves them all by as much (or none
  of them, if one would leave the song). A cue number changes only its own
  mark. Shift-click selects a range,
  Ctrl-click toggles, double-click goes to the mark. In a narrow window the
  sequence, time and hold columns fold away. (2026-09-29; several at once
  2026-10-09)
- **Times count from the song's start,** as `M:SS:FF`: in a song starting at
  04:00:00:00, a cue at 04:00:14:00 reads `0:14:00`. Typing a time moves the
  mark exactly; a full `HH:MM:SS:FF` is taken as the timecode itself. A time
  typed with units (`1m30s`, `14s5f`) is from the song's start too, unless it
  has hours (`4h0m14s`). (2026-09-30; units 2026-10-09)
- **Right-click a mark** (in a sequence, on a Track view flag or in the
  table) for its name, sequence, cue number, time and hold, with *Go to*,
  *Copy* and *Delete*. (2026-09-30)
- **Copy and paste** (buttons, or Ctrl+C, Ctrl+X, Ctrl+V). The first copied
  mark lands at the playhead in the selected sequence; the rest keep their
  distance from it in time and in sequences. It works from one song to
  another. Pasted cues get fresh numbers. Outlined diamonds show where a
  paste will land before it is made. A paste that would fall off the top or
  bottom sequence, or past the end of the song, is refused and says why.
  (2026-09-29)
- **BPM paste** repeats the copied marks at a tempo: every ¼ beat, ½ beat,
  beat, 2 beats, bar, 2 bars or 4 bars, starting at the playhead or the
  selected mark, for a number of beats, bars or seconds, or up to a chosen
  mark. Each copy is placed from the start, never from the copy before, so
  bar 64 is as exact as bar 1. Copies that would land exactly on a mark
  already there are skipped. It previews before pasting, pastes up to 4000
  copies, and is one undo step. (2026-09-29)
- **Undo and redo** (Ctrl+Z; Ctrl+Y or Ctrl+Shift+Z): 200 steps covering
  marks and sequences, one step per gesture. Typing into one field is one
  step. Show mode's mark edits are covered too. The history is cleared when
  the song changes or the set list is reshaped. Mark keys and the tempo are
  not part of undo. (2026-09-29)
- **Editing keys in Program mode:** Delete removes the selection, Ctrl+← and
  Ctrl+→ nudge it by a frame, Ctrl+Shift+← and Ctrl+Shift+→ by a second, and
  Ctrl+A selects every mark in the selected sequence. They work when no text
  field has focus, and give way to any key assigned in Keys. (2026-09-29)
- **Sequences | Track view.** Track hides the sequence rows and draws the
  marks as flags over the stems, in their sequence's colour, labelled with
  cue number and name. New marks go into the sequence named in *into*.
  (2026-09-30)
- **Snap: Frames | Beats.** On Beats, drags and double-clicks land on the
  nearest beat of the song's tempo. (2026-09-30)
- **Seeing cues fire.** While playing, a mark the playhead passes flashes its
  row in the cue table and the table follows it down; the row the playhead is
  at has a bar at its left. In the Sequences tab the sequence's row flashes
  too, and stays lit while a Temp or Flash is held. Jumping fires nothing.
  (2026-09-30)
- **Three layouts by window width:** Small (under 600 points) puts the
  transport on one row with a ⋯ menu, Medium is the reference, and Large
  (from 1100 points) puts the stems and sequences on the left and the table
  on the right. (2026-09-29)
- **The song's *Starts at* and *Rate*** are in Program mode as well, on the
  row with the Cues | Sequences switch (in the ⋯ menu at Small). (2026-09-30)
- **Pin the selected mark** (Settings, General) shows the selected mark's
  details in a line (Small) or a panel (Large). Off by default. (2026-09-30)
- **The lock in Program mode:** locked, it can be looked at and marks can be
  selected, but nothing can be changed or undone. (2026-09-29)

#### Export to grandMA2

- **Export to MA2…** in Program mode writes the loaded song's marks out for
  a grandMA2 (3.9.60 or later) as two files: a macro, and the timecode it
  imports. Nothing reaches the console until you run the macro there, with
  the three commands the window shows afterwards: delete the macro at that
  number, import the new one, run it. The macro:
  - stores each new cue of a Goto sequence, empty, for you to fill;
  - labels the cues with their marks' names, and each sequence by the
    *Names* pattern (its own name first: *Main cue - Baptised*);
  - puts a sequence on its executor where that is ticked, and sets the
    executor's button to the sequence's function, so a Temp sequence sits on
    a Temp button;
  - deletes the timecode in that pool, imports the new one, names it, and
    gives it its *Info*;
  - gives everything its colour, when *Colours* says to;
  - deletes itself as its last line, unless you keep it.

  The timecode starts at its *Offset* (the song's start, 07:10:00:00 say),
  runs for its *Length*, and has a track for each sequence, aimed at its
  executor, with an event at every mark, counted from the offset. Temp,
  Flash and Swop marks are a press and, a hold later, a release. Exporting
  only writes files, so it works while the show is locked and while it
  plays. (2026-10-06; deleting before importing 2026-10-07; offset, button
  functions, names, colours, info and deleting itself 2026-10-09)
- **The Export window folds into parts:** *Destination*, *Timecode*, *Page*,
  *Sequences*, *Macro*, *Names* and *Colours*. Each is one line saying what
  it is set to, and opens to its settings with a click; the window opens with
  all of them folded, remembers which you opened for as long as Synphonos
  runs, and scrolls when they do not fit. What the export comes to, anything
  stopping it, and *Export* stay in sight underneath. A part with a problem
  shows it on its line in the warning colour. (2026-10-09)
- **Timecode Options** (the gear beside *Timecode*) has everything
  grandMA2's own Timecode Options window has, laid out the same way: *Name*,
  *Slot*, *Length*, *Offset*, *Runs* (Endless Repeat, No Repeat or a number),
  *Switch Off* (Playbacks Off, Keep Playbacks), *Status Call*, *Time Unit*
  (the show's rate, 24, 25 or 30 FPS, 1/100 Seconds), *When Ending* (Stop,
  Pause), *When Stopping* (Do Nothing, Rewind), *AutoStart*, *User Bits* and
  *Info*. *Save to Default* makes them the options of every song not given
  its own, and *Load from Default* brings them back, as on the console; the
  name stays the song's. *Record Mode* is shown but greyed: its place in the
  file is not known, so set it on the console. (2026-10-09)
- **The timecode's slot** can be any of the console's TC slots, *Link
  Selected* or *Intern*. (2026-10-09)
- **Names** sets what things are called on the console, for the whole show:
  a pattern each for the sequences (`{sequence} - {song}` at first, so the
  sequence's own name comes first), the timecode (`{song}`) and the macro
  (`Synphonos {song}`). `{sequence}`, `{song}`, `{show}`, `{number}`,
  `{page}`, `{exec}` and `{function}` are filled in, and each row shows what
  it comes to for the loaded song. *Defaults* puts them back. (2026-10-09)
- **Colours** gives the sequences, the timecode and the macro a colour on the
  console: *Leave* them as they are, *One for all*, or *Each its own*, where
  the sequences can also take each one's own colour from Synphonos. A macro
  that deletes itself keeps no colour. (2026-10-09)
- **The macro deletes itself when it has run,** so the macro pool keeps only
  what you made. Untick *Delete the macro when it has run* (under *Macro*) to
  keep it. (2026-10-09)
- **The numbers are set per song, and kept.** The window has the timecode's
  pool number, *Offset*, *Length* and slot, the executor page, the macro
  number, and for every sequence its number in the console's pool and its
  executor on the page. They are filled in from the song: pool and page from
  its place in the set list, offset and length from the song's start and
  length, sequence numbers from the page (401, 402… on page 4), executors
  from the Sequences tab. Change any of them and it is kept with the song at
  once, exported or not, so a song can be set up ahead. The offset, the
  length and the executors go on following the song and the Sequences tab
  until you give them values of their own. (2026-10-06; executors
  2026-10-07; *Offset* and *Length*, the console's words, 2026-10-09)
- **Name the files.** *Files* sets what a song's two files are called:
  type `baptised` and they are `baptised_macro.xml` and `baptised_tc.xml`,
  and the import commands name them so. Letters, digits, `-` and `_` are
  kept, anything else becomes `_`, and a `.xml` typed on the end is taken
  off. Left empty, the name is made from the show and the song as before
  (`syn_baptised_s01`). It is kept with the song, and two songs cannot share
  a name, since each would replace the other's files. (2026-10-08)
- **Free sequence numbers from one number.** *Numbers from* is where the
  show's sequences start in the console's pool: type 500 and this song's
  sequences take the next numbers no other song of the show holds, in order
  down the list. It is kept for the whole show, so a song set up later starts
  at 500 too and goes round the numbers already given out. *Renumber* gives
  the song its free numbers again. Any one can still be given a number of its
  own on its line. Synphonos only knows the numbers its own songs hold, not
  sequences made on the console by hand. (2026-10-07)
- **Places on the page.** *Places* lists, for the whole show, where on a
  song's page sequences may go: *Faders* for cue lists (Goto sequences), and
  *Buttons* for the rest, typed as `6-10` or `107 108 111`. Down the list,
  each sequence with marks in the song takes the next place of its kind, so
  the fixed controls on the rest of the page are never touched. A sequence
  past the last place is shown as *none* and refused until there is room.
  Left empty, a kind stays on the executors the Sequences tab gives it.
  (2026-10-07)
- **A place on the page for each sequence.** *Exec* on a sequence's line is
  its executor on this song's page. It starts where *Places* (or the
  Sequences tab) puts it; changed here, it is this song's alone, and stays
  when *Places* change. (2026-10-07)
- **Create sequences** ticks *assign* on every sequence being exported at
  once: each is made in the console's pool and put on its executor. A dash
  shows when only some are ticked. (2026-10-07)
- **Tick what goes.** The window lists the sequences, folded, so all their
  numbers are in sight without scrolling. Each line has a tick for the whole
  sequence (a dash when only some of its marks are ticked), how many of its
  marks are ticked, its *Seq* and *Exec* numbers, and *assign*. Click the
  triangle or the name to open a sequence to its marks, each with a tick, its
  cue number, its name and the timecode the console fires it at. *All* and
  *None* tick the lot. A sequence with nothing ticked is left out.
  (2026-10-06; folding and the whole-sequence tick 2026-10-07)
- ***assign*** puts the sequence on its executor when the macro runs. It is
  ticked until an export has done it, and again if you change the sequence
  number, the executor or the page. Untick it when that executor already
  holds the sequence you want fired: a tick you turn off stays off.
  (2026-10-06; kept 2026-10-07)
- **Exporting again keeps your looks.** Synphonos remembers which cues it has
  stored in each sequence. The next export stores only the new ones and
  relabels the rest; every time is updated; a deleted or unticked mark loses
  its event and its cue is left alone. When there is something to store, the
  macro starts with *ClearAll* so the new cues are stored empty: the window
  says so, and a tick turns it off. When there is nothing to store, the
  programmer is not touched. (2026-10-06)
- **Where the files go:** straight into grandMA2 onPC on this PC (every
  installed version is found, newest first), onto a USB drive laid out for a
  console, or into a folder to copy over by hand. The last one used is
  offered first. Afterwards the *Exported* window names the two files and
  the commands to type, with *Copy commands* and *Open folder*. *Copy
  commands* copies them as one line, parted by `;`, so one paste and one
  Enter run them all. From a USB drive the macro goes back to the console's
  own disk when it is done, so the next save of the show does not land on
  the stick. (2026-10-06; one line 2026-10-07)
- **Names on the console** are the marks' and the *Names* patterns', with
  the characters a macro would trip over taken out: quotation
  marks, `$`, `;` and round brackets, which in a macro ask the operator to
  type something. A song called *Tag (Demo)* is labelled *Tag Demo*.
  (2026-10-06)
- **What it refuses, and says why:** a show at 29.97 DF (the console has no
  drop-frame timecode), a Goto mark with no cue number, two sequences given
  the same number or the same executor, a sequence with no place left,
  places that do not read as executors, a timecode that would run past 24
  hours, and a song whose audio is not loaded. Events that fall after the end
  of the timecode are counted in a warning. (2026-10-06; executors and places
  2026-10-07)

#### Export to grandMA3

- **A console switch at the top of the Export window: grandMA2 | grandMA3.**
  The window's title follows it, and the parts underneath are that
  console's, in the same order, changing only where grandMA3 differs. The
  show remembers the console last picked. (2026-10-10)
- **Export for grandMA3** writes the loaded song as two files grandMA3
  imports from its library: a macro, and the timecode it imports. In onPC,
  two commands bring them in: import the macro (it replaces whatever is at
  that number) and run it. The macro, in plain commands only:
  - stores each new cue of a Goto sequence, empty, and labels the cues and
    the sequences as on grandMA2;
  - makes the page first when *Create page* is ticked;
  - puts each sequence on its executor where *assign* is ticked, and sets
    the executor's button to the sequence's function (Go+ for a cue list,
    Temp, Flash, Swap and so on), every time, since grandMA3 keeps an
    executor's old button when a sequence is put on it;
  - imports the timecode, names it, and gives it its colour;
  - gives the sequences, the timecode and the macro their colours as
    Appearances;
  - deletes itself as its last line, unless you keep it.

  The timecode has the song's start as its *Offset TC Slot* and its length
  as its *Duration*, a track aimed at each sequence, and an event at every
  mark counted from the start. A Goto names its cue by number, so a cue
  added in between later (2.5) leaves every other Goto on its own cue. Temp,
  Flash and Swop marks are a press and a release. (2026-10-10)
- **Each console keeps its own numbers for each song,** and its own record
  of which cues it holds, so exporting to one never stops the other from
  storing its cues. The first time a song is opened for grandMA3 it starts
  from its grandMA2 numbers: page, timecode pool, sequences, macro, file name
  and the marks left out. Executors move to grandMA3's numbers: grandMA2's
  fader executors 1-90 become 201-290 (grandMA3's row with faders) and its
  buttons 101-190 stay 101-190; the places move the same way, so *6-10*
  becomes *206-210*. (2026-10-10)
- **Timecode Settings** (the gear beside *Timecode*) has everything
  grandMA3's own Timecode Settings window has, grouped as there: *Time*
  (*Name*, *TC Slot*, *Offset TC Slot*, *Duration*), *Playback* (*Auto
  Start*, *Auto Stop*, *Loop Mode*, *Loop Count*, *Switch Off*, *Assert
  Previous Events*), *Display* (*Time Display Format*, *Frame Readout*),
  *Record* (*Record Go*, *Playback and Record*) and *Other* (*User Bits*,
  *Restart Option*, *Note*). *Save to Default* and *Load from Default* work
  as on grandMA2, with a default of grandMA3's own. The slot can be TCSlot 1
  to 8, *<Selected>* or *<Internal>*. Every setting is written into the
  timecode file. (2026-10-10)
- **Create page** (under *Page*, grandMA3 only) makes the song's page before
  anything is put on it: grandMA3 puts nothing on a page it does not have.
  Making a page that is already there is an error, so it is a tick, off
  until you tick it, and the window warns when a page may be missing. A note
  under *Places* gives grandMA3's executor rows. (2026-10-10)
- **Appearances** (under *Colours*, grandMA3 only): grandMA3 colours objects
  with Appearances, so the macro makes one for each colour, from the number
  set here (901 at first), named *Synphonos* and the colour. A colour keeps
  its Appearance from song to song. (2026-10-10)
- **Where the files go for grandMA3:** onPC on this PC (grandMA3's library,
  which every onPC version installed reads), a USB drive (in
  `grandMA3\gma3_library`), or a folder (a `datapools` folder to copy into a
  console's library). On a USB stick the commands start with `Select Drive
  2` and the macro goes back to drive 1 when it is done. (2026-10-10)

#### Tempo and the beat grid

- **Set BPM,** a button next to Speed that shows the tempo once there is one.
  Type it (20 to 400), tap it (*Tap*, four times or more; while the song
  plays the taps also place the first beat), double or halve it (×2, ÷2), or
  **Detect** it from a stem, which finds the tempo and the first beat. A
  click stem gives an exact answer; on a full mix it is a first guess to
  check. Set where bar 1 starts (*First beat*, or *At playhead*) and the
  beats in a bar. The tempo is saved with the song in the show file.
  (2026-09-30)
- **Beat grid.** Once a song has a tempo, beat and bar lines run through the
  stems and the sequences, with bar numbers along the top. Zooming out drops
  the beats first, then the bars. (2026-09-30)
- **BPM paste opens at the song's tempo,** and gives a song that has none the
  tempo it was pasted at. (2026-09-30)

#### Files

- **The Files window,** behind a folder at the right-hand end of the status
  bar, in both modes. (2026-10-03)
  - **Show:** where its file is, *Open folder* (Explorer, with the file
    picked out), *Change folder…* (moves the show file and carries on working
    there), *New show…*, *Load show…* and *Save as…*.
  - **Recent shows:** the last eight opened, started or saved. Click one to
    load it; × takes it off the list and leaves the file alone. A show whose
    file has gone is greyed out.
  - **Settings:** where `settings.toml` is, *Open folder*, *Change folder…*
    to keep the settings somewhere else (a backed-up folder, say) and *Use
    default* to move them back. The crash log moves with them. If that folder
    is missing at start-up (a drive not plugged in), the default folder is
    used for that run and the status bar says so.
  - Anything that would replace a file already there asks first. While the
    show is locked, *New show…*, *Load show…* and the recent list are greyed
    out; moving the files is not.

#### The window

- **A Settings box,** behind a cog at the right-hand end of the status bar,
  in both modes, with four tabs: Tracks, Output (device, LTC, MTC), Keys and
  General (pause, jump, pin the selected mark). (2026-09-30)
- **A zoom bar** above the stems, in both modes. Its thumb is the part of the
  song in view: drag it to move, drag its ends to zoom, double-click it or
  press ↺ for the whole song. It shows the playhead and, in Program mode, a
  tick for every mark. (2026-09-30)
- **Stems size one by one:** Alt+scroll over a stem, or drag the line under
  it, sizes that stem alone. Past about a quarter of the window the stems
  scroll on their own, and the rest of the window stays put. (2026-09-30)
- **The window reopens where it was closed:** the same size and place, and
  maximised if it was. If the screen it was on is no longer attached, it
  opens on one that is. (2026-10-04)
- **It reopens in the mode it was closed in,** Show or Program. The start-up
  animation still hands over to Show mode's layout first, then switches.
  (2026-10-04)

#### The look

- **A new start-up animation, in the new look.** The dark cracks: one split
  through the middle, then more and faster, light pushing through them in
  shafts, until it breaks and the pieces fly out past you. The diamond, the
  two lines and the circle arrive as before but are drawn in the waveform's
  grains, and they are alive: the grains travel along the gold, heat runs
  through it, it flickers and throws off sparks. The hands are rows of
  points, and each finger moves on its own. Clicking still burns it away
  into the window: the hands fall, the diamond burns from the top, the
  circle opens out. The picture now sits a little smaller, with the name
  above it and *Click to begin* below, and the name has lost its two side
  rules. It is drawn live rather than played from pictures, at the window's
  own size; Appearance's switches for the animation, its intro and the name
  work as before, and it still takes the accent colour. It opens into the
  mode you were last in: closed in Program mode, Program mode is what the
  burn reveals, rather than Show mode appearing first and Program mode
  snapping in after it. (2026-10-06; last mode 2026-10-08)

- **The window is set in a new typeface,** Atkinson Hyperlegible, in place of
  the built-in one: the readout, every label and every number. Its figures
  all have the same width, so a running timecode does not shift from side to
  side. (2026-10-05)
- **The waveform is drawn as fine glowing grains** in place of solid bars:
  packed solid through the loud middle, thinning out towards each peak, with
  a haze of light round it. What has played is gold, burning to ember at the
  edges; what is still to come is ivory. The haze spreads from one stem
  across the next and fades out above and below them. (2026-10-05)
- **Outlines and rules in place of filled boxes.** Buttons are thin outlines.
  Speed, Follow, Vol, Locate, Rate and Starts at are a quiet name and a
  value, outlined only under the pointer or while you type. Switches (Show |
  Program, Frames | Beats, Sequences | Track, Cues | Sequences, the Settings
  tabs) are plain words, the chosen one lit with a diamond before it. Corners
  are square. (2026-10-05)
- **The stems and the sequences run to the window's edges,** with no box
  round them, on a ground that is nearly black. (2026-10-05)
- **Rows of controls sit on the window's centre line** in Show mode and in
  Program mode's Small and Medium windows. (2026-10-05)
- **Show mode's readout grows with the window:** larger in a medium window,
  larger again in a wide one, where the speed, transport, rate and start rows
  also become one line and Show | Program moves to the top right corner.
  (2026-10-05)
- **A time ruler under Show mode's stems:** minutes and seconds along the
  foot, as far apart as the zoom allows. (2026-10-05)
- **Lists are ruled, not striped:** the set list, the Marks list, the cue
  table and the sequence list have a thin line under each row, gold under
  the loaded song, the mark the playhead is at, or the selected row.
  (2026-10-05)
- **The cue table and the Marks list dim what has played,** so they read as
  a running order: rows before the playhead are quieter. (2026-10-05)
- **A wide Program window puts the readout at the top left** with the file
  line beside it. (2026-10-05)

- **Cue times, as in the console's sequence sheet.** Each cue can have its
  own fade, out fade, delay and out delay, a mode (Normal, Assert, X-Assert
  or Release), a command the console runs as the cue fires, and an info
  line. Leave a time empty and the console keeps its own. A cue fired again
  later (a repeat) is the same cue, so it shares its times. In a sequence
  without cue numbers (Temp, Flash and the rest) every press fires the same
  cue, so its times belong to the sequence. Copy and paste carry a cue's
  times. (2026-10-11)
- **An Off time for each sequence:** how long it takes to fade out when it
  goes off, at a release, an Off, or after a Release cue. (2026-10-11)
- **Fade and Out columns in the cue table,** next to Hold, to type a cue's
  fade in and fade out without opening anything. For a Temp, Flash or Swop
  sequence, Out is its Off time, the fade after each release. A time the
  cue takes from its sequence shows greyed. (2026-10-11)
- **More in a mark's right-click menu:** its cue's fade, out fade, delay,
  out delay, mode, command and info, and its sequence's Off time. In the
  lower half of the window the menu opens upwards, and the fields scroll in
  a short window. (2026-10-11)
- **Right-click a sequence** (anywhere in it with no mark under the pointer,
  or its row in the Sequences tab) for its Off time and its cues' times: in
  a Goto sequence they are what each cue has unless it has its own, in any
  other they are its one cue's. The Sequences tab also has an **Off**
  column. (2026-10-11)
- **Fades are drawn in the sequences:** a dashed line rises from each press
  over its fade in (after any delay) and falls over its fade out: after a
  release over the sequence's Off time, after a Release cue's fade, or over a
  cue's own out fade. Set a Temp's press, its release and its Off time and
  see where the light is gone. (2026-10-11)
- **A very faint shadow** under marks, the lines through them, holds,
  releases and fades, in the sequences and over the stems, so a gold mark
  reads over the gold waveform. (2026-10-11)
- **The export sends cue times to both consoles.** grandMA2 gets them as
  `Assign Fade 2 Sequence 701 Cue 2` (and OutFade, Delay, OutDelay), the
  mode, command and info as options of the cue, and the Off time on the
  sequence's executor. grandMA3 gets the cue's CueInFade, CueOutFade,
  CueInDelay, CueOutDelay, Release, Assert, Command and Note, and the Off
  time as the fade of the sequence's OffCue (grandMA3 has no Off time of its
  own; MA's notes on bringing grandMA2 shows over do the same). Only what is
  set is written, so an export of a song with no times is as before. On
  grandMA3 onPC 2.4.2 and 2.5.1 every value was imported and read back,
  first export and again over the same cues. A cue's command goes out only
  when it is ticked in the Export window (the next entry). (2026-10-11;
  commands only when ticked 2026-10-12)
- **Cue commands are listed in the Export window, and go out only when
  ticked.** When the marks being exported have cues with commands, the
  window lists each one in full above its summary (*Main cue · cue 1: Go
  Macro 5*) under a tick, *Write 5 cue commands*. The tick is off every
  time the window opens, and again when you switch console. While it is
  off the export leaves the commands out and sends the cues' times as
  usual. A command is something the console runs each time its cue fires,
  and a show from someone else can carry ones nobody at the desk has read.
  The list shows the first twelve and counts the rest, and scrolls when it
  is long, so the summary and the buttons stay in the window. Looked at in
  the window, and in the files written for both consoles; not run on a
  console. (2026-10-12)

### Changed

- **The manual, *Synphonos - How to use.pdf*, is new for 1.1:** 132 pages in
  place of 33, in the program's new look, with the start-up animation's own
  frames on its cover and at the head of each chapter. It opens with a quick
  start (ten steps to timecode leaving the computer) and a tour of the
  window; then chapters by task for running a show and for programming a
  console; then reference: every window, control, key, limit and range, the
  show and settings files, the command line, timecode itself, both console
  exports from end to end, and what each line of the macro does; then
  troubleshooting by what you see, known issues, questions and answers, a
  glossary and an index. Page numbers are the PDF's own, so a number from
  the contents or the index can be typed into a reader's page box, and the
  PDF has bookmarks. Every picture is taken from the running program. It
  says plainly, chapter by chapter and in one table, what has not been tried
  on a real console. It was brought up to the changes of 2026-10-12, and
  every picture taken again from the program that ships: a stem whose file
  is missing and *Look again*, the files a show may not name, cue commands
  and the tick that lets them out, *Store every cue again*, the limits on a
  show file and on sample rates, what the diagnostics hold, the terms
  being asked once more, and how to get Synphonos's MTC into grandMA3 onPC
  on the same PC. (2026-10-11, 2026-10-12)
- **The download is `Synphonos-1.1.0-windows-x64.zip`:** one folder,
  *Synphonos 1.1.0*, holding the program, the manual and the licence. It is
  20 MB, where 1.0's was 16 MB: the manual is four times as long. A
  SHA-256 checksum is made with it (in a file of the zip's name ending
  `.sha256`), to publish beside the link so a download can be checked. The program in it is built from the exact
  dependencies recorded with the source, and nothing in it names the
  machine it was built on. (2026-10-12)
- **Export to MA2… is now Export…,** and opens on the console last picked,
  with the switch at the top of the window. (2026-10-10)
- **Show mode's lower area holds the set list and the marks only.** Tracks,
  Outputs, Keys, *Pause returns to play start* and *Jump* moved into the
  Settings box behind the cog. (2026-09-30)
- **The *Reset view* button is gone;** the zoom bar's ↺, or a double-click on
  the bar, shows the whole song. (2026-09-30)
- ***Offset* is now *Starts at*.** Same setting: the song's timecode at its
  first sample. (2026-09-30)
- **Marks in Show mode are diamonds in the middle of each stem's waveform,**
  one per stem, not a single diamond at the top edge. The play-start flag
  stays at the top. (2026-10-04)
- **Marks in Show mode no longer carry their names along the foot of the
  stems;** the names are in the Marks list. (2026-10-01)
- **Show mode's marks and Program mode's marks are separate.** Show mode has
  its own (name, time and a key, for finding your way round while the show
  runs); Program mode has the marks in sequences. Neither mode shows the
  other's. Keys that go to a mark belong to Show marks only. (2026-10-01)
- **Appearance → Waveform sets every stem's height at once,** and clears any
  stems sized on their own. (2026-09-30)
- **The show line's *New* is *New…*** and asks where the new show goes first.
  (2026-10-03)
- **The show opened at start-up joins the recent list,** so shows from before
  the list existed appear in it as they are used. (2026-10-04)
- **The status bar says *Play*, *Pause* or *Stop*** with a diamond before
  it, and *Play* is gold, not green. Gold is what is live; green, rose and
  red stay for the audio, MTC and key indicators. (2026-10-05)
- **Appearance → Glow also sets the waveform's haze,** from none to twice as
  strong. A dense, loud song fills its stem with haze; this is where to turn
  it down. (2026-10-05)
- **Every Appearance preset has a deeper ground.** A look saved on a preset's
  old ground moves to the new one the first time 1.1 opens it; a ground you
  picked yourself is left alone. (2026-10-05)
- **Marks are larger and ringed,** in the stems and the sequences: each
  diamond has a thin ring of the ground round it, so it stands clear of the
  waveform behind it. (2026-10-05)
- **A sequence's waveform is as strong as the stems' own,** no longer
  dimmed, and the open sequence sits between two gold lines instead of in a
  gold box. The *SEQUENCES* bar is a plain row: *Sequences*, its hint and
  *+ Sequence*. (2026-10-05)
- **The beat grid is fainter,** and its bar lines are as thin as its beat
  lines, only brighter. (2026-10-05)
- **The row you select in the cue table still holds its fields,** but they
  look like the row: gold, and outlined only under the pointer. (2026-10-05)

- **The Sequences tab names executors on the page set in the Export
  window,** not always the song's place in the set list, and says when the
  loaded song has a sequence on an executor of its own. (2026-10-06,
  2026-10-07)
- **Timecodes can be typed with units:** `7h10m`, `7h 10m 5s 12f`, `90m`,
  `30f`; a number after the last unit is the next one down (`7h10` is
  07:10:00:00). It works in every timecode field (*Starts at*, the set list,
  *Locate*, the Export window's *Offset* and *Length*) and turns into
  `HH:MM:SS:FF` when you press Enter or leave the field. `07:10:00:00` works
  as before. (2026-10-09)
- **Copy diagnostics no longer spells out your Windows account's name.**
  The settings file's path is written from `%APPDATA%` on, as
  `%APPDATA%\tcgen\config\settings.toml`. Settings moved to a folder
  outside your user folder are still written in full, and the audio device
  and MIDI port are named as before: read it before you post it.
  (2026-10-12)
- **Opening a show says what it brings with it.** If stems were left out
  (see Fixed), the status bar says how many, at start-up too. If *Ticked
  keys work from other apps* is on and the show's marks have keys ticked
  to work from other apps, *Open…* and the recent list say how many: while
  that show is open those keys are taken from every other program.
  (2026-10-12)
- **The licence, terms and privacy notice are version 1.1, and you are
  asked to accept them once more.** The terms themselves are as they were.
  The privacy notice now lists every file this version writes: the show's
  sequences, cues and export record, the export files, the note left behind
  when the settings are moved, and the two files that can appear beside a
  show while it is saved or when it cannot be read. It also says that a
  show or audio kept on a network drive is read over your network, as by
  any program. The first time 1.1 opens after 1.0, the terms window comes
  up headed *The terms have changed*, with what is different said first.
  From now on it is shown once for each version of the terms, and the
  settings keep which version was accepted. (2026-10-12)

### Fixed

- **A stem that could not be opened was forgotten by the show.** When a song
  loaded and one of its stems was missing or could not be read, the show
  kept only the stems that did open and was saved a second later: the other
  stem's path, level and output channels were gone from the show file, and
  putting the audio back did not bring it back. Opening a show on the backup
  laptop before its audio was copied across, or with the audio drive on
  another letter, was enough. The show now keeps such a stem, in its place
  among the others, with its level, mute and channels, and looks for it
  again every time the song is loaded. **Settings, Tracks** lists it under
  the ones that loaded, in rose, as *not found* (rest the pointer on the
  name for where it was looked for), with **Look again**, which loads the
  song again once the file is back, and × to take it out of the show for
  good. The set list counts it: *3 stems, 1 not found*. The status bar
  says *Cannot load …* and the reason, then *It stays in the show*.
  *Load…* still replaces all of a song's stems, missing ones too; a file
  added for the first time that cannot be played is still not added. Seen
  in the window, and in the show file it saved. This was in 1.0 as well.
  (found 2026-10-11, fixed 2026-10-12)
- **An export that never reached the console still counted as stored.**
  Synphonos notes a sequence's cues as stored when it writes the files, not
  when the macro runs: it cannot see the console. If the macro stopped on an
  error, or was never run, the next export of that song only relabelled
  those cues and never stored them. Once a song has been exported, the
  Export window's **Macro** part has a tick, *Store every cue again*. With
  it ticked, the export stores every cue the sequence should hold and puts
  every sequence back on its executor (each *assign* tick comes back on,
  unless you took it off yourself), as the first export did. The macro
  always clears the programmer first while it is ticked, so a cue the
  console already has is left as it is, with the look stored in it, and the
  tick is safe when you do not know how far the macro got. It is for one
  export: it is off again afterwards, and whenever the window opens. The
  Exported window says where to find it. Looked at in the window, and
  tested in the files for both consoles; not run on a console. (found
  2026-10-07, fixed 2026-10-12)
- **The Marks list in Show mode showed only the first five or six letters
  of a mark's name.** The name's field came out much narrower than it was
  meant to be, so *Verse one, quietly* read *Verse*. It has its full width
  now. (found 2026-10-11, fixed 2026-10-12)
- **Closing Synphonos could leave it running with no window.** If the audio
  was being read from a drive that had stopped answering (a network drive
  that had stalled), closing the window waited for that read for ever: the
  window went, and the program stayed, holding the sound card and the MIDI
  port until it was ended in Task Manager. It now waits two seconds and
  then closes regardless. Not seen happening; from reading the code. This
  was in 1.0 as well. (2026-10-12)
- **Moving a show, or the settings, into the folder it was already in under
  another name deleted the file.** *Change folder…* writes the file in the
  new place and then removes the old one. One folder reached by two names
  (a share by its name and by its address) was not seen as the same place,
  so the file just written was the one removed. The show stayed in memory
  and came back at the next change; the settings came back at the next
  save. Both are now written again at once. (2026-10-12)
- **The Files window stalled when a recent show was on a drive that had
  gone.** The list asked the disk about every show on every frame, and a
  show on an unreachable share made each answer take seconds. It now asks
  once for each show when the window opens. Playback and timecode were
  never affected. (2026-10-12)
- **The Timecode Options window said more had been tried on a console than
  had.** Its note now reads *Only the slot and AutoStart have been imported
  on grandMA2 onPC so far; none of them on a console*, which is what the
  record under Known issues says. (2026-10-12)
- **A missing stem of the loaded song was named twice** in the status bar
  at start-up. (2026-10-12)
- **A show file could make the computer sign in to another computer.** A
  stem's path in a show file was believed as written. One that named a
  server (`\\server\share\band.wav`) made Windows sign in to that server
  as the show opened, before anything was played, which hands the server
  your user name and a hash of your password. One that named a device
  (`COM3`, `NUL`) was opened as if it were audio, and could stop anything
  loading again until a restart. A stem is now opened only from a drive
  letter, or from a network share when the show file itself is kept on
  that same share, and never from a device; the path kept relative to the
  show may climb two folders at most, which is all Synphonos writes. Such
  stems are left out before the disk is asked anything, and the status bar
  says so: *2 stems were left out: this show names files on another
  computer or on a device…* (rest the pointer on it for the whole
  message). A share mapped to a drive letter works as before. What
  changes for your own shows: audio added from `\\server\share\…` to a
  show kept on this computer is left out the next time the show opens, so
  map the share to a drive letter, or keep the show on the share. This is
  in 1.0 as well. (2026-10-12)
- **One bad sample in an audio file could stop playback and timecode.** A
  float WAV holding a sample that is not a number (a plug-in blowing up
  during a bounce is enough), played at a sample rate other than the audio
  device's or at a speed other than 100%, ended the part of the program
  that feeds the audio: playback ran dry, and LTC and MTC with it, until
  Synphonos was restarted. Such a sample is now played as silence, and
  nothing is let through louder than 12 dB over full scale. This is in
  1.0 as well. (2026-10-12)
- **A tiny audio file could take all the computer's memory.** A file whose
  header gave an absurd sample rate (1 Hz, or hundreds of megahertz) made
  Synphonos ask for tens of gigabytes as it loaded, and again at every
  start while the show named it. A file whose sample rate is outside 8,000
  to 768,000 Hz is now refused, and the status bar says *Cannot load …:
  its sample rate is given as 1 Hz: only 8000 to 768000 Hz can be played*.
  This is in 1.0 as well. (2026-10-12)
- **A long crash log could stop Synphonos starting, without a word.** Once
  `crash.log` passed 256 KB it was cut in half at start-up. If the cut
  fell inside an accented character (in a file name, or a Windows message
  that is not in English), the program closed at once, every time, until
  the log was deleted. This is in 1.0 as well. (2026-10-12)
- **Opening a 1.1 show in Synphonos 1.0 stripped it.** 1.0 read the file
  without complaint and, within about a second, saved it back without the
  sequences, cue numbers, holds and tempo. A show saved by 1.1 now begins
  with a line 1.0 cannot read, so 1.0 says the file *is not a readable show
  file* and leaves it exactly as it was, both when it starts on that show
  and from *Open…*. It carries on with an empty show (at start-up) or the
  show it already had (from *Open…*). Rest the pointer on the message in
  1.0 and the whole of it appears, with the line *This show needs Synphonos
  1.1 or later*. Proven with 1.0's own code on copies of real shows; not
  yet seen in 1.0's window. (found 2026-10-03, fixed 2026-10-11)
- **An exported timecode came in 7 hours late, with its end as its length.**
  The file counted every event from 00:00:00:00 and gave the timecode's end
  as its length, so onPC showed a song starting at 07:10:00:00 as 7:15:00
  long with no offset, and every cue 7 h 10 min too late. The timecode's
  *Offset* is now the song's start and its *Length* the length set in the
  window, and the events count from the offset: exactly what fixing it by
  hand on onPC gave (offset 07:10:00:00, length 5:00, every cue moved back
  by 7 h 10 min). Not yet re-imported on a console. (2026-10-09)
- **Temp sequences came up as Flash on the console.** The timecode's events
  were Temp all along (the show onPC saved after the import holds them as
  Temp, the same as Temp presses recorded on the console), but the
  executor's button was left as the console made it. The macro now sets each
  button sequence's executor to its function (Temp, Flash, Swop, Toggle,
  On, Off, Go+, Go-, Top, Pause): on executors it puts a sequence on, and on
  those an earlier export put one on, so exporting again mends Temp buttons
  already on the console. A sequence on an executor you placed yourself
  (*assign* unticked) is not touched. Not yet tried on a console.
  (2026-10-09)
- **An exported macro arrived on the console empty.** The first export
  tried on onPC made a macro with no name and no lines. The commands and the
  files now follow the console's own help and files:
  - an import names its file without `.xml`;
  - nothing asks an import to overwrite, which it cannot do: the macro and
    the timecode at the destination are deleted first;
  - the object in each file is at index 0, as in every file known to import;
  - the files start with a byte-order mark, as the console's own do.

  Not yet confirmed on the console. (2026-10-07)
- **In the Sequences tab, each row's × sat a little further right than the
  one above,** and a long waveform name ran over the Marks count at Medium.
  Every row now has the same width, and the name is cut to its column.
  (2026-10-11)
- **A new show could overwrite the unsaved default show.** *New* pointed the
  empty show at the default file and saved over it. It now asks for a file of
  its own, and the show you were in stays saved where it was. (2026-10-03)
- **At 480 wide, the file line ran past the window's right edge** and
  stretched the stems wider than the window. The position and sample rate now
  move into the file name's hover text when there is no room. (2026-09-29)

### Show files and compatibility

- **1.1 saves shows in a new format (format 2), which Synphonos 1.0 cannot
  open.** A show saved by 1.0 opens in 1.1 as it was: its marks stay Show
  mode's marks, its Program mode starts empty with one sequence (*Main cue*),
  and it is saved as format 2 from then on. Once 1.1 has saved it, 1.0
  refuses it: keep a copy of the 1.0 file for any machine still on 1.0.
  (2026-09-29; marks kept as Show marks since 2026-10-01; closed to 1.0
  since 2026-10-11)
- **Synphonos 1.0 refuses a 1.1 show and leaves the file alone,** where it
  used to strip it (see the first entry under Fixed). The file now begins
  `version = "This show needs Synphonos 1.1 or later"`, where 1.0 looks for
  a number. (2026-10-11)
- **A show saved by a 1.1 build from before 2026-10-11 is protected the first
  time 1.1 opens it.** Nothing has to be done: about a second after it
  opens, the show is saved again with the new first line, and nothing else
  in it changes. Until 1.1 has opened it, 1.0 can still strip it.
  (2026-10-11)
- **After 1.0 has refused a show, 1.1 opens it as before.** 1.0 leaves the
  settings both versions share pointing at a spare file beside the show
  (`<name>.synshow.recovered`). 1.1 goes back to the show itself, unless
  something was saved in the spare from 1.0. (2026-10-11)
- **1.1 never saves over a show from a newer version.** It opens and runs the
  show, says *Changes are not being saved* in the status bar, and leaves the
  file untouched. *Save as…* to a new file is still allowed. (2026-09-29)
- **Update every machine before sharing a 1.1 show.** A machine still on 1.0,
  the backup rig included, will say the show is not readable and run without
  it. (2026-10-11)
- **A show file has limits.** A file over 16 MB is not opened as a show: it
  is left alone, as any unreadable show is. A song keeps at most 20,000
  marks of each kind, and a name, a command or an info line is cut to 256
  characters. All are far past any real show; they stop a damaged or
  deliberately huge file from freezing the program at every start.
  (2026-10-12)

### Known issues

- **A stem left out for naming another computer is not kept by the show.**
  A stem the show may not open (see Fixed: a path on another computer, or
  a device) is left out as the show is read, and the show is saved without
  it. A stem that is merely missing is kept (see Fixed). If the files are
  yours, add them again with *Add…*. (2026-10-12)
- **Running Synphonos 1.0 beside 1.1 can still lose what 1.0 does not know
  about.** Neither of these is a matter of 1.0 reading a show, so the new
  first line does not stop them:
  - 1.0 saves the settings both versions share with only what it knows. 1.1's
    recent shows, the window's size and place, Show or Program, each stem's
    and sequence's height, the pinned selected mark and the last export
    destination go back to how they start.
  - *New* in 1.0 starts its empty show in the default show's file and saves
    over it, whichever version saved it (the fault fixed in 1.1 on
    2026-10-03). A show saved under a name of its own with *Save as…* is out
    of its reach.

  (found 2026-10-11)
- **Export to grandMA2 is only partly checked on a console.** The files
  follow a real console export, the style sheet onPC ships for timecode
  files and onPC's own text, and their contents are tested. The first try on
  onPC 3.9.63 (2026-10-06) left an empty macro: the import command named its
  file with `.xml` and the macro inside asked the import to overwrite,
  neither of which the console's help for Import allows. With both changed
  (see Fixed), the import works on onPC 3.9.63 (2026-10-07). The second
  try showed the timecode's offset and length were wrong, and Temp
  sequences on Flash buttons (both fixed, 2026-10-09). Still to check:
  - the macro runs to its end without an error in the command line, and
    deletes itself;
  - events sit at the right timecode at your frame rate (times are written
    in 30ths of a second, which is how the console counts them at 24, 25 and
    30 fps alike), counted from the offset;
  - a Goto event fires the cue it names, also after a cue has been added
    between two others (2.5);
  - a Temp, Flash or Swop mark presses and releases its executor, and the
    button is the sequence's function;
  - the Timecode Options other than the slot and AutoStart (Runs, Switch
    Off, Status Call, Time Unit, When Ending, When Stopping, User Bits): the
    file uses the names onPC's own program has for them, but no console has
    read them yet. Only what differs from the console's default is written;
  - colours (Appearance) and Info;
  - a track aimed at an executor with nothing on it is kept (the *on 4.1*
    tick puts an empty sequence there in case it is not).

  (2026-10-06; import working 2026-10-07; list brought up to date
  2026-10-09)
- **Export to grandMA3 has been tried on onPC, not on a console.** Every
  command the macro uses, the files, and playback were checked on grandMA3
  onPC 2.4.2 and 2.5.1 (2026-10-10): the macro runs to its end with every
  line accepted and deletes itself; sequences, cues, labels, pages, buttons,
  Appearances and the timecode's settings arrive as set; and played from a
  timecode slot, every Goto fires its own cue and every Temp, Flash and Swap
  presses and releases at its time after the offset. Still to try:
  - on a real console, and from a USB stick (drive 2 is the first stick on
    onPC and most consoles: *List Drive* shows them);
  - grandMA3 2.5 was tried as a copy unpacked from MA's installer, not an
    installed one;
  - the files aim at the *Default* data pool, the one a new show uses; a
    show working in another data pool is not covered;
  - whatever is at the Appearance numbers is given Synphonos's colours.

  With Synphonos's own MTC arriving it has now been tried, on onPC 2.4.2
  through a loopMIDI port (2026-10-12): the slot followed Synphonos, the
  imported timecode started by itself, every Goto fired its own cue,
  every press and release fired, each within two frames of its time, and
  the playbacks went off when Synphonos paused. The cue at the very start of
  the song fired five frames in. onPC took no MIDI from the PC until its
  *MIDI from wing* setting was switched off: the manual says how. Still
  untried that way: onPC 2.5.1, and timecode arriving as LTC.

  (2026-10-10; MTC 2026-10-12)
- **Cue times on grandMA2 are untried on a console and on onPC.** On the
  day they were built grandMA2 onPC would not take typed commands, so the
  lines follow MA's own help and macros (`Assign Fade 3 Cue 2`, `Store Cue 3
  OutFade 4`, `Assign Cue 1 /info=…`, `Assign Executor … /OffTime=…`, the
  `cue_mode` option). Least certain: `/cue_mode=normal`, which takes a cue
  back from Release or Assert (the help lists the other modes, not Normal).
  grandMA3's were all tried on onPC. Still untried on 2026-10-12: grandMA2
  onPC took typed text as a new name for whatever was selected, not as a
  command, so nothing was run on it. (2026-10-11, 2026-10-12)
- **On grandMA2 the Off time needs the sequence on its executor:** it is the
  executor's setting there, so a sequence the export does not put on an
  executor (assign unticked, and not put there by an earlier export) keeps
  the console's Off time. (2026-10-11)
- **Not offered: Trig and Trig time, MIB, Snap, grandMA2's Break and X-Break
  modes, and the other sequence options** (tracking, wrap around, restart,
  protect, priority). A Follow or Time trigger would fight the timecode,
  which fires every cue itself; Break has no grandMA3 equivalent; the rest
  can be added the same way if they are wanted. (2026-10-11)
- **A Temp, Flash or Swop mark cannot have times of its own:** every press
  of such a sequence fires its one cue, so the times are the sequence's. Put
  presses that need other times in a sequence of their own. (2026-10-11)
- **An older 1.1 build drops cue times and Off times** when it saves a show
  that has them, as 1.0 drops sequences (above). (2026-10-11)
- **Record Mode cannot be exported.** The Timecode Options window shows it
  greyed: the timecode file's place for it is not known. Set it on the
  console. (2026-10-09)
- **Seeking to the very end of a song that has a shorter stem** shows "cannot
  seek". This is in 1.0 as well. (noted 2026-09-30)

### Not in this release yet

- **Sending to a console over the network, and exporting every song at
  once,** are not built. (2026-10-06; grandMA3 export built 2026-10-10)
- **Code signing** is still outstanding from 1.0. Until the program is
  signed, the checksum published with the download is the way to tell it
  is the real one. (2026-10-12)
- **Windows DLLs the program loads by name while it runs** (the graphics
  ones) are still looked for beside the exe first. Keep the program in a
  folder of its own. The cure can stop a graphics driver finding its own
  files, and needs trying on more machines than one before it ships.
  (2026-10-12)

## 1.0.0 (2026-09-20)

The first public release: `Synphonos-1.0.0-windows-x64.zip`.

Plays up to eight stems as one song and sends SMPTE timecode locked to the
playback position, as LTC audio and as MTC over MIDI. Set lists and show
files (`.synshow`) that travel to a backup machine, marks with keys, keys
that work from other programs, the show lock, playback speed, waveform zoom
and follow, an adjustable look, the start-up animation, and the licence and
privacy notice. The manual that ships with it, *Synphonos - How to use.pdf*,
describes all of it.
