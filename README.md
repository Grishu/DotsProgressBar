##Dots progressbar for Android (Horizontal progress bar with dots)
This project provides a horizontal progress bar with dots.

1. Create a class extends View.

          public class DotsProgressBar extends View {
              public DotsProgressBar(Context context) { 
                    super(context);
                    init(context);
                   }
 
            public DotsProgressBar(Context context, AttributeSet attrs) {
                     super(context, attrs);
                     init(context);
                }
 
            public DotsProgressBar(Context context, AttributeSet attrs, int defStyle) {
                 super(context, attrs, defStyle);
                 init(context);
              }
 
           private void init(Context context) {
                 mRadius = context.getResources().getDimension(R.dimen.circle_indicator_radius);
                 // dot fill color
                  mPaintFill.setStyle(Style.FILL);
                  mPaintFill.setColor(Color.BLACK);
                // dot background color
                   mPaint.setStyle(Style.FILL);
                   mPaint.setColor(0x33000000);
                   start();
              }
          }

2. Draw dos in onDraw method


         @Override
         protected void onDraw(Canvas canvas) {
             super.onDraw(canvas);
 
               float dX = (widthSize - mDotCount * mRadius * 2 - (mDotCount - 1) * margin) / 2.0f;
               float dY = heightSize / 2;
                 for (int i = 0; i < mDotCount; i++) {
                     if (i == mIndex) {
                           canvas.drawCircle(dX, dY, mRadius, mPaintFill);
                  } else {
                   canvas.drawCircle(dX, dY, mRadius, mPaint);
                  }
 
                  dX += (2 * mRadius + margin);
              }
          }

3. Set dots count

The **default cout is 3**. You can also set the dots count using ```setDotsCount(int count)``` method. 

![Screenshot](https://raw.github.com/kellysnow/DotsProgressBar/master/screenshot.png)
