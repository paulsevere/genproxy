# One Proxy to Integrate Them All

> This project is now moved to https://github.com/SpectoLabs/hoverfly 

-

## Configuration

Specifying which site to record/playback with regular expression (by default it records everything):
./GenProxy --destination="."

By default proxy is always in playback mode. To switch to record mode, add "--record" flag during startup:
./GenProxy --record

Or you can use API call to change proxy state while running.


Do a curl request with proxy details: 
+ curl http://mirage.readthedocs.org --proxy http://localhost:8500/

### Playback

Start proxy in playback mode:
./GenProxy

## API

Access admin panel under default port 8888:

* Recorded requests: GET http://proxy_hostname:8888/records ( __curl http://proxy_hostname:8888/records__ )
* Wipe cache: DELETE http://proxy_hostname:8888/records ( __curl -X DELETE http://proxy_hostname:8888/records__ ) 
* Get current proxy state: GET http://proxy_hostname:8888/state ( __curl http://proxy_hostname:8888/state__ )
* Set proxy state: POST http://proxy_hostname:8888/state, where
   + body to start playback: {"record":false}
   + body to start recording: {"record":true}
* Exporting recorded requests to a file: __curl http://proxy_hostname:8888/records > requests.json__
* Importing requests from file: __curl --data "@/path/to/requests.json" http://localhost:8888/records__
