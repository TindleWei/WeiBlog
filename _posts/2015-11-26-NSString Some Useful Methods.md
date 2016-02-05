---
layout: post
title: NSString Some Useful Methods
date:   2015-11-26
categories: iOS
excerpt: Web App 相关技术，移动端的 web 应用
---

2015-11-26-NSString Some Useful Methods

1. [string substringToIndex:N]
 get substring from 0 to N-1;

2. [string substringFromIndex:N]
 get substring form N to length-1;

3. [string substringWithRange:NSMakeRange(N,M)]
 get substring from N to N+M-1;

 4. ([string rangeOfString:@“A”].location == NSNotFound)
 check substring contains ‘A’;

 5. Get Range Of String
 \`\`\`
\`NSString\*string =@“abcdefgh”;
NSRange range = [string rangeOfString:@"fg”]();
NSLog(@"rang:%@",NSStringFromRange(range));//{5,2}
string = [string substringWithRange:range]();
\`\`\`
\`
6. Separate String
\`\`\`
\`NSString\*string =@“123A456”;
NSArray \*array = [string componentsSeparatedByString:@"A"]();
NSLog(@"array:%@",array); 
\`\`\`
\`

