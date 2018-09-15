# react-file-upload

- Demo: 

## Tools
- **cloudinary**: For storing photos online 
- **Dropzone**: a node module for dragging and dropping files to be downloaded
- **request** - a node module for making post request to Cloudinary


## Setup the component
- setup the component's **state** for the url (this is the url where the image is stored in Cloudinary)
  ```javascript
  this.state = { 
      uploadedFileCloudinaryUrl: '',
   };
  ```
- setup the **render method**
  - renders the image if the state currently contains a URL 
  ```javascript
  render() {
    return (
        <div>
        {(this.state.uploadedFileCloudinaryUrl) ? 
            <img src={`${this.state.uploadedFileCloudinaryUrl}`} width="150px"/>
            : 
            /* dropzone component will go here
        }
      </div>
    )
}
```
## Create the Dropzone component
- install and import the Dropzone module
  ```javacsript
  $ npm install react-dropzone

  import Dropzone from 'react-dropzone';
  ```
- create the dropzone in the app:
  ```javascript
   <Dropzone
        multiple={false}
        accept="image/*"
        onDrop={this.onImageDrop}>
        <p>Drop an image or click to select a file to upload.</p>
    </Dropzone>
  ```
  - Dropzone properties:
    - `multile=BOOLEAN`: if multiple images can be acceped
    - `accetp=STRING`: type of files accepted
    - `onDrop=FUNCTION`: function to run when image is submitted

## the onDrop method 
- create the onDrop method in the component
  ```javascript
  onImageDrop = (files) => {

  }
  ```
  - accepts a `files` argument which is an array of all the images the user submitted 
- in Clouidnary -
  - in "settings": change to "unsigned mode" to allow uploads directly to clouinary and grab the "preset name" 
  - in the dashboard: grab the "API Base URL" for image upload
- create variables for the upload preset and upload url
  ```javascript
  const CLOUDINARY_UPLOAD_PRESET = "<Upload preset>";
  const CLOUDINARY_UPLOAD_URL = "https://api.cloudinary.com/v1_1/<CLOUDINARY APP NAME>/image/upload"
  ```
- we are going to use `superagent` for making the request to cloudinary so we need to install and import it
  ```javacsript
  $ npm install superagent

  import request from 'superagent'
  ```







