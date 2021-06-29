# anime-music-quiz

[[Video]](https://www.youtube.com/watch?v=7fUicc_lIGA)
[[Lecture]](https://stephen-huan.github.io/assets/pdfs/cs-lectures/computer-vision/convolution/handout.pdf#page=48)

A bot which automatically plays [animemusicquiz](https://animemusicquiz.com/).
Based on minimizing the l2 norm between the given clip and each
song in its database, though the Fast Fourier Transform (FFT).

Future work: make it based off fingerprints, like Shazam.

### Installing and Running

To install dependencies, run:
```shell
pipenv install
```

The program needs to be able to take in system sound. You can create a loopback
device; the exact steps depend on your operating system. For example, in macOS,
one program is [soundflower](https://rogueamoeba.com/freebies/soundflower/).

Once you have the loopback program setup get
its device ID with the following command:
```shell
python -m sounddevice
```

Create a JSON file called `params.json` as follows,
where the device ID was found from the previous command:
```json
{
  "IN": DEVICE_ID
}
```

Finally, run `amq.py` as follows:
```shell
python amq.py
```

It will prompt you for a username and password. To avoid putting
in the login credentials every time, you can store the data
in a JSON file `login.json` as follows (GPG encryption TODO):
```json
{
 "username": "USERNAME",
 "password": "PASSWORD"
}
```

If everything is working properly, it will then prompt you for
a room ID and password. Once that information is given, it
will join the room and once the game starts, will begin play.

It will then warn you if the audio it receives is suspiciously quiet ---
check that the system output is going to the loopback device properly.

