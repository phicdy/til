http://stackoverflow.com/questions/26404951/avoid-passing-null-as-the-view-root-warning-when-inflating-view-for-use-by-ale

``java
// Show waring to null parent
//getLayoutInflaor().inflate(context, R.layout.dialog_edit, null);
View.inflate(context, R.layout.dialog_edit, null);
```
