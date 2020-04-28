# aSpecialKindOfOne
math game for non-readers
This is a math game written by a dislexic grandfather for his 35 grandchildren. Through his own experience with all the excelent advantages of a dislexic mind, he will make all his grandchildren who inherited his gift, develop self respect, and excel beyond their peers.
The Special Kind of One APP utilizes a playlist, and a mediaPlayer. as the grandfather and his grandchildren interact, phrases, numbers, and words are added to the playlist. When execution is paused, the mediaPlayer plays everything that has accumulated in the playlist one time, unless a button is pressed, at which the playlist is emptied, and begins to fill up with new 'words' in response to which button has been selected.
Everything goes well 95% of the time, but for some mysterious reason the program crashes every once in a while. This error is especially irritating if the crash occures during a competition. 
I strongly suspect that the error occures while executing the  code pasted below.
Since i am new to coding in android studio, I suspect that an experienced coder will have little problem improving my code.


private void Play() {
                    if (mp != null) {
                        mp.stop();
                        mp.release();
                        mp = null;
                        timer.cancel();}
                    if (!playlist.isEmpty()) {
                        words = playlist.get(0);
                        mp = MediaPlayer.create(MainActivity.this, words);
                        mp.start();
                        playlist.remove(0);
                        timer = new Timer();
                        if (playlist.size() > 0) playNext();
                    }

                }
                private void playNext() {
                    timer.schedule(new TimerTask() {
                        @Override
                        public void run() {
                            mp.reset();

                            mp = MediaPlayer.create(MainActivity.this, playlist.get(0));

                            mp.start();
                            playlist.remove(0);
                            if (playlist.size() > 0) {
                                playNext();
                            }

                        }


                    }, mp.getDuration() + 100);


                }
                private void StopPlaying() {
                    playlist.clear();
                    if (mp != null) {
                        mp.stop();
                        mp.release();
                        mp = null;
                        timer.cancel();
                    }
                }
