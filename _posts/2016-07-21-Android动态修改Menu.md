---
 layout: post  
 title:  Android动态修改Menu  
 date:   2016-07-21   
 categories: Android  
---

## 打开一个包含Fragment的Activity: 
### -- 普通方式 --

这个普通的步骤就可以：

1. 添加 `setHasOptionsMenu(true);`

2. onCreateOptionMenu

3. onOptionItemSeleted

**重要Tip:**    
需要在 onCreate 或 onCreateView中加入 `setHasOptionsMenu(true);`


## 在Activity中切换Fragment:
### -- 特殊方式 --

初始化时调用

```
	getActivity().supportInvalidateOptionsMenu();
```

切换需要调用

```
    @Override
    public void onPrepareOptionsMenu(Menu menu) {
        menu.clear();
        MenuInflater inflater = getActivity().getMenuInflater();
        inflater.inflate(R.menu.menu_zeus_save, menu);
        super.onPrepareOptionsMenu(menu);
    }
```

在ViewPager切换监听调用

```
getActivity().invalidateOptionsMenu();
```

## 补充

这里说一下 `onCreateOptionsMenu` 和 `onPrepareOptionsMenu` 的区别

+ onCreateOptionsMenu：  
只会调用一次，他只会在Menu显示之前去调用一次，之后就不会在去调用。

+ onPrepareOptionsMenu：  
每次在display Menu之前，都会去调用，只要按一次Menu按鍵，就会调用一次。所以可以在这里动态的改变menu。


## SearchView

```
    <item android:id="@+id/action_search"
        android:title="Search"
        android:icon="@mipmap/ic_action_search"
        app:showAsAction="collapseActionView|always"
        android:animateLayoutChanges="true"
        app:actionViewClass="android.support.v7.widget.SearchView"/>
```


```
    public void initSearchView(final Menu menu) {
        SearchManager searchManager = (SearchManager) getActivity().getSystemService(Context.SEARCH_SERVICE);
        MenuItem searchItem = menu.findItem(R.id.action_search);
        if (searchItem != null) {
            MenuItemCompat.setOnActionExpandListener(
                    searchItem, new MenuItemCompat.OnActionExpandListener() {
                        @Override
                        public boolean onMenuItemActionExpand(MenuItem item) {
                            return true;
                        }

                        @Override
                        public boolean onMenuItemActionCollapse(MenuItem item) {
                            return true;
                        }
                    });
            mSearchView = (SearchView) MenuItemCompat.getActionView(searchItem);
            mSearchView.setInputType(InputType.TYPE_TEXT_VARIATION_FILTER);
            mSearchView.setImeOptions(EditorInfo.IME_ACTION_DONE | EditorInfo.IME_FLAG_NO_FULLSCREEN);
            mSearchView.setQueryHint(getString(R.string.action_search));
            mSearchView.setSearchableInfo(searchManager.getSearchableInfo(getActivity().getComponentName()));
            mSearchView.setOnQueryTextListener(new SearchView.OnQueryTextListener() {
                @Override
                public boolean onQueryTextSubmit(String query) {
                    return onQueryTextChange(query);
                }

                @Override
                public boolean onQueryTextChange(String newText) {
                    Toast.makeText(getActivity(), newText, Toast.LENGTH_SHORT).show();
                    return true;
                }
            });
        }
    }
```

