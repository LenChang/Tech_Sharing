# Introduction
- https://blog.angular-university.io/angular-file-upload/

## Building the User Interface of a File Upload Component
### HTML
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
### CSS
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
