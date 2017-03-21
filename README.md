Embedded Assistant Python Sample
================================

This repository contains a Python sample for the Embedded Assistant API.

See
[Getting Started with the Raspberry Pi 3](https://developers.google.com/assistant/) for
instructions on how to run the sample on supported hardware.

Prerequisites
=============
- [Python](https://www.python.org/) (3.x prefered)
- [Google API Console Project](https://console.developers.google.com) w/ Embedded Assistant API [enabled](https://console.developers.google.com/apis).
- [OAuth client ID credentials](https://console.developers.google.com/apis/credentials) with application type `Other`.

Run the sample
==============

- Enter the sample directory

        cd embedded-assistant-sdk-python

- Install the sample and its dependencies:
  - If using python 3 (recommended):

        sudo apt-get update
        sudo apt-get install python3-dev python3-venv portaudio19-dev libffi-dev libssl-dev
        python3 -m venv env
        env/bin/python -m pip install -e ".[MAIN]"

  - If using python 2:

        sudo apt-get update
        sudo apt-get install python-dev python-virtualenv portaudio19-dev libffi-dev libssl-dev
        virtualenv env --no-site-packages
        env/bin/pip install -e ".[MAIN]"

- Verify the audio setup:

        # Record a 5 sec sample and play it back
        env/bin/python -m googlesamples.assistant.audio_helpers

- Authorize the Embedded Assistant sample to make Google Assistant query for a given Google Account.

        env/bin/python -m googlesamples.assistant --authorize client_secret_XXXX.json
        Please go to this URL: ...
        Enter the authorization code:

- Start the Embedded Assistant sample.

        env/bin/python -m googlesamples.assistant

- Record a voice query and the sample should play back the Google
  Assistant answer.

Troubleshooting
===============

- Use the following commands to troubleshoot/workaaround PyAudio issues:
```
# Record an assistant query with alsa commandline tools
arecord --format=S16_LE --duration=5 --rate=16k --file-type=raw in.raw
env/bin/python -m googlesamples.assistant -i in.raw

# Playback an assistant answer with alsa commandline tools
env/bin/python -m googlesamples.assistant -o out.raw
aplay out.raw
```

Test
====

```
# Run tests
env/bin/python setup.py flake8
env/bin/python setup.py test
```

License
=======

Copyright (C) 2016 Google Inc.

Licensed to the Apache Software Foundation (ASF) under one or more contributor
license agreements.  See the NOTICE file distributed with this work for
additional information regarding copyright ownership.  The ASF licenses this
file to you under the Apache License, Version 2.0 (the "License"); you may not
use this file except in compliance with the License.  You may obtain a copy of
the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the
License for the specific language governing permissions and limitations under
the License.
