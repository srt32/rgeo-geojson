## RGeo::GeoJSON

RGeo::GeoJSON is an optional module for [RGeo](http://github.com/dazuma/rgeo)
that provides GeoJSON encoding and decoding services.

### Summary

RGeo is a key component for writing location-aware applications in the Ruby
programming language. At its core is an implementation of the industry
standard OGC Simple Features Specification, which provides data
representations of geometric objects such as points, lines, and polygons,
along with a set of geometric analysis operations. See the README for the
"rgeo" gem for more information.

RGeo::GeoJSON is an optional RGeo add-on module that provides GeoJSON encoding
and decoding services. GeoJSON is an emerging standard format used by many web
services that need to communicate geospatial data. See http://www.geojson.org
for more information.

Example:

    require 'rgeo/geo_json'

    str1 = '{"type":"Point","coordinates":[1,2]}'
    geom = RGeo::GeoJSON.decode(str1, :json_parser => :json)
    geom.as_text              # => "POINT(1.0 2.0)"

    str2 = '{"type":"Feature","geometry":{"type":"Point","coordinates":[2.5,4.0]},"properties":{"color":"red"}}'
    feature = RGeo::GeoJSON.decode(str2, :json_parser => :json)
    feature['color']          # => 'red'
    feature.geometry.as_text  # => "POINT(2.5 4.0)"

    hash = RGeo::GeoJSON.encode(feature)
    hash.to_json == str2      # => true

### Installation

RGeo::GeoJSON has the following requirements:

*   Ruby 1.8.7 or later. Ruby 1.9.2 or later preferred.
*   rgeo 0.3.13 or later.
*   If you are using Ruby 1.8, you should install the "json" gem to support
    parsing JSON strings. Ruby 1.9 has JSON support in its standard library
    and does not require the gem.


Install RGeo::GeoJSON as a gem:

    gem install rgeo
    gem install rgeo-geojson

See the README for the "rgeo" gem, a required dependency, for further
installation information.

### To-do list

*   Add support for the "bbox" and "crs" elements.


### Development and support

Documentation is available at http://dazuma.github.com/rgeo-geojson/rdoc

Source code is hosted on Github at http://github.com/dazuma/rgeo-geojson

Contributions are welcome. Fork the project on Github.

Build status: [<img src="https://secure.travis-ci.org/dazuma/rgeo-geojson.png"
/>](http://travis-ci.org/dazuma/rgeo-geojson)

Report bugs on Github issues at http://github.org/dazuma/rgeo-geojson/issues

Contact the author at dazuma at gmail dot com.

### Acknowledgments

RGeo is written by Daniel Azuma (http://www.daniel-azuma.com).

Development is supported by Pirq. (http://www.pirq.com).

### License

Copyright 2010-2012 Daniel Azuma

All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

*   Redistributions of source code must retain the above copyright notice,
    this list of conditions and the following disclaimer.
*   Redistributions in binary form must reproduce the above copyright notice,
    this list of conditions and the following disclaimer in the documentation
    and/or other materials provided with the distribution.
*   Neither the name of the copyright holder, nor the names of any other
    contributors to this software, may be used to endorse or promote products
    derived from this software without specific prior written permission.


THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
