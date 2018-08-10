# More Time Documentation V0.1
## Introduction

This game is based on a story I wrote many years ago, it was supposed to be part of a certain contest, but unfortunately, I couldn't participate.
So, instead of that, I did this game, as a foundation for what's to come.

## Index

[#Subtitles] Subtitles Behaviour


## Subtitles

Subtitles behave in a simple way, they are handled by [https://github.com/roguecode/Unity-Simple-SRT]Unity-Simple-SRT. 
In summary, the system uses two text game objects in a canvas and an ".srt" file converted into a plain ".txt" file.

It has been modified so it changes a flag in the King's game object, so it can only play one object's story dialog at a time. When the Subtitle Displayer (from Unity-Simple-SRT) finishes playing the dialog, it changes the "playing" state in the King's script to false, so it can play another dialog.

This is the code that makes this work.
```c#
if (hitting && (playing == false)){
            if (Input.GetMouseButton(0)){
                timer += Time.deltaTime;
                if (timer >= holdTime) {
                    StartCoroutine(hit.transform.gameObject.GetComponent<SubtitleDisplayer>().Begin());
                    playing = true;
                }
            }
        }
```