# Overview
> https://valor-software.com/ngx-bootstrap/#/
# modal
## trouble shooting
### How to get a return value from a modal?
```
this.modalRef = this.modalService.show(HomeModalComponent);
this.modalRef.content.onClose.subscribe(result => {
  console.log('results', result);
})
```
#### Reference
- https://stackoverflow.com/questions/46408428/ngx-bootstrap-modal-how-to-get-a-return-value-from-a-modal
