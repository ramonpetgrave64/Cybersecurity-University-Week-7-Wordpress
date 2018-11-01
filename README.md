# Cybersecurity-University-Week-7-Wordpress
example attacks on Wordpress

# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. WordPress 4.2 - Persistent Cross-Site Scripting, CVE-2015-3440
  - [ ] Summary: 
  
      This is a stored XSS attack affecting comments. When the attacker's comment is viewed, the script is executed. The comment must be more than 64kb long, so that the database will truncate the comment when storing. This causes the HTML wrappings on the comment to be malformed, allowing the javscript injection.
      
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.11
  - [ ] GIF Walkthrough: ![WP 4.2 xss comment gif](https://github.com/ramonpetgrave64/Cybersecurity-University-Week-7-Wordpress/blob/master/xss%20comment.gif?raw=true)
  - [ ] Steps to recreate: 
- Enter the comment below, with the 64kb of filler text (64*1024 characters). 
- ``` <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a> ```

2. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
    
3. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

On Windows 10, I had trouble setting up the WPDistillery. Posts would create, but attempting to navigate to them would result in 404.
I got around this by proceeding though http://wpdistillery.vm/wp-admin/setup-config.php

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
