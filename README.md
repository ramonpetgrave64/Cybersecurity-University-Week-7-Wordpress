# Cybersecurity-University-Week-7-Wordpress
example attacks on Wordpress

# Project 7 - WordPress Pentesting

Time spent: 10 hours spent in total

> Objective: Find, analyze, recreate, and document vulnerabilities affecting an old version of WordPress

## Pentesting Report

1. WordPress 4.2 - Commenting XSS, CVE 2015-3440
  - [ ] Summary: 
  
      This is a stored XSS attack affecting the comment system. When the attacker's comment is viewed, the script is executed. The comment must be more than 64kb long, so that the database will truncate the comment when storing. This causes the HTML wrappings on the comment to be malformed, allowing the javscript injection.
      
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.11
  - [ ] GIF Walkthrough: ![WP 4.2 xss comment gif](https://github.com/ramonpetgrave64/Cybersecurity-University-Week-7-Wordpress/blob/master/xss%20comment.gif?raw=true)
  - [ ] Steps to recreate: 
  - Enter the comment below, with the 64kb of filler text (64*1024 characters). 
  - ``` <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a> ```
  - [ ] Affected source code:
    - [Changes in branches/4.2 [32300:32307]](https://core.trac.wordpress.org/changeset?sfp_email=&sfph_mail=&reponame=&new=32307%40branches%2F4.2&old=32300%40branches%2F4.2)
    
2. WordPress 4.2 - Posting XSS, CVE 2015-5622
  - [ ] Summary: Stored XSS possible with a user with posting privileges. The user puts the malformed shortcode into the post's text editor. The javascript is loaded when the post is viewed.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: ![WP 4.2 xss post gif](https://github.com/ramonpetgrave64/Cybersecurity-University-Week-7-Wordpress/blob/master/xss%20post.gif?raw=true)
  - [ ] Steps to recreate: 
    - Create a user with posting privileges. Create a new post and eneter the code below into the post's text editor, rather than the visual editor. Publish and view the post.
    - ```<a href="[caption code=">]</a><a title=" onmouseover=alert('XSS')  ">link</a>```
    - Wordpress presents the post as ```<a href="&lt;/a&gt;&lt;a title=" onmouseover="alert('XSS')" "="">link</a>```
  
  - [ ] Affected source code:
    - [Changeset 33359](https://core.trac.wordpress.org/changeset/33359)
    
3. Wordpress 4.2 - Large File Upload XSS, CVE 2017-9061
  - [ ] Summary: This XSS attack is carried out when attempting to upload a file that exceeds a file-size limit. The script is put file's name. When the file-size limit error is triggered, WordPress outputs on the page an error message containing the file's name, without escaping or sanitizing.
    - Vulnerability types:
    - Tested in version: 4.2
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: ![WP 4.2 xss file upload gif](https://raw.githubusercontent.com/ramonpetgrave64/Cybersecurity-University-Week-7-Wordpress/master/xss%20file%20upload.gif?token=Ae5bC6NqBSD9BZVkEPhxFOmK20waq-Niks5b55qswA%3D%3D)
  - [ ] Steps to recreate: 
    - Get a file that is too large for the WordPress site to upload, e.g. a 10MB file. Rename the file to something like below and upload through the administration page's ```Media -> Add New'''
    - ``` my too big file<img src=x onerror=alert(1)>.png```
  - [ ] Affected source code: 
    - [wp-includes/script-loader.php](https://core.trac.wordpress.org/changeset/37375/branches/4.2/src/wp-includes/script-loader.php?contextall=1&old=32211&old_path=%2Ftrunk%2Fsrc%2Fwp-includes%2Fscript-loader.php)
    - [wp-includes/js/plupload/handlers.js](https://core.trac.wordpress.org/changeset/40742/branches/4.2/src/wp-includes/js/plupload/handlers.js?old=31690&old_path=trunk%2Fsrc%2Fwp-includes%2Fjs%2Fplupload%2Fhandlers.js)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

On Windows 10, I had trouble setting up the WPDistillery. Posts would create, but attempting to navigate to them would result in 404.
I got around this by proceeding through http://wpdistillery.vm/wp-admin/setup-config.php

## License

    Copyright [2018] [Ramon Petgrave]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
