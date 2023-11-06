# Introduction
- How to upload files and preview it if the file is image

## Building the User Interface of a File Upload Component
#### HTML
```
<input type="file" class="file-input"
       (change)="onFileSelected($event)" #fileUpload>

<div class="file-upload">

   {{fileName || "No file uploaded yet."}}

    <button mat-mini-fab color="primary" class="upload-btn"
      (click)="fileUpload.click()">
        <mat-icon>attach_file</mat-icon>
    </button>
</div>
```
#### CSS
```
.file-input {
  display: none;
}
...
```
## How to accept only files of a certain type
```
<label for="avatar">Choose a profile picture:</label>

<input type="file"
       id="avatar" name="avatar"
       accept="image/png, image/jpeg">
```
## How to Upload Multiple Files
```
<input type="file" class="file-upload" multiple>
```

## Show Image Preview
#### HTML
```
<input type="file" accept="image/*" (change)="showPreview($event)" />
```
#### TS file
```
...
showPreview(event) {
    const file = (event.target as HTMLInputElement).files[0];
    const reader = new FileReader();
    reader.onload = (e) => {
      this.imageURL = e.target.result as string;
    }
    reader.readAsDataURL(file)
  }
...  
```
## Reset selected file
> ViewChild
#### html
```
<input #myInput type="file" placeholder="File Name" name="filename" (change)="onChange($event)">
```
#### ts
```
@ViewChild('myInput')
myInputVariable: ElementRef;
...
reset() {
    console.log(this.myInputVariable.nativeElement.files);
    this.myInputVariable.nativeElement.value = "";
    console.log(this.myInputVariable.nativeElement.files);
}
```

# Reference
- https://blog.angular-university.io/angular-file-upload/
- https://developer.mozilla.org/en-US/docs/Web/API/File_API/Using_files_from_web_applications
- https://www.positronx.io/angular-show-image-preview-with-reactive-forms-tutorial/
