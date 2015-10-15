---
layout: post
title:  “Activity killed by system“
date:   2015-10-11 12:34:20
categories: Android dev
highlight: true
image: http://4.bp.blogspot.com/-IOD6VutWGlA/UW8Jq05M0DI/AAAAAAAAAeA/OVckWFybKqg/s1600/DSC01317.JPG
---
Coding in Android is not difficult. But sometimes if you don't understand how Android works it may fail you and you have no idea what is going on. 

Recently I encounted with this exception with Fragment:
> java.lang.IllegalStateException: Can not perform this action after onSaveInstanceStateIt turns out that somehow, when I launch this Activity, system kills it immediately and restart it again. And I have a thread to load data before it's displayed in fragment. Notice that when Activity is destroied, the thread is still running, as a result of which, it has a reference of this Activity. It still tries to add this fragment in this old Activity (which is supposed to be destroied). There it goes wrong. 
The code is simplified as follow:
    //in onCreate()    new Handler().postDelayed(new Runnable() {        @Override        public void run() {            Fragment fragment = new MainFragment();            getSupportFragmentManager().beginTransaction()                .replace(R.id.main_content, fragment)                .commit();        }    }, 5000);
    Therefore, the solution is quite simple, set a flag as true only after onDestroy() is called, then you won't want to add this fragment when it's true, like this:
    @Override    protected void onDestroy() {        super.onDestroy();        isDestroyed = true;    }    //in onCreate()    new Handler().postDelayed(new Runnable() {        @Override        public void run() {            if(flag) return;            ...        }    }, 5000);It looks fine now, but there's another problem. onCreate() in Fragment is called twice. That's because Activity cashes fragments itself. That's simple, cause Fragment has its own onSaveInstanceState, if Activity doesn't cache it, how it's supposed to call onSaveInstanceState? Therefore, the solution is as simple as this:    @Override	protected void onCreate(Bundle savedInstanceState) {		new Handler().postDelayed(new Runnable() {            @Override            public void run() {                addFragment(savedInstanceState == null);            }        }, 5000);	...	private void addFragment(boolean isNull){        Fragment fragment = null;        if(isNull){            fragment = new MainFragment();        }else{            fragment = getSupportFragmentManager().findFragmentByTag("fragment");        }        getSupportFragmentManager().beginTransaction()                .replace(R.id.main_content, fragment, "fragment")                .commit();    }