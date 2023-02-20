# CSS Layout - The position Property
## Properties
### static
> It's default position property and it isn't affected by property top, bottom...etc
### relative
> It's positioned relative to its normal position
- it **would** keeps the position:static
  - It **wouldn't** affect others cuz position:static is still existed
- Relative to position:static to move by property top, right ...etc
- It will overlay other blocks but still in same layer. It means that the property will take after parents'
### absolute
> It's positioned relative to the **nearest positioned ancestor** (instead of *fixed*)
- It **wouldn't** keep the position:static
  - It **would** affect others cuz position:static is gone.   
- It will overlay other blocks and belongs to **new layer** which is above on base layer. It also means that the property will only follow the content (**No inheritance**)
#### z-index
> bigger number, higher layer

### fixed
- TBC
### sticky
- TBC

## Reference
- https://www.w3schools.com/css/css_positioning.asp
- https://ithelp.ithome.com.tw/articles/10212202
- [z-index](https://kumo.tw/article.php?id=44)
