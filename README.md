Pop `index.html` into your public bucket and you have yourself a usable index to browse. All the other examples I found was extremely convoluted and janky. This isn't.

This file is compatible with the iOS home screen: From Safari go to "Share" and then "Add to home screen", this will add an icon to your home screen for super quick usage.
The index file will automatically update when the page is reopened (so you don't need to close the "app" every time you update your bucket). 

If you add an icon file (`icon.jpg`) to the same folder as `index.html`, the home screen shortcut will get that icon.

In order to make `index.html` work properly, you need to enable the following IAM policy for the bucket:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": [
          "*"
        ]
      },
      "Action": [
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::[NAME OF YOUR PUBLIC BUCKET]"
      ]
    },
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": [
          "*"
        ]
      },
      "Action": [
        "s3:GetObject"
      ],
      "Resource": [
        "arn:aws:s3:::[NAME OF YOUR PUBLIC BUCKET]/*"
      ]
    }
  ]
}
```
