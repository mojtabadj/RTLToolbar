# RTL Toolbar
Action Menu | Snipper Menu
---- | ----
![Action Menu](https://github.com/mojtabadj/RTLToolbar/raw/master/resources/action_menu.jpg) | ![Snipper Menu](https://github.com/mojtabadj/RTLToolbar/raw/master/resources/snipper_menu.jpg)

## Create RTL Toolbar
In `Layout`
```java
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <android.support.v7.widget.Toolbar
        android:id="@+id/toolbar"
        android:minHeight="?attr/actionBarSize"
        android:background="@color/colorPrimary"
        android:layout_width="match_parent"
        android:layout_height="64dp">

        <Spinner
            android:id="@+id/spinner_nav"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

    </android.support.v7.widget.Toolbar>

</RelativeLayout>
```
In `Activity`
```java
// Array of choices
        String colors[] = {"Red","Blue","White","Yellow","Black", "Green","Purple","Orange","Grey"};

        // Selection of the spinner
        Spinner spinner = (Spinner) findViewById(R.id.spinner_nav);

        // Application of the Array to the Spinner
        ArrayAdapter<String> spinnerArrayAdapter = new ArrayAdapter<String>(this,   android.R.layout.simple_spinner_item, colors);
        spinnerArrayAdapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item); // The drop down view
        spinner.setAdapter(spinnerArrayAdapter);
        spinner.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {
            @Override
            public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {

                Toast.makeText(MainActivity.this, adapterView.getItemAtPosition(i).toString(), Toast.LENGTH_LONG).show();

            }

            @Override
            public void onNothingSelected(AdapterView<?> adapterView) {

            }
        });

        setTitle(null);
        Toolbar topToolBar = (Toolbar)findViewById(R.id.toolbar);
        setSupportActionBar(topToolBar);
        topToolBar.setLogo(R.mipmap.ic_launcher);
        topToolBar.setLogoDescription(getResources().getString(R.string.logo_desc));
        topToolBar.setLayoutDirection(View.LAYOUT_DIRECTION_RTL);
        getSupportActionBar().setDisplayShowTitleEnabled(false);
```

