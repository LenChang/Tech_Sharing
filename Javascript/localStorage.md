# What is the difference between sessionStorage and localStorage?
- The main difference between them is that sessionStorage only maintains a storage area. At the same time, the browser is open (including when the page reloads or restores) while localStorage continues to store data after the browser is closed.

# localStorage vs. cookies
- Cookies can only store a maximum of four kilobytes of data, which is significantly less than the five megabytes storage capacity of localStorage.\
- Cookies are automatically sent to the server with every HTTP request, but localStorage aren't
- localStorage doesn't expire, but cookies can be set to expire with conditions

# Advantages and disadvantages of localStorage
## Advantages
- Data stored doesn't expire
- You can still access the data offline without an internet connection
- It's a larger storage capacity compared to cookies
## Disadvantages
- It's synchronous that each called operation only executes on after the other
- Anyone with access the device can access the data
- the storage limitation is 5 MB


# Reference
- https://blog.logrocket.com/localstorage-javascript-complete-guide/#what-localstorage-javascript
