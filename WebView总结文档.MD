WebView

//访问url
webview.loadUrl("url");

//在当前webview打开点击的url，不调用系统浏览器
webView.setWebViewClient(new WebViewClient() {
	@Override
	public boolean shouldOverrideUrlLoading(WebView view, String url) {
		return false;
	}
});

//监听页面进度
webView.setWebChromeClient(new WebChromeClient() {
	@Override
	public void onProgressChanged(WebView view, int newProgress) {
		super.onProgressChanged(view, newProgress);
		if (newProgress == 100) {
			progressbar.setVisibility(View.GONE);
		} else {
			if (progressbar.getVisibility() == View.GONE)
				progressbar.setVisibility(View.VISIBLE);
		}
	}
});


//支持javascript
webview.getSettings().setJavaScriptEnabled(true);

//监听后退键，调用webview后退方法
public boolean onKeyDown(int keyCode, KeyEvent event) {
	// 
	if (webView.canGoBack() && event.getKeyCode() == KeyEvent.KEYCODE_BACK) {
		// 
		webView.goBack();
		return true;
	}
	return super.onKeyDown(keyCode, event);
}

