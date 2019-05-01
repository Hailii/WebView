# 实验5
## WebView
### 新建一个工程使用 WebView 来加载 URL
#### 截图
![无法显示](/images/1.jpg)
#### 关键代码
```
private String uriHome = "http://www.baidu.com";
    private String url;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        WebView webView = (WebView) findViewById(R.id.webview);
        webView.getSettings().setJavaScriptEnabled(true);

        webView.setWebViewClient(new WebViewClient(){
            @Override
            public boolean shouldOverrideUrlLoading(WebView view, String url) {
                view.loadUrl(url);
                return true;
            }
        });

        Intent intent = getIntent();
        Uri data = intent.getData();
        if (data == null) {
            url = "http://www.baidu.com";
            data = Uri.parse(url);
        }
        webView.loadUrl(data.toString());
    }
```
