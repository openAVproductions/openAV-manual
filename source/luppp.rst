########
Luppp
########

Luppp is a music creation tool, intended for live use. The focus is on real
time processing and a fastintuitive workflow. With extensive MIDI mapping
support, you can get looping just how you like!

Use Case
========

Luppp is designed for live usage.
To see a what features Luppp has and what is possible, check out this video: https://www.youtube.com/watch?v=AcIuKktCaLg

Just Loop!
==========

Before we can start we need to connect some audio source to Luppps master_in and
connect master_right and master_left to the output jacks of the system.

Now we take a look at the Interface:

.. image:: img/luppp/luppp_interface.png
   :align: left

You can see 8 Tracks with each 10 Clips. To check if your setup work just play your audio source and you should see an aplitude on the top right meter. If this works, you are ready to go! Just klick on a Clip to start recording and click another time to start looping it. All actions of Luppp are synced to the Beat, which is indicated by the four squares on the bottom right of the window. You can change the tempo by simply use the knob with the number (which should be 120 by default).

To look how it works, you can watch this video: https://www.youtube.com/watch?v=R6WiWDDKRCQ

Scenes 
======

A pretty important concept of Luppp are the scenes. On each track you can just play one clip at the same time. In the master section of Luppp you can see a list of Scenes, by default 10. You can launch a scene by clicking on it.When you do this, all clips in this row start at the same time.

.. Tip::
   When you use clips with a length higher than one bar, be careful to start the recording at the same time when other clips in the row are starting. If not, launching a scene will create a little mess ;)


.. image:: img/luppp/luppp_track.png
   :align: left

Tracks
======

All tracks of Luppp have some controllers to do incredible thinks. I will walk through them from top to bottom. At first, there is the name of the track. You can change it by simply do a right-click on it. Below this, there is a circle showing the progress of the playing loop in the track. Its pretty useful to look at it when recording other clips in the same row. The next thing to come are the clips. You can give them a name with a right click, too. They also show the currect status of a clip, if its recording, playing or empty. On the buttom is a fader, which adjust the volume of the track mixed to the master. On the left side of the faders are some controls we look at in the next sections.

.. Tip::
	You can use your keyboard, to control the clips! The first scene are the numbers from 1-8, 9 triggers the first scene. The following rows are binded to the subjacent scenes. Just try!

Reverb Send
===========

This feature gives you the great possibility to simply add some reverb on a track. Before we can try, we need to connect Luppps send_out to a reverb of our choice (eg :ref:`roomy`) and the outputs of the reverb back to Luppps master_returns. If its done, we can enable the reverb for each track with the Snd-Button and adjust the amount of reverb the the above knob. Its that simple!

.. Error::
	At the moment the master returns does not work, so you can simply send the output of the reverb to the systems outputs.

There is a video about this topic, too: https://www.youtube.com/watch?v=wLy9oG_WpHg

Sidechaining
============

Using Luppp its very easy to use sidechaining, for example to create some house bass lines.. Its a pretty simple concept: you use one audio signal to control the processing of another signal. This processing could be a compressor or an enveloper (eg :ref:`ducka`). So, how to use it? At first we again need to do some connections. Luppps sidechain_key needs to be connected to a sidechain input and Luppps sidechain_signal needs to be connected to the regular inputs of the plugin. Send the outputs of the plugins back to Luppps master_returns.

.. Error::
	At the moment the master returns does not work, so you can simply send the output of the reverb to the systems outputs.

Back to Luppp. On one track you need to enable the Key-Button. This way the output of the track is the trigger for the sidechain effect. Now you can send each track with the knob above the Key-Button to the plugin. If you want to see how its works, watch these videos: 

* Explanation: https://www.youtube.com/watch?v=-AwtMUeBc9w
* Showcase: https://www.youtube.com/watch?v=bPJQs6w2XQc