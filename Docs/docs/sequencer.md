# Overview

The **Sequencer** (or Pattern Editor) displays a grid of patterns and it is where you will edit the high level structure of your song.

The sequencer is made of a few components:

* On the left side is the channel & track list.
* At the top is the timeline where each bar is numbered.
* In the middle is the grid of patterns
* In the top-right corner is the floating toolbar containing a few view options

![](images/Sequencer.png#center)

Each column of the sequencer represents exactly **1 Bar** of music, and each row represent a **Track**. A track is always part of a **Channel** and will display the color of its parent channel. A channel may have zero or more tracks. 

Visually all tracks of a channel are the same color and the first track of a channel will have a little icon next to its names, allowing you to mute/solo it.

Please note that the terms channels and tracks do not correspond to the concept of MIDI channels or tracks. This app is not concerned with MIDI beyond import or export. 

There are 2 types of tracks:

* [Piano Roll](pianoroll.md) tracks contain musical notes. 
* [Automation](autotrack.md) tracks contain curves that can modify the value of a single parameter over the course of the song

There are 3 types of channel:

* **Instrument Channels** use an instruments to generate sound. Instrument channel can have either piano roll and automation tracks.
* **Effect Chains** only contain effects and can optionally use automation track to modify the values of effect parameters.
* The **Master Channel** is always present and cannot be deleted. It is effectively the final effect chain but can do special things such as automate the BPM of the song.

# Channels & Tracks

On the left side of the sequencer are all the channel & tracks of the current song. 

![](images/TrackList.png#center)

## Selected channel

The **Selected Channel** is displayed with lighter color in the sequencer and is the channel that will be previewed when playing the pop-up piano, or pressing keys on a MIDI controller. To change the selected channel, simply click on an instrument channel.

In the above screenshot, the "Bitcrushed Drums 1" channel is selected channel.

## Adding channels & Tracks

To add a new channel, simply press the **(+) Add** button below the last track. You will be prompted with the type of channel to add.

Additionally, if there is a selected channel, you'll have the option to add a piano roll track to it. Having multiple piano roll track on a channel is mostly for your own organization, although there are some cases where it is genuinely useful (arpeggios, playing the same note twice, etc.).

To add an automation track, you need to choose a parameter to automate in the [project explorer](instruments.md)

![](images/AddChannel.png#center)

## Deleting channels & tracks

To delete a track or a channel, simply right-click on its name or long press on mobile. A contextual menu will give you the option to delete.

## Muting & Soloing channels

Muting a channel is done by clicking on its icon. Visually, muted channels have their icon dimmed. A single click will mute a channel, while a double click will solo it by muting all the other channels.

## Changing channel parameters

When clicking on any track of channel, the project explorer will navigate to that channel, allowing you to edit its properties. 

On mobile, double tapping on a channel name will also pop open the project explorer from the right on the screen.

![](images/ChannelSettings.png#center)

These parameters are explained more in depth in the [project explorer](instruments.md) section of the documentation, but this is where you can change the name, color, volume, balance and effect send of a specific channel. Individual tracks cannot be renamed.

## Mixer view

A much more efficient way to change the volume, balance and send effect chain of a channel is simply to open the **Mixer View**. This is done by checking the option from **View** section of the floating toolbar on the top right of the sequencer. 

![](images/MixerView.png#center)

## Reordering channels & tracks

On the right of the mixer view are the **Reordering Grips** which allow reordering channel & tracks.

To reorder a channel (i.e. move all the tracks a channel relative to other channels), grab the first track of the channel and you will be able to move the entire channel up or down relative to others.

To reorder a track inside a channel, grab any track that is not the first one, and you will be able to moving it relative to other tracks inside that channel. Please do note that piano roll tracks always come before automation tracks in a channel and this will be enforced during reordering.

# Patterns & Bars

At the center of the sequencer are all the patterns of the current song. 

Patterns are re-usable little units of notes or automation that you can re-use multiple times on a given track. They can be as small as 1 bar, but can be much longer too. 

![](images/PatternEditor.png#center)

## Difference with other DAWs

Before we start, please note that patterns, sometimes called clips in other apps, are edited slightly differently from mainstream DAWs. 

In some DAWs (e.g. FL Studio Mobile), resizing a pattern makes it loop multiple times. In KiraStudio, resizing a pattern simply changes its duration, repetition is done using **Instancing** which creates a linked copy of a pattern. 

Another difference is that, when opening in the piano roll or automation editor, patterns are shown with the rest of the song. In other DAWs, clips are editing in a vacuum, without seeing the outside context. In KiraStudio, the piano roll or automation editor are basically an extreme close up on a track.

Please do keep these differences in mind as you read the next few sections.

## Adding, Deleting & Resizing patterns

Patterns are simply added by clicking in an empty space in the grid. 

* On desktop, patterns are deleted using a double-click and they are resized by grabbing the left or right edge and resizing.
* On mobile a double-tap opens the pattern in the appropriate editor, either the piano roll or automation track editor. To any selected pattern(s) on mobile, you can simply press the **Delete** button from the toolbar (big **X** icon), or use the contextual menu that appears when long-pressing a pattern. To help resizing on small screens, the mobile version will display big colored resize handles for the selected pattern(s), allowing you to resize it from the left or right side.

## Selecting patterns

Selected patterns have a white outline around them and can be moved and resized as a group.

* On desktop, you can select patterns by right-clicking anywhere in the grid and dragging to drag a rectangle. 
* On mobile, you can long-press somewhere and start drawing a rectangle once the pulsating circle appears. 

You can also select entire columns of patterns by doing a selection from the timeline, which is the row with the bar numbers at the top. 

When selecting patterns this way, you will notice that the bar numbers also get a white outline around them. This is important and means that if you copy these patterns, or move them left/right, the associated [custom time signatures](#custom-time-signatures) will also be moved with them. Without the bar highlight, only the patterns are move and no tempo information is.

=== "Desktop"
    ![](images/SelectPatternsDesktop.gif#center)
=== "Mobile"
    ![](images/SelectPatternsMobile.gif#center)

## Copying & instancing patterns

Patterns have an associated 3-digit numbers. This number is a unique pattern on a given track and allows you to tell if a pattern is used multiple times inside a track. Re-using a pattern multiple times in a track is called **instancing**. When modifying a pattern, all of the its instances will be modified at the same time. 

Another way to tell if a pattern is an instance of another is simply to select it and to look for the **chain link icon**. When a pattern is selected, all of its instances will show this icon and the 3-digit numbers will appear white. In the example below, pattern 000 is selected and a few other instance are shown.

![](images/Instance.png#center)

To create an instance of an existing pattern, simply selected it and drag from the little **Colored Chain-Link Button** that appears at the bottom left and release where you want to create the instance. Note that trying to create an instance on a different track will force a copy.

To create a completely separate copy of a pattern, a copy that will retain no connection to the original, simply drag from the **Colored Paperstack Icon** that appears and release it where you want to create the copy.

=== "Desktop"
    ![](images/InstanceCopyPatternsDesktop.gif#center)
=== "Mobile"
    ![](images/InstanceCopyPatternsMobile.gif#center)

## De-instancing patterns

If you have created instances of a pattern, but have second thoughts and want to make a unique copy, you can simply right-click on a pattern (long-press on mobile) and select the **Make Pattern(s) Unique** option. This will create a completely independent copy of it which its own unique 3-digit number.

## Merging identical patterns

On the flip side, if you have created many copies of a pattern and did not end up making any unique changes to them, you can select a few patterns, right click (long-press on mobile) on the selected pattern(s) and choose the **Merge Identical Patterns** option. This will look for perfectly identical pattern and create instances if matches are found.

## Setting the loop point

Each song can have a loop point which is where the song will jump to when the end is reached. Currently this is quite primitive and the song will loop forever. 

* To set the loop point to a specific bar, simply right-click (long-press on mobile) on the bar number in the timeline and choose the **Set Loop Point** option.
* To clear the loop point and create a non-looping song, right-click (long-press on mobile) on the bar number of the currently set loop point and choose the **Clear Loop Point** option.

## Custom time signatures

Songs have a default time signature, which is usually the time signature that covers most of the song. But for each bar of the song, a **Custom Time Signature** can be specified. 

To set a custom time signature for a given bar, right-click (long-press on mobile) on the bar number and select the **Edit Custom Time Signature...** option. If multiple bars are selected using the timeline selection mode, the changes will be applied to all selected bars.

![](images/CustomTimeSignature.gif#center)
