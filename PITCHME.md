@snap[north-west]
<br><br><br>
<h2>@color[orange](Personal Performence Review)<h2>
@snapend

@snap[west]
<br><br><br><br>
Dingyi Chen
@snapend

---

@snap[north-west]
<br><br>
<h4>@color[orange](Involved Poejects)<h4>
@snapend

@snap[west span-100]
<br><br>
@ol[](false)
- Phabricator:<br>@size[0.5em](Setting Phabricator up and run by using docker, as well as introducing development specifaction from git workflow.)

- Launcher:<br>@size[0.5em](Implementing Rokid Glass Laucher systemn UI and refactoring into native launcher3 APP.)

- System UI:<br>@size[0.5em](Starting the development of systemn UI, such as <i>Dialog<i>, <i>Notification<i>, etc. )
@olend
@snapend
  
---

### @color[orange](Project: Phabricator)

**Status:**

@fa[check-square-o fa-1x] Closed

@fa[square-o fa-1x] Under Long Term Maintaince


---

## @color[orange](Outcome Display @fa[hand-o-right fa-8x fa-orange])

---

### [Phabricator](http://gitus.rokid-inc.com/)
![ph](archive/img/screenshot/ph.png)

---

### @color[orange](Git Flow)

<img src="https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg" width="640">

---
### @color[orange](Dialog UI)
![Cartoon](https://raw.githubusercontent.com/dchen23/zaigeiwo2fenzhong/master/archive/img/demo/dialog.mp4)

---

@snap[north-west]
<br><br>
<h4>@color[orange](System UI Developing Pattern)<h4>
@snapend

@snap[west span-100]
<br>
@ol[roman](false)
- Riview Design UI
- Locate Source Code
- Add or Modify API
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

- System UI
- System Apps
- *DevOps*

---

@snap[west span-65]
@fa[linux fa-huge]

@snapend

@snap[north-east span-30]
<br><br><br>
@quote[Android的功夫，在Android之外。](知乎答主)

@snapend

---
@transition[slide-in]

## @color[orange](@fa[android fa-1x fa-spin fa-lime] Thank you @fa[android fa-1x fa-spin fa-lime])

#### Q & A

