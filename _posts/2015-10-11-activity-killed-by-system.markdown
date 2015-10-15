---
layout: post
title:  Activity killed by system
date:   2015-10-11 12:34:20
categories: Android dev
highlight: true
image: http://4.bp.blogspot.com/-IOD6VutWGlA/UW8Jq05M0DI/AAAAAAAAAeA/OVckWFybKqg/s1600/DSC01317.JPG
---
Recently I encounted with this exception with Fragment:
> java.lang.IllegalStateException: Can not perform this action after onSaveInstanceStateIt turns out that somehow, when I launch this Activity, system kills it immediately and restart it again. This happens when the system memory is low. 

It won't happen in every case cause most of the activities ain't large enough to force system to shut them down. However, you can test it by setting ‘Don't keep activities’ in Developer options. Once set, the system will force activities to shut them down when they're invisible to users(like when you hit the home button, the system will shut this activity down, which triggles onSaveInstanceState()). Therefore, you may be able to test what is gonna happen when the system shuts activities down.

Let's go back to the problem. I have a thread to load data before fragment is created. Notice that when Activity is destroyed, the thread is still running, as a result of which, it has a reference of this Activity. It still tries to add this fragment in this old Activity (which is supposed to be destroied). There it goes wrong. 
The code is simplified as follow:
    //in onCreate()
    //Let's say we have this Runnable to do something
    //5 seconds later, it adds the fragment    new Handler().postDelayed(new Runnable() {        @Override        public void run() {            Fragment fragment = new MainFragment();            getSupportFragmentManager().
                beginTransaction()                .replace(R.id.main_content, fragment)                .commit();        }    }, 5000);
    Therefore, the solution is quite simple, set a flag as true only after onDestroy() is called, then you won't want to add this fragment when it's true, like this:
    @Override    protected void onDestroy() {        super.onDestroy();        flag = true;    }    //in onCreate()    new Handler().postDelayed(new Runnable() {        @Override        public void run() {            if(flag) return;            Fragment fragment = new MainFragment();            getSupportFragmentManager().
                beginTransaction()                .replace(R.id.main_content, fragment)                .commit();        }    }, 5000);Let's change this code into async load, which means you'll add this fragment in Main Thread. Your code may be like this:

    //in onCreate()
    Fragment fragment = new MainFragment();    getSupportFragmentManager()
            .beginTransaction()            .replace(R.id.main_content, fragment)            .commit();

Then hit the home button and re-enter this activity. You'll find onCreate() in MainFragment is called twice.
That's because Activity cashes fragments itself. That's simple, cause Fragment has its own onSaveInstanceState, if Activity doesn't cache it, how it's supposed to call onSaveInstanceState? Therefore, the solution is as simple as this:    @Override	protected void onCreate(Bundle savedInstanceState) {        addFragment(savedInstanceState == null);	    ...	private void addFragment(boolean isNull){        Fragment fragment = null;        if(isNull){            fragment = new MainFragment();        }else{            fragment = getSupportFragmentManager()
                   .findFragmentByTag("fragment");        }        getSupportFragmentManager()
                .beginTransaction()                .replace(R.id.main_content, fragment, "fragment")                .commit();    }