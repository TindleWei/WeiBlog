---
layout: post
title:  Screen Density
date:   2016-02-08 11:59:05
categories: Android
excerpt: Screen Density
---

# 宽高计算

在Activity中，可以这样获得宽高密：

```
	float mDensity = getBaseContext().getResources().getDisplayMetrics().density;
	float mScreenHeight = getBaseContext().getResources().getDisplayMetrics().heightPixels;
    float mScreenWidth = getBaseContext().getResources().getDisplayMetrics().widthPixels;
```

例如，我的手机Nexus6手机的分辨率是 1440*2560，
打印出的数据是：
desity:3.5
height:2392.0
width:1440.0

接下来，查看statusBar和navigationBar的高度：

```
    //获取statusBar高度
    public int getStatusBarHeight(Context context){
        int result = 0;
        int resourceId = context.getResources().getIdentifier("status_bar_height", "dimen", "android");
        if(resourceId>0){
            result = context.getResources().getDimensionPixelSize(resourceId);
        }
        return result;
    }

    //获取底部navigationBar高度
    public int getNavigationBarHeight(Context context) {
        int result = 0;
        int resourceId = context.getResources().getIdentifier("navigation_bar_height", "dimen", "android");
        if(resourceId>0){
            result = context.getResources().getDimensionPixelSize(resourceId);
        }
        return result;
    }
```

打印出的数据：
statusbar height:84
navigationbar height:168

接下来计算：
168/3.5=48
2560-2392=168, 所以NavigationBar包括了StatusBar.

--------------------

## dp2px

实际，返回的值是 (int)(dp * density + 0.5f);

### RootView

```
    public void init(){
        ViewGroup decor = (ViewGroup) mActivity.getWindow().getDecorView();
        ViewGroup contentParent = (ViewGroup)mActivity.findViewById(android.R.id.content);
        View rootView = contentParent.getChildAt(0);

        if(loadview==null){
            loadview = LayoutInflater.from(mActivity).inflate(R.layout.layout_loadindview,null);
            FrameLayout.LayoutParams lp = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.WRAP_CONTENT, ViewGroup.LayoutParams.WRAP_CONTENT);
            lp.gravity = Gravity.CENTER;
            loadview.setLayoutParams(lp);
            contentParent.addView(loadview);
            loadview.setVisibility(View.GONE);
        }
    }
```

### 屏幕截图

```
    private void getBitmapScreenshot() {
        //create save path to for file
        String mPath = Environment.getExternalStorageDirectory().toString() + "/" + IMAGE_FILENAME;

        //create bitmap screenshot
        Bitmap bitmap;
        //remove .getRootView() if you want everything but the actionbar.
        View view = getWindow().getDecorView().findViewById(android.R.id.content).getRootView();
        view.setDrawingCacheEnabled(true);
        bitmap = Bitmap.createBitmap(view.getDrawingCache());
        view.setDrawingCacheEnabled(false);

        OutputStream fileOut = null;
        File imageFile = new File(mPath);

        try {
            fileOut = new FileOutputStream(imageFile);
            bitmap.compress(Bitmap.CompressFormat.JPEG, 90, fileOut);
            fileOut.flush();
            fileOut.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }

        Uri uri = Uri.fromFile(new File(mPath));
        //done. next steps are optional. just displaying screenshot for you in app.
        Picasso.with(this)
               .load(uri)
               .into(mScreenshotImageView);
        mPathTextView.setText("Screenshot saved at: " + mPath);
    }
```



