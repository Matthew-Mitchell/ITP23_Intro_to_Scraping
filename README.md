```python
from selenium import webdriver
import time
import pandas
import numpy as np
from bs4 import BeautifulSoup
```

## Selenium! 

https://www.selenium.dev/selenium/docs/api/py/


### Browser Drivers:

https://chromedriver.chromium.org/downloads

https://github.com/mozilla/geckodriver

### Launch!


```python
geckoDriverPath = '/Users/matthewmitchell/Documents/Projects/Tools/Python/Scraping/geckodriver'
driver = webdriver.Firefox(executable_path=geckoDriverPath)
```


```python
driver.get("https://itp.nyu.edu/camp2023/")
```

## XPath Selections Are Your Friend!

![image.png](attachment:image.png)


```python
div = 
button = 

```

## Beautiful Soup


```python
cur_html = driver.page_source
```


```python
soup = BeautifulSoup(cur_html)
print(soup.prettify())
```

    <html lang="en">
     <head>
      <meta charset="utf-8"/>
      <meta content="initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" name="viewport"/>
      <meta content="width=device-width, initial-scale=1" name="viewport"/>
      <title>
       About - ITP Camp 2023
      </title>
      <base href="https://itp.nyu.edu/camp2023/"/>
      <!--    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css">-->
      <link href="https://itp.nyu.edu/camp2023/css/style.less" rel="stylesheet/less" type="text/css"/>
      <style id="less:camp2023-css-style" type="text/css">
       /*
    
    @red: #ED303C;
    @yellow: #EDC951;
    @light_yellow: #e9ffb5; //#f8f6b5;
    @green: #0080A0;
    @light_green: #d8ffb5;
    @sky_blue: #FF9C5B;
    @blue: #3ecad4;
    @light_gray: #dddddd;
    @dark_gray: #888888;
    
    @purple: #d549da;
    @pink: #e33880;
    @orange: #f0c220;
    @redorange: #f09520;
    
    @light_purple: #edb8ef;
    @light_pink: #eeaec9;
    @light_orange: #f3e09f;
    
    */
    @font-face {
      font-family: Montserrat;
      src: url("https://itp.nyu.edu/camp2023/fonts/Montserrat-VariableFont_wght.ttf");
    }
    body {
      margin: 0px;
      background: white;
      font-family: 'Montserrat', 'sans-serif';
    }
    h1,
    h2,
    h3,
    h4,
    h5,
    h6 {
      font-weight: normal;
      /* color: @dark_gray; YEN: To fixed contrast errors */
    }
    h1 a,
    h2 a,
    h3 a,
    h4 a,
    h5 a,
    h6 a {
      font-weight: normal;
      color: #888888;
    }
    h1 a:hover,
    h2 a:hover,
    h3 a:hover,
    h4 a:hover,
    h5 a:hover,
    h6 a:hover {
      color: #910091;
      /* Changed by Kate */
    }
    h1 {
      font-size: 36px;
      font-family: 'Montserrat';
      margin-top: 10px;
    }
    h1 span.headerTag {
      font-family: 'Montserrat', 'sans-serif';
      font-size: 10px;
      background: #ED303C;
      color: white;
      padding: 3px 5px;
      border-radius: 8px;
      position: relative;
      top: -4px;
      text-transform: uppercase;
    }
    a {
      text-decoration: none;
      font-weight: bold;
      color: #7F0799;
    }
    a.button {
      background: #7F0799;
      color: white;
      border-radius: 8px;
      padding: 5px 8px;
      cursor: pointer;
    }
    a:hover {
      text-decoration: underline;
      color: #910091;
      /* Changed by Kate */
    }
    span.toggle {
      border: 2px solid #7F0799;
      color: #7F0799;
      padding: 3px 5px;
      cursor: pointer;
      text-align: center;
    }
    span.toggleLeft {
      border-right-width: 1px;
      border-radius: 8px 0px 0px 8px;
    }
    span.toggleCenter {
      border-left-width: 1px;
      border-right-width: 1px;
      border-radius: 0px;
    }
    span.toggleRight {
      border-left-width: 1px;
      border-radius: 0px 8px 8px 0px;
    }
    span.toggleOn {
      background: #7F0799;
      color: white;
    }
    span.bullet {
      color: #888888;
      /* changed by jiwon */
    }
    span.answerYes {
      color: #6FB66F;
      font-weight: bold;
    }
    span.answerNo {
      color: #ED303C;
      font-weight: bold;
    }
    .field {
      margin-bottom: 1rem;
    }
    input,
    select,
    textarea {
      font-family: 'Montserrat', 'sans-serif';
      font-size: 16px;
    }
    input[type=text],
    input[type=password],
    textarea,
    select {
      border-radius: 6px;
      padding: 3px 8px;
      border: 2px solid #F1F2F2;
      background: white;
    }
    input[type=submit],
    input.button,
    button {
      font-family: 'Montserrat', 'sans-serif';
      font-size: 16px;
      font-weight: bold;
      background: #ED303C;
      /* color: white; Yen: fix contrast */
      border-radius: 8px;
      padding: 5px 8px;
      margin: 0px;
      border: 0px;
      cursor: pointer;
    }
    hr {
      border: 0px;
      border-top: 2px solid #ffb599;
      clear: both;
    }
    div.clear {
      clear: both;
    }
    div.header {
      background: #F1F2F2;
    }
    div.header div.headerInner {
      max-width: 1024px;
      margin: 0px auto;
    }
    div.header h1 {
      font-family: 'Montserrat';
      font-weight: normal;
      margin: 0px 0px 0px 25px;
      font-size: 36px;
      float: left;
      height: 70px;
      line-height: 70px;
      overflow: visible;
    }
    div.header h1 img {
      position: relative;
      left: -25px;
      top: -5px;
    }
    div.header h1 a {
      color: white;
      font-weight: normal;
    }
    div.header ul {
      float: right;
      margin: 0px 25px 0px 0px;
      height: 70px;
      line-height: 70px;
      white-space: nowrap;
    }
    div.header ul li {
      display: inline;
      background: white;
      border-radius: 8px;
      padding: 5px 8px;
      margin: 0px;
    }
    div.header ul li.signIn {
      background: #888888;
      /* Changed by Kate */
      padding: 5px 0px 5px 5px;
    }
    div.header ul li.signIn input[type=text],
    div.header ul li.signIn input[type=password] {
      border: 0px;
    }
    div.header ul li.signIn button {
      background-color: #7F0799;
      /* changed by jiwon */
    }
    div.submenu {
      background: #F1F2F2;
      padding: 10px 0px;
    }
    div.submenu div.submenuInner {
      max-width: 900px;
      margin: 0px auto;
      padding-left: 124px;
    }
    div.submenu ul {
      margin: 0px 0px 0px 50px;
      padding: 0px;
      float: left;
    }
    div.submenu ul li {
      display: inline;
      margin: 0px;
    }
    div.submenu ul li a {
      background: white;
      border-radius: 8px;
      padding: 5px 8px;
    }
    div.submenu ul li a:hover {
      background: #7F0799;
      /* changed by jiwon */
      color: white;
      /* changed by jiwon */
    }
    div.submenu ul li a.attend {
      background: #EDC951;
      color: #ED303C;
    }
    div.submenu ul li a.attend:hover {
      background: #99d199;
    }
    div.submenu ul.rightMenu {
      float: right;
      margin: 0px 50px 0px 0px;
    }
    div.notification {
      background: #EDC951;
      padding: 10px 0px;
    }
    div.notification div.notificationInner {
      max-width: 1024px;
      margin: 0px auto;
    }
    div.notification div.notificationInner p {
      text-align: center;
      margin: 5px 100px;
    }
    div.content {
      max-width: 924px;
      margin: 0px auto;
      padding: 60px 50px;
    }
    div.content div.bigAlert {
      border: 2px solid #888888;
      /* Changed by Kate */
      border-radius: 30px;
      text-align: center;
      padding: 5px 30px;
      margin-top: 20px;
    }
    div.content div.bigAlert p.applyButton a {
      background: #6FB66F;
      color: white;
      border-radius: 20px;
      font-size: 16px;
      padding: 5px 12px;
    }
    div.content div.campEnded {
      background: #ffb599;
      border-radius: 4px;
      text-align: center;
      padding: 5px 10px;
      margin-bottom: 10px;
    }
    div.content div.campEnded p {
      margin: 0px;
    }
    div.content div.leftContent {
      float: left;
      width: 650px;
      margin-bottom: 100px;
    }
    div.content div.leftContent h1 {
      font-size: 30px;
      font-family: 'Montserrat', 'sans-serif';
    }
    div.content div.leftContent p.averageRating {
      font-size: 18px;
    }
    div.content div.leftContent p.averageRating span.rating {
      font-size: 36px;
    }
    div.content div.leftContent span.rating {
      color: #ED303C;
      font-weight: bold;
    }
    div.content div.leftContent p.searchBar {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 0px;
    }
    div.content div.leftContent p.searchBar input {
      width: 630px;
    }
    div.content div.leftContent p.searchBar input.calendar {
      width: 510px;
    }
    div.content div.leftContent p.searchBar .listGridToggle {
      display: flex;
    }
    div.content div.leftContent div.sessionInfo {
      background: #ffeecc;
      padding: 5px 10px;
      margin-bottom: 30px;
      font-size: 13px;
    }
    div.content div.leftContent div.sessionInfo p {
      margin: 0px;
    }
    div.content div.leftContent div.sessionInfo p.sessionLeaders span.delete {
      display: inline-block;
      text-align: center;
      vertical-align: center;
      position: relative;
      width: 15px;
      height: 15px;
      font-weight: bold;
      color: #ED303C;
      background: white;
      border-radius: 10px;
      line-height: 15px;
      cursor: pointer;
      margin-left: 2px;
    }
    div.content div.leftContent div.sessionInfo p.sessionLeaders span.delete:hover {
      color: white;
      background: #ED303C;
    }
    div.content div.leftContent div.sessionInfo hr {
      border-top: 1px solid white;
      margin: 5px -10px;
    }
    div.content div.leftContent div.blogPost {
      margin-bottom: 50px;
    }
    div.content div.leftContent div.blogPost h2 {
      margin-bottom: 2px;
    }
    div.content div.leftContent div.blogPost p.blogPostInfo {
      margin-top: 0px;
      font-size: 13px;
    }
    div.content div.leftContent div.blogPost p.blogComments {
      font-size: 12px;
    }
    div.content div.leftContent div.feedbackItem {
      border: 2px solid #c3eff2;
      padding: 5px 8px;
      border-radius: 12px;
      margin-bottom: 10px;
    }
    div.content div.leftContent div.feedbackItem p {
      margin: 0px;
    }
    div.content div.leftContent div.feedbackItem p.rating {
      font-size: 16px;
      font-weight: bold;
      color: #ED303C;
    }
    div.content div.leftContent div.feedbackItem p.feedback {
      font-size: 16px;
    }
    div.content div.leftContent div.feedbackItem p.feedback a {
      font-weight: normal;
      color: black;
    }
    div.content div.leftContent div.feedbackItem p.feedback a:hover {
      color: #7F0799;
    }
    div.content div.leftContent div.feedbackItem p.info {
      font-size: 12px;
    }
    div.content div.leftContent div.feedbackItem p.feedbackComments {
      margin: 8px 0px;
      font-size: 12px;
    }
    div.content div.leftContent div.expandableHints {
      border: 2px solid #888888;
      /* Changed by Kate */
      border-radius: 16px;
      padding: 0px 15px;
      margin-bottom: 10px;
      font-size: 12px;
    }
    div.content div.leftContent div.expandableHints h2 {
      margin: 5px 0px 0px 0px;
    }
    div.content div.leftContent div.expandableHints div.expandableContent {
      display: none;
    }
    div.content div.leftContent img.aboutProfileImage {
      float: right;
      border: 2px solid #F1F2F2;
      border-radius: 8px;
      margin: 0px 0px 10px 10px;
    }
    div.content div.leftContent img.sessionImage {
      float: right;
      border: 2px solid #F1F2F2;
      border-radius: 8px;
      margin: 0px 0px 10px 10px;
    }
    div.content div.leftContent img.projectImage {
      float: right;
      border: 2px solid #F1F2F2;
      border-radius: 8px;
      margin: 0px 0px 10px 10px;
    }
    div.content div.leftContent div.rateSession {
      border: 2px solid #ED303C;
      border-radius: 16px;
      padding: 8px 15px 0px 15px;
      margin-bottom: 10px;
      font-size: 12px;
    }
    div.content div.rightSidebar {
      float: right;
      width: 250px;
      font-size: 13px;
    }
    div.content div.rightSidebar div.sidebarBlock {
      border: 2px solid #888888;
      /* Changed by Kate */
      border-radius: 16px;
      padding: 0px 15px;
      margin-bottom: 10px;
    }
    div.content div.rightSidebar div.sidebarBlock h2 {
      font-size: 16px;
      font-weight: bold;
    }
    div.content div.rightSidebar div.sidebarBlock h2 a {
      font-weight: bold;
      color: #7F0799;
    }
    div.content div.rightSidebar div.sidebarBlock li {
      margin-bottom: 10px;
    }
    div.content div.rightSidebar div.sidebarBlock p.notes {
      font-size: 10px;
      color: #888888;
    }
    div.content div.rightSidebar div.sidebarBlock p input {
      width: 196px;
    }
    div.content div.rightSidebar div.sidebarBlock form p input {
      width: 216px;
    }
    div.content div.rightSidebar div.sidebarBlock img {
      max-width: 216px;
    }
    div.content div.rightSidebar div.locationMapBlock {
      border: 0px;
      padding: 0px;
      height: 240px;
      border-radius: 0px;
    }
    div.content div.rightSidebar div.locationMapBlock p {
      margin: 0px;
    }
    div.content div.rightSidebar div.locationMapBlock p img {
      border-radius: 16px;
      border: 5px solid #888888;
      /* Changed by Kate */
    }
    div.content div.rightSidebar div.sidebarUserProfile {
      padding: 3px;
      margin-bottom: 5px;
    }
    div.content div.rightSidebar div.sidebarUserProfile p {
      margin: 0px;
      line-height: 25px;
    }
    div.content div.rightSidebar div.sidebarUserProfile img {
      vertical-align: middle;
      margin-right: 5px;
      border-radius: 8px;
    }
    div.content div.rightSidebar div.sidebarUserProfile span.delete {
      display: inline-block;
      text-align: center;
      vertical-align: center;
      position: relative;
      width: 15px;
      height: 15px;
      font-weight: bold;
      color: #ED303C;
      background: white;
      border-radius: 10px;
      line-height: 15px;
      cursor: pointer;
      margin-left: 2px;
    }
    div.content div.rightSidebar div.sidebarUserProfile span.delete:hover {
      color: white;
      background: #ED303C;
    }
    div.content div.rightSidebar p.sidebarHeader {
      font-size: 22px;
      font-family: 'Montserrat';
      margin: 20px 0px 3px 0px;
      text-align: center;
      color: #888888;
    }
    div.content div.rightSidebar p.button {
      text-align: center;
      margin: 0px 0px 10px 0px;
    }
    div.content div.rightSidebar p.button a {
      background-color: #7F0799;
      border-radius: 16px;
      padding: 10px 15px;
      display: block;
      font-size: 20px;
      color: white;
    }
    div.content div.rightSidebar div.buttonWithoutAnchor {
      text-align: center;
      margin: 0px 0px 10px 0px;
      background-color: #7F0799;
      border-radius: 16px;
      padding: 10px 15px;
      display: block;
      font-size: 20px;
      color: white;
      cursor: pointer;
      font-weight: bold;
    }
    div.content div.rightSidebar div.buttonWithoutAnchor p.small {
      font-size: 12px;
      margin: 0px;
    }
    div.content div.rightSidebar div.buttonWithoutAnchor a {
      color: white;
    }
    div.content div.rightSidebar div.disabledButtonWithoutAnchor {
      text-align: center;
      margin: 0px 0px 10px 0px;
      background-color: #F1F2F2;
      border-radius: 16px;
      padding: 10px 15px;
      display: block;
      font-size: 20px;
      color: white;
      cursor: pointer;
      font-weight: bold;
    }
    div.content div.rightSidebar div.disabledButtonWithoutAnchor p.small {
      font-size: 12px;
      margin: 0px;
    }
    div.content div.rightSidebar div#cancelRSVP {
      background: #ED303C;
    }
    div.content div.rightSidebar div#cancelRSVPWaitlist,
    div.content div.rightSidebar div#cancelFollow {
      background: #910091;
      /* Changed by Kate */
    }
    div.sessionInfoBlock {
      border-radius: 16px;
      margin-bottom: 10px;
      border: 5px solid #888888;
      /* Changed by Kate */
      text-align: center;
      padding-top: 10px;
      padding-bottom: 10px;
    }
    div.sessionInfoBlock p {
      margin: 2px 0px;
    }
    div.sessionInfoBlock p.sessionDay {
      font-weight: bold;
      font-size: 18px;
    }
    div.sessionInfoBlock p.sessionTime {
      font-size: 16px;
    }
    div.sessionInfoBlock p.sessionLocation {
      font-size: 16px;
    }
    div.sessionInfoBlock p.sessionRSVPs {
      font-size: 11px;
    }
    div.contentTabs {
      border-bottom: 2px solid #7F0799;
    }
    div.contentTabs div.tab {
      display: inline-block;
      border: 2px solid #7F0799;
      border-bottom-width: 0px;
      color: #7F0799;
      border-radius: 8px 8px 0px 0px;
      font-size: 12px;
      font-weight: bold;
      padding: 3px 7px;
      cursor: pointer;
    }
    div.contentTabs div.activeTab {
      background: #7F0799;
      color: white;
    }
    div.sessionList h2 {
      font-size: 22px;
      font-family: 'Montserrat';
      color: #888888;
      margin-bottom: 2px;
    }
    div.sessionList p.note {
      margin-top: 50px;
      font-size: 11px;
      opacity: 0.35;
    }
    div.sessionListItem {
      border: 2px solid #c3eff2;
      border-radius: 16px;
      padding: 3px 10px 5px 10px;
      margin-bottom: 10px;
      overflow-x: hidden;
    }
    div.sessionListItem div.sessionVoteButton {
      float: left;
      width: 50px;
      background: #ED303C;
      border-radius: 10px;
      color: white;
      cursor: pointer;
      text-align: center;
      margin-right: 5px;
      margin-top: 2px;
      margin-left: -3px;
      font-size: 11px;
      font-weight: bold;
      position: relative;
      vertical-align: middle;
      padding-top: 14px;
      height: 30px;
    }
    div.sessionListItem div.votedFor {
      background: #7F0799;
    }
    div.sessionListItem div.sessionLeftColumn {
      float: left;
      width: 405px;
    }
    div.sessionListItem div.sessionVoteLeftColumn {
      float: left;
      width: 350px;
    }
    div.sessionListItem div.sessionRightColumn {
      float: right;
      width: 220px;
      margin-top: 3px;
    }
    div.sessionListItem div.sessionRightColumn p {
      text-align: right;
    }
    div.sessionListItem h3 {
      margin: 0px;
    }
    div.sessionListItem h3 span.sessionTime {
      color: black;
      font-size: 13px;
    }
    div.sessionListItem p {
      margin: 0px;
      font-size: 12px;
    }
    div.sessionListItem p.sessionTime {
      font-weight: bold;
    }
    div.sessionListItem p.sessionInfo .overlapping {
      color: #ED303C;
      font-weight: bold;
    }
    div.sessionListItem p.sessionVotes {
      color: #ED303C;
      font-size: 15px;
    }
    div.sessionListItem p.rateSession {
      padding: 10px 0px;
    }
    div.sessionListItemNew {
      border: 2px solid #00FFFF;
      /* Changed by Kate */
    }
    div.sessionListItemRsvp {
      border: 2px solid #910091;
      /* Changed by Kate */
    }
    div.sessionListItemWaitlist {
      border: 2px solid #00FFA4;
      /* Changed by Kate */
    }
    div.sessionListItemDraft {
      background-color: #DDD;
      /* Changed by Daniel */
      border: 2px solid transparent;
    }
    div.sessionListItemDraft h3 a {
      font-style: italic;
    }
    div.projectListItem {
      border: 2px solid #c3eff2;
      border-radius: 12px;
      padding: 3px 4px 5px 9px;
      margin-bottom: 5px;
    }
    div.projectListItem h3 {
      margin: 0px;
    }
    div.projectListItem h3 a {
      color: #7F0799;
    }
    div.projectListItem p {
      margin: 0px;
      font-size: 11px;
    }
    div.userListItem {
      border: 2px solid #c3eff2;
      border-radius: 12px;
      padding: 5px 4px 3px 4px;
      margin-bottom: 5px;
      background-color: white;
      z-index: -100;
    }
    div.userListItem p.profileImage {
      margin: 0px;
      float: left;
    }
    div.userListItem p.profileInfo {
      margin: 0px 0px 0px 5px;
      line-height: 100%;
      position: relative;
      top: 2px;
    }
    div.userListItem p.profileInfo span.shortAbout {
      color: #888888;
      font-size: 11px;
    }
    div.userListItem img {
      border-radius: 8px;
      position: relative;
      top: -1px;
      vertical-align: middle;
      margin-right: 5px;
    }
    div.userListItem a.button {
      font-size: 11px;
      padding: 2px 5px;
      display: inline-block;
      margin: 3px 0px;
    }
    div.comments div.addCommentWrapper {
      min-height: 40px;
    }
    div.comments a.button {
      background: #7F0799;
      border-radius: 8px;
      color: white;
      padding: 3px 5px;
      font-size: 12px;
      cursor: pointer;
    }
    div.comments a.cancelButton {
      background: #F1F2F2;
      border-radius: 8px;
      color: white;
      padding: 3px 5px;
      font-size: 12px;
      cursor: pointer;
    }
    div.comments div.commentForm {
      display: none;
    }
    div.comments div.commentForm p {
      margin: 0px;
    }
    div.comments div.commentForm textarea {
      width: 630px;
      font-size: 14px;
      height: 100px;
    }
    div.comments div.commentListItem {
      margin-top: 30px;
      margin-bottom: 30px;
    }
    div.comments div.commentListItem a.atReply {
      font-weight: normal;
      font-size: 12px;
      text-transform: uppercase;
    }
    div.comments div.commentListItem p {
      margin: 0px;
      font-size: 14px;
    }
    div.comments div.commentListItem p.commentInfo {
      font-size: 12px;
      margin-bottom: 2px;
      color: #888888;
      /* changed by jiwon */
    }
    div.comments div.commentListItem div.commentForm {
      margin-top: 10px;
    }
    div.comments div.commentListItem p.addComment {
      margin-top: 5px;
    }
    a#showHidePreviousSessions {
      display: block;
      text-align: center;
      font-size: 11px;
      color: #7F0799;
      background: #eeeeee;
    }
    table.calendar {
      border-spacing: 1px;
      border-collapse: separate;
      font-size: 12px;
    }
    table.calendar td {
      width: 92px;
      padding: 0px;
      border-radius: 4px;
      border: 1px solid black;
      /* Changed by Kate */
      vertical-align: top;
      height: 60px;
    }
    table.calendar td p.date {
      margin: 0px;
      background: black;
      /* Changed by Kate */
      color: white;
      font-size: 10px;
      text-transform: uppercase;
      text-align: center;
      padding: 3px 0px;
    }
    table.calendar td div.sessionGridItem {
      position: relative;
      font-size: 10px;
      max-height: 64px;
      margin: 2px;
      overflow: hidden;
    }
    table.calendar td div.sessionGridItem div.sessionGridItemInner {
      border-radius: 4px;
      border: 2px solid #00FFFF;
      /* Changed by jiwon */
      padding: 2px 4px;
      background: white;
      max-height: 56px;
      max-width: 76px;
      overflow-x: hidden;
    }
    table.calendar td div.sessionGridItem div.sessionGridItemInner .overlapping {
      color: #ED303C;
      font-weight: bold;
    }
    table.calendar td div.sessionGridItem div.sessionGridItemInner a.sessionGridLocation {
      color: #888888;
      /* Changed by Kate */
      font-weight: normal;
    }
    table.calendar td div.sessionGridItem div.sessionGridItemInner .session-title {
      display: block;
      margin-top: 0.25rem;
    }
    table.calendar td div.sessionGridItemNew div.sessionGridItemInner {
      border: rgba(0, 255, 255, 0.5) /* changed by jiwon */;
    }
    table.calendar td div.sessionGridItemDraft {
      /* changed by Daniel */
    }
    table.calendar td div.sessionGridItemDraft div.sessionGridItemInner {
      background-color: #DDD;
      border-color: transparent;
    }
    table.calendar td div.sessionGridItemRsvp div.sessionGridItemInner {
      border: 2px solid #910091;
      /* Changed by Kate */
    }
    table.calendar td div.sessionGridItemWaitlist div.sessionGridItemInner {
      border: 2px solid #00FFA4;
      /* Changed by Kate */
    }
    table.calendar td div.sessionGridItem:hover {
      z-index: 100;
      overflow: visible;
    }
    table.calendar td div.sessionGridItem:hover div.sessionGridItemInner:hover {
      max-height: 1000px;
    }
    table.calendar td.grayDay {
      border: 1px solid white;
    }
    table.calendar td.grayDay p.date {
      background: white;
    }
    table.calendar tr.dayOfWeek td {
      border: 1px solid #7F0799;
      /* changed by jiwon */
      background: transparent;
      /* changed by jiwon */
      color: #7F0799;
      /* Changed by Kate */
      text-align: center;
      padding: 3px 0px;
      height: auto;
    }
    table.calendar tr.dayOfWeek td.currentDay {
      background: #00FFFF;
      /* Changed by Kate */
      color: white;
      /* Changed by Kate */
    }
    div.noneFound {
      display: none;
    }
    div.deletedObject {
      color: white;
      background: #ED303C;
      border-radius: 4px;
      padding: 3px 5px;
      margin-bottom: 10px;
    }
    div.deletedObject p {
      margin: 0px;
    }
    form label,
    form .label {
      font-weight: bold;
      margin-bottom: 3px;
    }
    form label .required,
    form .label .required {
      margin-left: 0.25rem;
      color: #ED303C;
      font-size: small;
      font-style: italic;
    }
    form label .required::before,
    form .label .required::before {
      content: "(";
    }
    form label .required::after,
    form .label .required::after {
      content: ")";
    }
    form p.formElement {
      margin: 1px 0px;
    }
    form p.formElement input {
      width: 630px;
    }
    form p.formElement input.datePicker {
      width: 300px;
      margin-right: 10px;
      display: inline-block;
    }
    form p.formElement input.timePicker {
      width: 300px;
      display: inline-block;
    }
    form p.formElement textarea {
      margin: 0px;
      width: 630px;
      height: 200px;
      font-size: 16px;
    }
    form p.formElementDateTimeDate {
      display: inline-block;
    }
    form p.formElementDateTimeTime {
      display: inline-block;
    }
    form p.note {
      font-size: 12px;
      /* color: @dark_gray; Yen: to fix contrast*/
      margin-top: 1px;
    }
    form p.submit a.cancel {
      margin-left: 20px;
    }
    form p.submit small {
      font-size: 10px;
      color: #888888;
    }
    div.noPermission {
      margin-top: 100px;
      margin-bottom: 250px;
      text-align: center;
    }
    div.noPermission h1 {
      color: #ED303C;
      font-size: 150px;
      margin: 0px;
    }
    div.noPermission p {
      margin: -30px 0px 0px 0px;
    }
    div.notFound {
      margin-top: 100px;
      margin-bottom: 250px;
      text-align: center;
    }
    div.notFound h1 {
      color: #ED303C;
      font-size: 150px;
      margin: 0px;
    }
    div.notFound p {
      margin: -30px 0px 0px 0px;
    }
    p.userDidDoThings {
      font-size: 10px;
    }
    span.userDidPay,
    span.userDidDoThing {
      background: #7F0799;
      color: white;
      border-radius: 8px;
      padding: 2px 5px;
      font-size: 10px;
      font-weight: bold;
    }
    span.userDidNotPay,
    span.userDidNotDoThing {
      background: #ED303C;
      color: white;
      border-radius: 8px;
      padding: 2px 5px;
      font-size: 10px;
      font-weight: bold;
    }
    span.sessionTag {
      color: white;
      border-radius: 8px;
      padding: 3px 4px;
      font-size: 10px;
      font-weight: bold;
      position: relative;
      top: -2px;
      font-family: 'Montserrat', 'sans-serif';
    }
    span.sessionNew {
      background: #EDC951;
      color: #ED303C;
    }
    span.sessionRSVPed {
      background: #910091;
      /* Changed by Kate */
    }
    span.sessionWaitlisted {
      background: #00FFA4;
      /* Changed by Kate */
    }
    span.userTag {
      color: white;
      border-radius: 8px;
      padding: 3px 4px;
      font-size: 10px;
      font-weight: bold;
      position: relative;
      top: -2px;
      font-family: 'Montserrat', 'sans-serif';
      white-space: nowrap;
    }
    span.userCamper {
      background: #00FFFF;
      /* Changed by Kate */
    }
    span.userLeader {
      background: #00FFA4;
      /* Changed by Kate */
    }
    span.userCounselor {
      background: #910091;
      /* Changed by Kate */
    }
    span.userStaff {
      background: black;
      /* Changed by Kate */
    }
    span.userInstigator {
      background: #f09520;
      /* Changed by Kate */
    }
    hr.footer {
      margin-top: 100px;
      border-top: 2px solid #F1F2F2;
    }
    div.footer p {
      text-align: center;
      /* color: #999999; YEN: To fixed contrast errors*/
    }
    div.footerFeedback {
      text-align: center;
      margin-top: 25px;
      margin-bottom: 100px;
    }
    div.footerFeedback div.footerFeedbackInner {
      display: none;
      text-align: left;
      background: #eeeeee;
      border-radius: 12px;
      max-width: 700px;
      padding: 20px 40px 20px 40px;
      margin: 0px auto;
    }
    div.footerFeedback div.footerFeedbackInner textarea {
      width: 680px;
      height: 100px;
    }
    div.footerFeedback div.footerFeedbackInner p.note {
      font-size: 12px;
    }
    div.stats {
      background-color: #efefef;
      max-width: 924px;
      margin: 0px auto;
      padding: 20px 50px;
    }
    ul.applications li {
      margin-bottom: 20px;
    }
    ul.applications li small {
      color: #888888;
      font-size: 10px;
      padding-left: 20px;
    }
    ul.applications span.instigator {
      font-size: 10px;
      font-weight: bold;
      color: #00FFFF;
      /* Changed by Kate */
    }
    table.applications td {
      padding: 0.5rem;
      vertical-align: top;
    }
    span.applicationStatusButton {
      background: black;
      /* Changed by Kate */
      color: rgba(255, 255, 255, 0.75);
      border-radius: 12px;
      font-size: 13px;
      font-weight: bold;
      padding: 5px 8px;
      cursor: pointer;
      display: block;
      text-align: center;
      margin-bottom: 10px;
    }
    span.applicationStatusButtonActive {
      background: #00FFA4;
      /* Changed by Kate */
      color: white;
    }
    span.paymentModeButton {
      background: #ED303C;
      color: rgba(255, 255, 255, 0.75);
      border-radius: 12px;
      font-size: 13px;
      font-weight: bold;
      padding: 5px 8px;
      cursor: pointer;
      display: block;
      text-align: center;
      margin-bottom: 10px;
    }
    span.paymentModeButtonActive {
      background: #00FFA4;
      /* Changed by Kate */
      color: white;
    }
    .invisible {
      visibility: hidden;
    }
      </style>
      <link href="https://itp.nyu.edu/camp2023/css/social_genius_style.less" rel="stylesheet/less" type="text/css"/>
      <style id="less:camp2023-css-social_genius_style" type="text/css">
       /*
    
    @red: #ED303C;
    @yellow: #EDC951;
    @light_yellow: #e9ffb5; //#f8f6b5;
    @green: #0080A0;
    @light_green: #d8ffb5;
    @sky_blue: #FF9C5B;
    @blue: #3ecad4;
    @light_gray: #dddddd;
    @dark_gray: #888888;
    
    @purple: #d549da;
    @pink: #e33880;
    @orange: #f0c220;
    @redorange: #f09520;
    
    @light_purple: #edb8ef;
    @light_pink: #eeaec9;
    @light_orange: #f3e09f;
    
    */
    div.socialGeniusTimer {
      width: 650px;
      height: 60px;
      margin-bottom: 5px;
    }
    div.socialGeniusTimer div.timer {
      position: relative;
      background-color: #6FB66F;
      float: left;
      width: 100px;
      height: 60px;
      text-align: center;
      color: white;
    }
    div.socialGeniusTimer div.timer p {
      position: absolute;
      margin: 0px;
      top: 50%;
      width: 100%;
      transform: translateY(-50%);
      font-size: 11px;
      font-weight: bold;
    }
    div.socialGeniusTimer div.timer p span.timeRemaining {
      font-size: 24px;
    }
    div.socialGeniusTimer div.timerBarWrapper {
      border-radius: 10px;
      width: 400px;
      float: left;
      height: 60px;
    }
    div.socialGeniusTimer div.timerBarWrapper div.timerBar {
      background-color: #ED303C;
      height: 60px;
      width: 200px;
    }
    div.socialGeniusGameGrid {
      position: relative;
      clear: both;
      width: 650px;
    }
    div.socialGeniusGameGrid div.readyOverlay {
      position: absolute;
      width: 625px;
      height: 520px;
      top: 0px;
      left: 0px;
      background-color: #c3eff2;
    }
    div.socialGeniusGameGrid div.readyOverlay div.inner {
      position: absolute;
      top: 50%;
      width: 425px;
      transform: translateY(-50%);
      padding: 0px 100px;
    }
    div.socialGeniusGameGrid div.readyOverlay div.inner p {
      text-align: center;
    }
    div.socialGeniusGameGrid div.readyOverlay div.inner p.help {
      font-size: 13px;
    }
    div.socialGeniusGameGrid div.readyOverlay div.inner p.title {
      font-size: 16px;
      font-weight: bold;
    }
    div.socialGeniusGameGrid div.readyOverlay div.inner p.playButton {
      margin-top: 50px;
    }
    div.socialGeniusGameGrid div.readyOverlay div.inner p.playButton span#playButton {
      background-color: #ED303C;
      border-radius: 20px;
      padding: 10px 20px;
      font-size: 18px;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    div.socialGeniusGameGrid div.winOverlay {
      position: absolute;
      width: 625px;
      height: 520px;
      top: 0px;
      left: 0px;
      background-color: rgba(195, 239, 242, 0.9);
      display: none;
    }
    div.socialGeniusGameGrid div.winOverlay div.inner {
      position: absolute;
      top: 50%;
      width: 425px;
      transform: translateY(-50%);
      padding: 0px 100px;
    }
    div.socialGeniusGameGrid div.winOverlay div.inner p {
      text-align: center;
      font-weight: bold;
    }
    div.socialGeniusGameGrid div.winOverlay div.inner p span.timeRemaining {
      font-size: 24px;
    }
    div.socialGeniusGameGrid div.winOverlay div.inner p.againButton {
      margin-top: 50px;
    }
    div.socialGeniusGameGrid div.winOverlay div.inner p.againButton span.againButton {
      background-color: #ED303C;
      border-radius: 20px;
      padding: 10px 20px;
      font-size: 18px;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    div.socialGeniusGameGrid div.loseOverlay {
      position: absolute;
      width: 625px;
      height: 520px;
      top: 0px;
      left: 0px;
      background-color: #C6FF4C;
      display: none;
    }
    div.socialGeniusGameGrid div.loseOverlay div.inner {
      position: absolute;
      top: 50%;
      width: 425px;
      transform: translateY(-50%);
      padding: 0px 100px;
    }
    div.socialGeniusGameGrid div.loseOverlay div.inner p {
      text-align: center;
      font-weight: bold;
    }
    div.socialGeniusGameGrid div.loseOverlay div.inner p.againButton {
      margin-top: 50px;
    }
    div.socialGeniusGameGrid div.loseOverlay div.inner p.againButton span.againButton {
      background-color: #ED303C;
      border-radius: 20px;
      padding: 10px 20px;
      font-size: 18px;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    div.socialGeniusGameGrid div.square {
      position: relative;
      float: left;
      width: 100px;
      height: 100px;
      background-color: #dddddd;
      text-align: center;
      margin: 0px 5px 5px 0px;
      overflow: hidden;
      cursor: pointer;
    }
    div.socialGeniusGameGrid div.square p {
      margin: 0px;
      text-align: center;
      position: absolute;
      top: 50%;
      width: 100%;
      transform: translateY(-50%);
      font-size: 13px;
      font-weight: bold;
    }
    div.socialGeniusGameGrid div.selected {
      background: #ED303C;
      color: white;
    }
    div.socialGeniusGameGrid div.selected img {
      opacity: 0.5;
    }
    div.socialGeniusGameGrid div.done {
      background: #0080A0;
      color: white;
    }
    div.socialGeniusGameGrid div.done img {
      opacity: 0.5;
    }
    p.highScore {
      font-size: 14px;
    }
    p.highlight {
      background-color: #ffff88;
      background-color: #C6FF4C;
    }
      </style>
      <script src="https://code.jquery.com/jquery-1.11.0.min.js">
      </script>
      <script src="//cdnjs.cloudflare.com/ajax/libs/less.js/3.9.0/less.min.js">
      </script>
      <script src="https://itp.nyu.edu/camp2023/js/libs/jquery.tappable.js">
      </script>
      <script src="https://itp.nyu.edu/camp2023/js/libs/jquery.cookie.js">
      </script>
      <link href="https://itp.nyu.edu/camp2023/js/libs/jqueryui/css/ui-lightness/jquery-ui-1.10.4.custom.min.css" rel="stylesheet"/>
      <script src="https://itp.nyu.edu/camp2023/js/libs/jqueryui/jquery-ui-1.10.4.custom.min.js">
      </script>
      <script src="https://itp.nyu.edu/camp2023/js/libs/pickadate/picker.js">
      </script>
      <script src="https://itp.nyu.edu/camp2023/js/libs/pickadate/picker.date.js">
      </script>
      <script src="https://itp.nyu.edu/camp2023/js/libs/pickadate/picker.time.js">
      </script>
      <link href="https://itp.nyu.edu/camp2023/js/libs/pickadate/themes/classic.css" rel="stylesheet"/>
      <link href="https://itp.nyu.edu/camp2023/js/libs/pickadate/themes/classic.date.css" rel="stylesheet"/>
      <link href="https://itp.nyu.edu/camp2023/js/libs/pickadate/themes/classic.time.css" rel="stylesheet"/>
      <link href="https://fonts.googleapis.com/css?family=Raleway:400,700" rel="stylesheet" type="text/css"/>
      <!--–– YEN: deprecated ––-->
      <link href="https://s3.amazonaws.com/icomoon.io/114779/Socicon/style.css?u8vidh" rel="stylesheet"/>
      <link href="https://cdn.quilljs.com/1.3.6/quill.snow.css" rel="stylesheet"/>
      <link href="https://itp.nyu.edu/camp2023/css/extra.css" rel="stylesheet" type="text/css"/>
      <script type="text/javascript">
       function hideAddressBar() {
                if (!window.location.hash) {
                    if (document.height < window.outerHeight) {
                        document.body.style.height = (window.outerHeight + 50) + 'px';
                    }
                    setTimeout(function () {
                        window.scrollTo(0, 1);
                    }, 50);
                }
            }
    
            window.addEventListener("load", function () {
                if (!window.pageYOffset) {
                    hideAddressBar();
                }
            });
            window.addEventListener("orientationchange", hideAddressBar);
    
            function missingProfileImage(image) {
                image.onerror = "";
                image.src = "images/anon_user_large.png";
                return true;
            }
    
            function missingSessionImage(image) {
                image.onerror = "";
                image.src = "images/anon_session_large.png";
                return true;
            }
    
            function missingProjectImage(image) {
                image.onerror = "";
                image.src = "images/anon_session_large.png";
                return true;
            }
      </script>
     </head>
     <body>
      <div class="headerWrapper">
       <div class="header">
        <div class="headerInner">
         <h1>
          <a href="https://itp.nyu.edu/camp2023">
           <img alt="ITP Camp 2023" height="175" src="images/ITPCamp2023-logo2.png" width="175"/>
          </a>
         </h1>
         <form action="https://itp.nyu.edu/camp2023/auth/login" method="post">
          <ul class="login">
           <li class="signIn">
            <label for="signin_email" hidden="">
             Email Address
            </label>
            <input autocapitalize="none" autocorrect="off" id="signin_email" name="signin_email" placeholder="Email Address" required="" style="width: 150px;" type="email"/>
            <label for="signin_password" hidden="">
             Password
            </label>
            <input id="signin_password" name="signin_password" placeholder="Password" required="" style="width: 100px;" type="password"/>
            <button type="submit">
             Sign In
            </button>
           </li>
           <li>
            <a href="https://itp.nyu.edu/camp2023/lost_password">
             Lost password?
            </a>
           </li>
          </ul>
         </form>
         <div class="clear">
         </div>
        </div>
       </div>
       <div class="submenu">
        <div class="submenuInner">
         <ul>
          <li>
           <a href="">
            Welcome
           </a>
          </li>
          <li>
           <a href="about">
            About
           </a>
          </li>
          <li>
           <a href="dates">
            Dates+Fees
           </a>
          </li>
          <li>
           <a href="calendar">
            Calendar
           </a>
          </li>
          <li>
           <a href="people">
            People
           </a>
          </li>
         </ul>
         <ul class="rightMenu">
         </ul>
         <div class="clear">
         </div>
        </div>
       </div>
      </div>
      <div class="content">
       <h1>
        Welcome to the Un-University!
       </h1>
       <p>
        ITP Camp is a crash course/playground for
        <strong>
         creative and techy people who want to shake things up
        </strong>
        . Every June, we invite non-student makers, artists, musicians, programmers, fabricators, and creatives of all sorts, to join the ITP community to make stuff, hear speakers on the cutting edge, and collaborate with people from diverse disciplines.
       </p>
       <p>
        Camp activities and events in the
        <strong>
         afternoons, evenings, and weekends
        </strong>
        , NYC-time. Some people take the month off and immerse themselves fully in the culture and experience of ITP Camp. Others freelance or work remotely part-time while attending sessions in between. And many of our participants maintain day jobs outside of ITP Camp and join us for the evening activities.
       </p>
       <p>
        ITP was founded and is grounded in the belief that making is fundamental to thinking. Like any summer camp, the atmosphere is playful, cooperative and collaborative but there’s a serious purpose. We’re looking for people who are seriously motivated… to save the world, their industry, their career or just their sanity by being creative; who are dying to make something or just make sense out of what they are doing.
       </p>
       <p>
        The creative charge of ITP Camp comes from the community of participants sharing their ideas, skills, criticisms and passions with each other in small, informal groups. We’re creating a flexible structure, an Un-University, that is responsive and supportive to the group we select. The structure is based on “
        <a href="https://en.wikipedia.org/wiki/Unconference">
         unconferences
        </a>
        " such as
        <a href="http://en.wikipedia.org/wiki/Foo_Camp">
         foocamp
        </a>
        or
        <a href="https://en.wikipedia.org/wiki/BarCamp">
         barcamp
        </a>
        <a href="http://barcamp.org/">
         ,
        </a>
        where presentations and discussions form in response to participants’ interests and projects.
       </p>
       <p>
        Here is an article about what it's like to be at ITP Camp:
        <a href="https://wp.nyu.edu/connect/2018/10/11/unbreakable-makers/">
         Unbreakable Makers
        </a>
        by Anthony Bui and Roland Arnoldt in NYU Connect
       </p>
       <p>
        <img alt="An etched circuit board with the ITP Camp, LEDs, and other components." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_PCB_cropped_300.jpg"/>
       </p>
       <h1>
        People
       </h1>
       <p>
        <strong>
         Campers
        </strong>
        are experienced, motivated and generous people. ITP is a “hands on" place, but prior technical skills are not required. More important than technical skills is the diversity of people and project ideas. Connecting to people outside your field and comfort zone is always a boost for creativity. We think the ITP Camp environment will benefit projects spanning a wide range, including sociological experiments, art installations, new advertising models, health technologies, DIY biology, automatic window shades, cell phone games and dance performances. This is a non-credit program; it’s not designed for full-time students.
       </p>
       <p>
        <span style="color: rgb(26, 26, 26);">
         <img alt="A large group of ITP Campers smiling and waving, outdoors in summer clothing." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_BrooklynBridgeGroup_800_cropped.jpg"/>
        </span>
       </p>
       <p>
        <strong>
         Session Leaders
        </strong>
        can be pretty much anyone. Campers lead sessions. Invited experts lead sessions. ITP faculty lead sessions. Counselors lead sessions. The Un-University provides the opportunity to learn bottom-up, top-down, and side-to-side.
       </p>
       <p>
        <img alt="A session leader gesturing at the front of a group of ITP Campers." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_sessionleader1_400.jpg"/>
        .
        <img alt="A session leader demonstrating the use of a multimeter." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_sessionleader2_400.jpg"/>
       </p>
       <p>
        <strong>
         Counselors
        </strong>
        are your new best friends. The Counselor HQ (available in-person and online!) is a cross between Lucy’s Advice Booth and the Apple Genius Bar and is staffed by knowledgeable recent ITP graduates whose superpowers include electronics, programming, digital fabrication, mechanics, materials, and beyond.
       </p>
       <p>
        <span style="color: rgb(26, 26, 26);">
         <img alt="A group photo of 14 counselors wearing black ITP Camp hoodies with white text." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2019_counselors_800.jpg"/>
        </span>
       </p>
       <h1>
        Sessions
       </h1>
       <p>
        The sessions reflect the interests of the members of the camp. You can see the ideas for sessions starting to form on the schedule. Once you’ve registered, you can suggest ideas for sessions you’d like to see included (for ITP staff to organize, if possible) and schedule a session or two you’d like to lead.
       </p>
       <p>
        ITP camp is intended for busy, working professionals, so you don’t have to come to every session– come to as many or as few as you like. You are asked to RSVP in advance for the sessions that you want to attend because sessions will be added or dropped based on enrollment.
       </p>
       <p>
        Because of its experimental structure, the content of camp changes every year.
        <span style="background-color: transparent;">
         We don’t yet know what will be on the 2023 calendar, but here are some examples from the
        </span>
        <a href="https://itp.nyu.edu/camp2022/calendar">
         200+ sessions that happened in 2022
        </a>
        <span style="background-color: transparent;">
         :
        </span>
       </p>
       <ul>
        <li>
         <span style="background-color: transparent;">
          Artists in Laboratories
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Augmented Reality Poster Design
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          COVID-19 Impact Project: Extracting Stories from Data
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Crash Course in Blockchain and NFTs
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Cultural Appropriation vs. Appreciation
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          DIY PCB and SMD Soldering
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Fabricating and Ideation with Unconventional or Living Materials
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Lighting for Performance and Immersive Experience
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Make A Small Game World: Procedural Generation for 2D
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Motion Prototyping with Digital Tools
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Open Source Software for Textile Design
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Power Walking: create your own power generating shoes
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Sci-Fables: a speculative writing workshop
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Sensing Muscles, Pulse, and Stretch
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Thermochromic Ink Workshop
         </span>
        </li>
        <li>
         <span style="background-color: transparent;">
          Voice: Talking to my machines
         </span>
        </li>
       </ul>
       <p>
        <img alt="A session leader demonstrating a lighting rig while being filmed by an ITP Camp counselor." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_session1_400x267.jpg"/>
        .
        <img alt="An ITP camper presenting code and graphics on a screen in a room with purple lighting.
    " src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_campers2_400.jpg"/>
       </p>
       <h1>
        Projects
       </h1>
       <p>
        Some may develop a fully functioning prototype. Others will come up with new ideas and start to identify tasks and acquire skills for longer-term projects. Your idea might come from your job: for example, your media publishing company is looking to develop ideas to survive technological change. You might already be in the thick of managing new technological possibilities for corporate clients and want a summer camp to apply some of this new thinking to other projects of more artistic or social benefit. In all cases the project is owned by you, we only ask that you be completely open about your work with fellow campers while participating.
       </p>
       <p>
        <img alt="Two campers working on a soldering task together." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_campers1_400.jpg"/>
        .
        <img alt="An session leader presenting the results of the ITP Community Garden sessions." src="https://itp.nyu.edu/camp2023/images/ITPCamp2023_AboutPageImages/ITPCamp2022_CommunityGarden_400.JPG"/>
       </p>
       <h1>
        About ITP
       </h1>
       <p>
        ITP is a two-year graduate program located in the Tisch School of the Arts at New York University whose mission is to explore the imaginative use of communications technologies — how they might augment, improve, and bring delight and art into people’s lives. Perhaps the best way to describe us is as a Center for the Recently Possible. For over 30 years ITP has been a hub of experimentation in art, media and technology.
       </p>
       <p>
        ITP Camp is like ITP Classic put in the blender and squeezed into a month. It is ITP’s test kitchen, its R&amp;D arm, its back of the napkin. It’s the place were we encourage you, our faculty, former students, colleagues, and community to experiment, challenge, and play.
       </p>
       <p>
        ITP’s community will be made accessible to you through Camp activities. The creative atmosphere will help you generate ideas and implement projects and possibly broaden your own network and community of innovators and thinkers.
       </p>
      </div>
      <hr class="footer"/>
      <div class="footer">
       <p>
        Copyright © 2023 ITP Camp — All Rights Reserved
       </p>
       <p>
        <a href="https://itp.nyu.edu">
         <img alt="ITP Logo" height="125" src="images/itp_logo.png" width="125"/>
        </a>
       </p>
       <!--–– YEN: To fix wcag error ––-->
       <p style="font-size: 24px; position: relative; top: -20px;">
        <a aria-label="Link to ITP camp facebook" href="https://www.facebook.com/ItpCamp/">
         <span class="socicon-facebook" style="color: #3e5b98;">
         </span>
        </a>
        <a aria-label="Link to ITP camp twitter" href="https://twitter.com/itpcamp">
         <span class="socicon-twitter" style="color: #4da7de;">
         </span>
        </a>
        <a aria-label="Link to ITP camp instagram" href="https://www.instagram.com/itpcamp/">
         <span class="socicon-instagram" style="color: #000000;">
         </span>
        </a>
        <a aria-label="Link to ITP camp flickr" href="https://www.flickr.com/photos/itpcamp/">
         <span class="socicon-flickr" style="color: #1e1e1b;">
         </span>
        </a>
       </p>
      </div>
      <!-- Include the Quill library -->
      <script src="https://cdn.quilljs.com/1.3.6/quill.js">
      </script>
      <script src="https://cdn.jsdelivr.net/npm/quilljs-markdown@latest/dist/quilljs-markdown.js">
      </script>
     </body>
    </html>



```python
soup.find('h1')
```




    <h1><a href="https://itp.nyu.edu/camp2023"><img alt="ITP Camp 2023" height="175" src="images/ITPCamp2023-logo2.png" width="175"/></a>
    </h1>




```python
headers = soup.find_all('h1')
print(len(headers))
h = headers[0]
h
```

    6





    <h1><a href="https://itp.nyu.edu/camp2023"><img alt="ITP Camp 2023" height="175" src="images/ITPCamp2023-logo2.png" width="175"/></a>
    </h1>



## Type, Click and Scroll!

### Typing


```python

```

### Clicking


```python

```

### Scrolling


```python
def scroll(driver, up=False, amount=15):
    """15 is a little bit of scrolling"""
    current_position = driver.execute_script("return document.documentElement.scrollTop")
    for i in range(amount):
        if up:
            y = current_position - i*57
        else:
            y = current_position + i*57
        driver.execute_script("window.scrollTo(0, {})".format(y))
        time.sleep(np.random.uniform(low=0.01, high=.05))
```


```python
for i in range(10):
    scroll(driver)
    time.sleep(2) #Small Pause.
```

## Thoughts + Recommendations: 

1. Start Small!
2. Check Your Work
3. Build Iteratively
4. Use a VPN
5. SLOW DOWN!!!! - DON'T GET BLACKLISTED
6. Cache Pages! (You can update your parsing logic later!)
7. JS and React pages get more challenging

## Other Resources:

#### Other Scraping Resources:
* [Requests Documentation](https://docs.python-requests.org/en/latest/index.html)
* [Scrapy](https://scrapy.org/)

#### Regex:
* [Rexegg - Regex Resources](https://www.rexegg.com/)
* [Regex Documentation](https://docs.python.org/3/howto/regex.html)
* [Regex Cheat Sheet](https://www.debuggex.com/cheatsheet/regex/python)


```python

```
