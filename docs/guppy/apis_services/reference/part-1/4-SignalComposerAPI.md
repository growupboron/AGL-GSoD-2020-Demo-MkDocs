---
edit_link: ''
title: Signal Composer API
origin_url: >-
  https://git.automotivelinux.org/apps/agl-service-signal-composer/plain/docs/part-1/4-SignalComposerAPI.md?h=guppy
---

<!-- WARNING: This file is generated by fetch_docs.js using /home/boron/Documents/AGL/docs-webtemplate/site/_data/tocs/apis_services/guppy/agl-service-signal-composer-developer-guides-api-services-book.yml -->

# Signal Composer API

## subscribe/unsubscribe

Using subscribe you can get update on change for signals you chose and you can
using wildcard to subscribe several signals in the same time.

```json
signal-composer subscribe {"signal": "rear_left*"}
ON-REPLY 1:signal-composer/subscribe: {"jtype":"afb-reply","request":{"status":"success","uuid":"3d4b743b-7ac6-4d3c-8fce-721107f9dee5"}}
```

Then event comes up like the following:

```json
ON-EVENT signal-composer/257b343e-8ea9-4cd7-8f9e-1904fa77f8f2({"event":"signal-composer\/257b343e-8ea9-4cd7-8f9e-1904fa77f8f2","data":{"uid":"rear_left_door","event":"low-can\/messages.doors.rear_left.open","timestamp":4833910845032292484,"value":false},"jtype":"afb-event"})
```

Unsubscribe happens the same way. When no more signals are holded by the client
then it unsubscribe from the *AGL Application Framework* event handle.

## addObjects

Let you add sources or signals objects to the signal composer service after
its initialization phase. Use this verb and specify the file as argument, you
could use only the file name or the file name with its absolute path.

```json
signal-composer addObjects {"file": "sig_doors.json"}
ON-REPLY 1:signal-composer/addObjects: {"jtype":"afb-reply","request":{"status":"success","uuid":"00d7a519-816e-486a-8163-3afb1face4fa"}}
signal-composer addObjects {"file": "/tmp/sig_doors.json"}
ON-REPLY 2:signal-composer/addObjects: {"jtype":"afb-reply","request":{"status":"success"}}
```

You can follow the activity using the service log journal and check that the
correct number of objects has been added.

> **CAUTION**: You need to get the following permission to be able to load new
objects : `urn:AGL:permission::platform:composer:addObjects`

## get

You can get a signal value be requesting the API with the verb *get*:

```json
signal-composer get {"signal": "vehicle_speed", "options": {"average": 10}}
signal-composer get {"signal": "vehicle_speed", "options": {"minimum": 10}}
signal-composer get {"signal": "vehicle_speed", "options": {"maximum": 10}}
signal-composer get {"signal": "vehicle_speed"}
```

You apply apply some simple mathematical function by default present in the
binding, by default **last** is used:

- **average**: make an average on X latest seconds.
- **minimum**: return the minimum value found in the X latest seconds.
- **maximum**: return the maximum value found in the X latest seconds.
- **last**: return the latest value.

## list

Verb **list** will output the list of defined signals.
