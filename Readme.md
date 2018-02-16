<h1>Android OCR example with play vision</h1>

<h3>Example how can you obtain the text</h3>

```java
detector = new TextRecognizer.Builder(this).build();
if(detector.isOperational() && null != bitmap){
	Frame frame = new Frame.Builder().setBitmap(bitmap).build();
    SparseArray<TextBlock> textBlocks = detector.detect(frame);
    StringBuilder sb = new StringBuilder();
    for(int i = 0; i < textBlocks.size(); ++i){
        TextBlock tb = textBlocks.get(i);
        if (tb != null && tb.getValue() != null) {
            sb.append(tb.getValue());
        }
    }
    if(textBlocks.size() == 0){
        textView.setText("Scan failed");
    }else{
        textView.setText(sb.toString());
    }
} else{
    textView.setText("Invalid image");
}
```