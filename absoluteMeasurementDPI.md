# A 12pt Font Should Be The Same Size Everywhere: Time to Get Serious About Resolution Independence 

## tl;dr

Computer displays have reached high-enough pixel densities where the graphics and text rendered on them should be specified using absolute measurements such as inches or millimeters. Expedient excuses by the computing community to use current pixel-based measurements are just that: expedient. The visual mismatches when rendering computer graphics will only become more pronounced as user interfaces for ubiquitous computing take increasing advantage of multiple displays. We must return to the original design intent of resolution independent graphics to get the benefits of rendering them in a predictable fashion.

## The Problem in a Picture

If you render the sentence "The quick brown fox jumped over the lazy dog." using 12 point Times Roman in a box that is specified to be 5 inches across in [HTML](testPage.html), you will likely observe the following:

![Different renderings of a 5" in HTML](https://github.com/kickingvegas/12pt-should-be-the-same-everywhere/raw/master/different_sizes_measured.png)

The real-world definitions of inches and points (1 point = 1/72<sup>nd</sup> inch) get lost in translation when the final result shows up on a computer display. The following table describes what is actually observed:

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

Computer hardware and software people could never figure out a reliable way to communicate the diagonal display size. It was just easier for the hardware and software to communicate the screen resolution and just punt on factoring in how packed the pixels were when rendering computer graphics. There was never committment by the computer industry to deliver display output that matched real-world measurements.

## "Told You So" - An Old Rant About Resolution Independent Computer Graphics 

The old argument is this: When [rasterizing](http://en.wikipedia.org/wiki/Rasterisation) computer graphics, the only sane APIs are those which faithfully support real-world measurements such as inches or millimeters. This argument for [resolution independence](http://en.wikipedia.org/wiki/Resolution_independence) has been around for a long time:

* 1978 for TeX which introduced the device independent file format.

* 1982 for PostScript which used real-world measurements by specifying a point to be 1/72<sup>nd</sup> of an inch.

* 1987 for [DisplayPostscript](http://en.wikipedia.org/wiki/Display_PostScript) which unified an imaging model between printing and displaying to a screen. 

The advent of mass-market high density (&ge;160 Pixels Per Inch (PPI)) displays today has made designing user interfaces that work consistently across them a challenge. Add the fact that many of those displays are touch-enabled, then the argument to faithfully support real-world measurements in graphics APIs becomes even more compelling.

*To do otherwise is just a hack.*

A number of unnatural metrics for computer graphics to account for different displays have arisen, particularly in the mobile space:

* [iOS points vs pixels](http://developer.apple.com/library/ios/#documentation/windowsviews/conceptual/viewpg_iphoneos/WindowsandViews/WindowsandViews.html)

* [Android density-independent pixel (dp)](http://developer.android.com/guide/practices/screens_support.html)

Both approaches above do not specify dimensions that map reliably to measurable units that humans can touch and see. 

## We Need To Fix This Now

The current approach to building user interfaces to support multiple display densities is neither sustainable nor fun. We are starting to conceive of and build deeply pervasive and ubiquitous computing applications that define interactions across multiple displays. To efficiently build such user interfaces, we need software and hardware that take into account display density.

## Yes, but&hellip;

Expedient Excuses:

* Legacy support. Too much code has been written using pixel dimensions.

    Moving to using points or dp is a step towards migrating away from pixels. What needs to be done next is to lock down the mapping of these units into real-world dimensions.

* Too many different kinds of displays.

    Start implementing resolution independing graphics with displays that are 100 PPI or higher. (Prediction: in 5 years all new mobile handsets will have > 160 PPI screens.)   

* Font-hinting gets thrown under a bus.

    Font-hinting becomes less necessary at 200 PPI and higher. That said, resolution  independent implementation of fonts at 100 PPI will still be a challenge but can be considered in the long term (say 10 years from now going forward) a short-term problem. Hardware vendors could relish at the thought of selling high density displays to replace existing ~100 PPI displays today.

* Getting vendor consensus on specifications is too hard.

    You have to start somewhere, sometime. Having the hardware and software development community to understand that we can fix this problem *now* is a good place to start.
        
    
## It's Not Too Late

Resolution independent graphics is a solved problem. My appeal is to software and hardware developers to ensure that a 12 point font will be rendered the same size everywhere, regardless of screen size and density. With high PPI displays we can deprecate the practice of using pixels to describe dimension. Solve this and then we can really have the fancy things we're seeing people imagine in the movies.

## "All of this has happened before, and it will all happen again."

I'm writing this in the middle of July 2012. Where will this argument be in another 25 years?

## Links

[Pixels Per Inch (PPI) Calculator](http://members.ping.de/~sven/dpi.html)

## Acknowlegements

