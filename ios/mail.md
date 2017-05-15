## メール画面の表示

* ユーザがメール設定をしていない場合があるので、メールが送れるかのチェックを入れる

### Objective-C

```objective-c
#import <MessageUI/MessageUI.h>

if (![MFMailComposeViewController canSendMail]) {
    UIAlertController* alert = [UIAlertController alertControllerWithTitle:@"Title" message:@"Message"
                                                            preferredStyle:UIAlertControllerStyleAlert];
    UIAlertAction* defaultAction = [UIAlertAction actionWithTitle:@"OK" style:UIAlertActionStyleDefault
                                                          handler:^(UIAlertAction * action) {}];
    [alert addAction:defaultAction];
    [self presentViewController:alert animated:YES completion:nil];
    return;
}

// Email content settings
MFMailComposeViewController *picker = [[MFMailComposeViewController alloc] init];
picker.mailComposeDelegate = self;
[picker setSubject:@"Subject"];
NSString *emailBody = @"Email Body";
[picker setMessageBody:emailBody isHTML:NO];

// Show mail view
[self presentViewController:picker animated:YES completion:nil];
```
