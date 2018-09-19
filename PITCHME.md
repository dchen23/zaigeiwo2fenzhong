@snap[north-west]
<br><br><br><br>
<h2>@color[orange](Rokid Group Sharing)<h2>
@snapend

@snap[west]
<br><br>
<i>Dingyi Chen<i>
@snapend

---

@snap[north-west]
<br><br>
<h4>@color[orange](Outline)<h4>
@snapend

@snap[west span-100]
<br><br>
@ul[circles]
- Setting Phabricator up and run by using docker. as well as introducing development specifaction which using git workflow. 
- Implementing Rokid Glass Laucher systemn UI and refactoring into native launcher3 APP.
- Starting the development of systemn UI, such as <i>Dialog<i>, <i>Notification<i>, etc. 
@ulend
@snapend
  
---

@snap[north-west]
<br><br>
<h4>@color[orange](CodeBase@US)<h4>
@snapend

@snap[west span-100]
<br>
@ul[spaced-list-items]
- The Benefits of using Docker
  + Easily Setup and Backup
  + Good Scalability
- The Benefits of using Phabricator
  + Pre-Commit *Code Review*
  + Robust **Git**, Mercurial, and SVN System
@ulend
@snapend

---

## @color[orange](Click Me @fa[hand-o-down fa-7x fa-pink])

http://gitus.rokid-inc.com/

---

## @color[orange](Git Flow)

![GitFlow](http://lanziani.com/slides/gitflow/images/gitflow_3.png)

---

@snap[north-west]
<br><br>
<h4>@color[orange](How to develop System UI)<h4>
@snapend

@snap[west span-100]
<br>
@ol[roman](true)
- Riview Design UI
- Locate Source Code
- Add new API or Modify Current Implementation
- Change Layout and Logic
- Release for testing
@olend
<br><br>
@snapend

---

### @color[orange](example)

```
com
└── rokid
    └── glass
        └── launcher
            ├── InsettableLinearLayout.java
            ├── ObservableBattery.java
            ├── RokidBatteryView.java
            ├── RokidGlassLauncher.java
            ├── RokidWifiView.java
            ├── Utilities.java
            └── pageindicators
                └── PageIndicatorDotsRokid.java
```

@[6-7](implement battery view)

---
### @color[orange](example)

``` java
@Override
protected void onDraw(Canvas canvas) {
    super.onDraw(canvas);
    canvas.setDrawFilter(mDrawFilter);

    anodeRectF.set(mWidth / 2 - anodeWidth / 2, 0,
            mWidth / 2 + anodeWidth / 2, anodeHeight);
    anodeBottomRectF.set(anodeRectF.left, anodeRectF.bottom - anodeRadius,
            anodeRectF.right, anodeRectF.bottom);

    shellRectF.set(shellStroke / 2, shellStroke / 2 + anodeHeight,
            mWidth - shellStroke / 2, mHeight - shellStroke / 2);

    backgroundRectF.set(shellStroke + powerPadding,
            anodeHeight + shellStroke + powerPadding,
            mWidth - shellStroke - powerPadding,
            mHeight - shellStroke - powerPadding);

    float lightnRatio = (float) lightning.getMinimumHeight() / lightning.getMinimumWidth();
    float iconRatio = 0.6f;
    float lightnOffsetWidth = (mWidth - shellStroke * 2 - powerPadding * 2 ) * (1 - iconRatio) / 2;
    float lightnOffsetHeight = ((mHeight - shellStroke * 2 - powerPadding * 2) -
            (mWidth - shellStroke * 2 - powerPadding * 2 ) * (iconRatio + .2f) * lightnRatio) / 2;
    lightningRect.set(shellStroke + powerPadding + (int)lightnOffsetWidth,
            anodeHeight + shellStroke + powerPadding + (int)lightnOffsetHeight,
            mWidth - shellStroke - powerPadding - (int)lightnOffsetWidth,
            mHeight - shellStroke - powerPadding - (int)lightnOffsetHeight);

    float topOffset = (mHeight - anodeHeight - powerPadding * 2 - shellStroke) *
            (MAX_LEVEL - powerLevel) / MAX_LEVEL;
    powerRectF.set(shellStroke + powerPadding,
            anodeHeight + shellStroke + powerPadding + topOffset,
            mWidth - shellStroke - powerPadding,
            mHeight - shellStroke - powerPadding);

    shellPaint.setStyle(Paint.Style.FILL);
    canvas.drawRoundRect(anodeRectF, anodeRadius, anodeRadius, shellPaint);
    canvas.drawRect(anodeBottomRectF, shellPaint);

    shellPaint.setStyle(Paint.Style.STROKE);
    canvas.drawRoundRect(shellRectF, shellRadius, shellRadius, shellPaint);

    // Drawing background of power.
    canvas.drawRect(backgroundRectF, backgroundPaint);

    canvas.drawRect(powerRectF, powerPaint);

    if (mIsCharging) {
        lightning.setBounds(lightningRect);
        lightning.draw(canvas);
    }
}
```

---

### @color[orange](Future Work)

@snap[north-west span-30]
- System UI
  - Notification
  - Dialog ... 
@snapend

@snap[north-midpoint span-30]
- System Apps
  - Launcher
  - Settings
    - Bluetooth
    - Wifi 
    - cast ...
@snapend

@snap[north-east span-30]
- DevOps
  - CI system
  - Slack Integration
@snapend

---

@snap[west span-55]
@fa[linux fa-huge]
@fa[android fa-4x fa-spin fa-lime]
@snapend

@snap[north-east span-35]
<br>
@quote[Android的功夫，在Android之外。](知乎答主)
@snapend

---
@transition[slide-in]

## @color[orange](Thank you @-@)

### Q & A

