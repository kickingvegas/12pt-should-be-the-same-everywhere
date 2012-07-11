# A 12pt Font Should Be The Same Size Everywhere: Time to Get Serious About Resolution Independence 

## tl;dr

Computer displays have reached high-enough pixel densities where the graphics and text rendered on them should be specified using absolute measurements such as inches or millimeters. Expedient excuses by the computing community to use current pixel-based measurements are just that: expedient. The visual mismatches when rendering computer graphics will only become more pronounced as user interfaces for ubiquitous computing take increasing advantage of multiple displays. We must return to the original design intent of resolution independent graphics to get the benefits of rendering them in a predictable fashion.

## The Problem in a Picture

If you want to display the sentence "The quick brown fox jumped over the lazy dog." using 12 point Time Roman in a box that is specified to be 5 inches across, you will likely observe this when implementing this in [HTML](testPage.html):

![Different renderings of a 5" in HTML](https://github.com/kickingvegas/12pt-should-be-the-same-everywhere/raw/master/different_sizes_measured.png)

The real-world definitions of inches and points (1 point = 1/72<sup>nd</sup> inch) get lost in the translation when the final result shows up on a computer display. The following table shows what is actually measured:

<table width='100%' border='1'>
<tr>
  <th>Model</th>
  <th>Resolution</th>
  <th>Diagonal Size (inches)</th>
  <th><a href='https://en.wikipedia.org/wiki/Pixels_per_inch'>PPI</a></th>
  <th>Actual direct-on-glass 5" measurement (inches)</th>
</tr>
<tr>
  <td>Samsung SyncMaster 910T</td>
  <td>1280x1024</td>
  <td>19</td>
  <td>86.27</td>
  <td>5.5625</td>
</tr>
<tr>
  <td>Apple iMac 27"</td>
  <td>2560x1440</td>
  <td>27</td>
  <td>108.79</td>
  <td>4.4063</td>
</tr>
<tr>
  <td>Apple iPad 2</td>
  <td>1024x768</td>
  <td>9.7</td>
  <td>131.96</td>
  <td>4.8438</td>
</tr>
</table>

## How We Got Here

Folks in hardware and software could never figure out a reliable way to communicate the diagonal display size. It was just easier for the hardware and software to communicate the screen resolution and just punt on factoring in how packed the pixels were when rendering computer graphics. There was never committment by the computer industry to deliver display output that matched real-world measurements.

## "Told You So" - An Old Rant About Resolution Independent Computer Graphics 

The old argument is this: When [rasterizing](http://en.wikipedia.org/wiki/Rasterisation) computer graphics, the only sane APIs are those which faithfully support real-world measurements such as inches or millimeters. This argument for [resolution independence](http://en.wikipedia.org/wiki/Resolution_independence) has been around for a long time:

* 1978 for TeX which introduced the device independent file format.

* 1982 for PostScript which mapped to real-world measurements by specifying a point to be 1/72<sup>nd</sup> of an inch.

* 1987 for [DisplayPostscript](http://en.wikipedia.org/wiki/Display_PostScript) which unified an imaging model between printing and displaying to a screen. 

The advent of mass-market high density (&ge;160 Pixels Per Inch (PPI)) displays today has made designing user interfaces that work consistently across them a challenge. Add the fact that large number of those displays are touch-enabled, then the argument to faithfully support real-world measurements in graphics APIs becomes even more compelling.

*To do otherwise is just a hack.*

A number of unnatural metrics for computer graphics to account for different displays have arisen, particularly in the mobile space:

* [iOS points vs pixels](http://developer.apple.com/library/ios/#documentation/windowsviews/conceptual/viewpg_iphoneos/WindowsandViews/WindowsandViews.html)

* [Android density-independent pixel (dp)](http://developer.android.com/guide/practices/screens_support.html)

Both approaches above do not specify dimensions that map reliably to measurable units that humans can touch and see. 

## We Need To Fix This Now

The development effort to support multiple display densities in building user interfaces using existing approaches is neither sustainable nor fun. We are starting to conceive of and build deeply pervasive and ubiquitous computing applications that define interactions across multiple displays.

The abstractions that we use to build these user interfaces will have to stop taking into account display density.

## It's Not Too Late

Computers aren't a fad and resolution independent graphics is a solved problem. It just requires willingness from the computer industry to do implement it. Solve this and then we can really have the fancy things we're seeing in the movies.

## "All of this has happened before, and it will all happen again."

Where will this argument be in another 25 years?

## Links

[Pixels Per Inch (PPI) Calculator](http://members.ping.de/~sven/dpi.html)


