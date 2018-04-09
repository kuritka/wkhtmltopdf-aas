# docker-wkhtmltopdf-aas

wkhtmltopdf in a docker container as a web service.

This image is based on the 
[wkhtmltopdf container](https://registry.hub.docker.com/u/openlabs/docker-wkhtmltopdf/).

## Running the service

Run the container with docker run and binding the ports to the host.
The web service is exposed on port 80 in the container.

```sh
docker run -d --name kuritka/docker-wkhtmltopdf-aas -p 127.0.0.1:8080:80 kuritka/docker-wkhtmltopdf-aas
```

The container now runs as a daemon.

Find the port that the container is bound to:

```sh
docker port 071599a1373e 80
```

where 071599a1373e is the container SHA that docker assigned when
`docker run` was executed in the previous command.

Take a note of the public port number where docker binds to.

## Using the webservice

There are multiple ways to generate a PDF of HTML using the
service.

### Uploading a HTML file

This is a convenient way to use the service from command line
utilities like curl.

```sh
curl -X POST -vv -F 'file=@/home/aq446/trash/blah.html' http://127.0.0.1:80 -o /home/aq446/trash/file.pdf
```

where:

* docker-host is the hostname or address of the docker host running the container
* port is the public port to which the container is bound to.
* html contains all resources - embeded images and css
```html
<!DOCTYPE html>
<!-- saved from url=(0022)http://localhost:5000/ -->
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Home Page - GlobalNotes</title>
      <style>
         * {
         box-sizing: border-box;
         }
         html, body {
         height: auto;
         }
         /*div {
         border: 1px solid black;
         }*/
         /*https://css-tricks.com/almanac/properties/p/page-break/*/
         /*https://manytools.org/http-html-text/image-to-data-uri/*/
         .globalNote {
         margin-left: 1cm;
         margin-right: 1cm;
         position: relative;
         padding-top: 0;
         margin-bottom: -5px;
         }
         .globalNote h1 {
         padding-top: 2cm;
         text-align: center;
         }
         .globalNote h2 {
         page-break-before: always;
         color: forestgreen;
         background-color: yellow;
         text-align: center;
         }
         .globalNote h3, h4 {
         page-break-after: avoid;
         }
         .globalNote pre, blockquote {
         page-break-after: avoid;
         }
         .break {
         page-break-after: always;
         }
         .globalNote .signature1 {
         width: 100px;
         height: 100px;
         background: #ffffff;
         border: 0;
         background-repeat: no-repeat;
         background-size: contain;
         background-image: url(data:image/png;base64,iVBORw0KGgoAAAVORK5CYII=);
         }
         .globalNote .signature2 {
         width: 100px;
         height: 100px;
         background: #ffffff;
         border: 0;
         background-repeat: no-repeat;
         background-size: contain;
         background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAATYASUVORK5CYII=);
         }
         .globalNote .logo {
         width: 8cm;
         height: 5.8cm;
         background: #ffffff;
         border: 0;
         background-repeat: no-repeat;
         background-size: contain;
         background-image: url(data:image/jpeg;base64,/9j/4QAYRXhpZgAASUkqAAgAAAAAAAAAAAAAAP/sABFEdWNreQABAAQAAABkAAD/4QNxaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wLwA8P3hwYWNrZXQgYmVnaW49Iu+7vyIgaWQ9Ilc1TTBNcENlaGlIenJlU3pOVGN6a2M5ZCI/PiA8eDp4bXBtZXRhIHhtbG5zOng9ImFkb2JlOm5zOm1ldGEvIiB4OnhtcHRrPSJBZG9iZSBYTVAgQ29yZSA1Lj=);
         }
         .globalNote footer {
         position: absolute;
         bottom: 3cm;
         width: 100%;
         border-top: 3px solid grey;
         }
      </style>
   </head>
   <body>
      <div>
         <br>
         <div>
            <div class="globalNote">
               <h1>DE00000054548712AA1</h1>
               <div>lorem ipsum .....</div>
               <div>
                  <div class="signature1">
                  </div>
                  <div>
                     <div class="logo">
                     </div>
                     <footer>© GlobalNotes 2018</footer>
                     <div class="break"></div>
                  </div>
                  <div class="globalNote">
                     <h1>DE00000054548712AA11</h1>
                     <div>lorem ipsum .....</div>
                     <div>
                        <div class="signature1">
                        </div>
                        <div>
                           <div class="logo">
                           </div>
                           <footer>© GlobalNotes 2018</footer>
                           <div class="break"></div>
                        </div>
                        <div class="globalNote">
                           <h1>GB0000002645545645</h1>
                           <div>lorem ipsum ..</div>
                           <div>
                              <div class="signature1">
                              </div>
                              <div>
                                 <div class="logo">
                                 </div>
                                 <footer>© GlobalNotes 2018</footer>
                                 <div class="break"></div>
                              </div>
                              <div class="globalNote">
                                 <h1>DE00000054548712AA1</h1>
                                 <div>lorem ipsum .....</div>
                                 <div>
                                    <div class="signature1">
                                    </div>
                                    <div>
                                       <div class="logo">
                                       </div>
                                       <footer>© GlobalNotes 2018</footer>
                                       <div class="break"></div>
                                    </div>
                                    <div class="globalNote">
                                       <h1>DE00000054548712AA11</h1>
                                       <div>lorem ipsum .....</div>
                                       <div>
                                          <div class="signature1">
                                          </div>
                                          <div>
                                             <div class="logo">
                                             </div>
                                             <footer>© GlobalNotes 2018</footer>
                                             <div class="break"></div>
                                          </div>
                                          <div class="globalNote">
                                             <h1>GB0000002645545645</h1>
                                             <div>lorem ipsum ..</div>
                                             <div>
                                                <div class="signature1">
                                                </div>
                                                <div>
                                                   <div class="logo">
                                                   </div>
                                                   <footer>© GlobalNotes 2018</footer>
                                                   <div class="break"></div>
                                                </div>
                                             </div>
                                          </div>
                                       </div>
                                    </div>
                                 </div>
                              </div>
                           </div>
                        </div>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </div>
   </body>
</html>
```

### JSON API

If you are planning on using this service in your application,
it might be more convenient to use the JSON API that the service
uses.

Here is an example using python requests:

```python
import json
import requests

url = 'http://0.0.0.0:80/'
data = {
    'contents':  open('/home/aq446/trash/blah.html').read().encode('base64'),
}
css_data = {
 'contents': open('/home/aq446/trash/GlobalNotes_files/print.css').read().encode('base64')
}
headers = {
    'Content-Type': 'application/json',    # This is important
}
response = requests.post(url, data=json.dumps(data), headers=headers)

# Save the response contents to a file
with open('/home/aq446/trash/file1.pdf', 'wb') as f:
    f.write(response.content)
```

Here is another example in python, but this time we pass options to wkhtmltopdf.
When passing our settings we omit the double dash "--" at the start of the option.
For documentation on what options are available, visit http://wkhtmltopdf.org/usage/wkhtmltopdf.txt

```python
import json
import requests

url = 'http://<docker_host>:<port>/'
data = {
    'contents': open('/file/to/convert.html').read().encode('base64'),
    'options': {
        #Omitting the "--" at the start of the option
        'margin-top': '6', 
        'margin-left': '6', 
        'margin-right': '6', 
        'margin-bottom': '6', 
        'page-width': '105mm', 
        'page-height': '40mm'
    }
}
headers = {
    'Content-Type': 'application/json',    # This is important
}
response = requests.post(url, data=json.dumps(data), headers=headers)

# Save the response contents to a file
with open('/path/to/local/file.pdf', 'wb') as f:
    f.write(response.content)
```