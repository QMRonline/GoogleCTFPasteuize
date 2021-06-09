# GoogleCTFPasteuize
PASTEURIZE - Google CTF  This was a super fun challenge that really tests your process and thoroughness when assessing a web application. Admittedly, I did not complete the challenge before the CTF was over, but that shouldn’t stop you from following through on finishing a challenge. Doing this challenge, you’ll learn some cool tricks with NodeJS, get better with source code review, and improve your web app response analysis.

 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
 
Simple Solving steps :
Step1 : Always read the desciption
Challenge description
*In this challenge, we get a URL: https://pasteurize.web.ctfcompetition.com/ and a description that says:
*This doesn’t look secure. I wouldn’t put even the littlest secret in here. My source tells me that third parties might have implanted it with their little treats already. Can you prove me right?
*On this website, we can create a “Paste”. After submitting it, we get redirected to a page with a random id, which shows our note.
*We also have the option to share this with TJMike🎤.

Step2 : Checking the source of web application
*There’s also a note which says: “<!– TODO: Fix b/1337 in /source that could lead to XSS –>“. So we navigate to https://pasteurize.web.ctfcompetition.com/source. 

Step3 : Planning the attack
*Navigating to the /source page reveals the source code for the web application which shows that it is a NodeJS Express web application.
*The database name is littlethings shown with the db structure used. 
*The escape_string function is used on the note content before it is added to the page.
const escape_string = unsafe => JSON.stringify(unsafe).slice(1, -1)
  .replace(/</g, '\\x3C').replace(/>/g, '\\x3E');
*After closer inspection, we realize that DOMPurify is its latest version and there are no known bypasses for it. So we have to inject our XSS payload before it reaches DOMPurify. This means that we should inject double quotation, close the string definition in the JavaScript code on the page and run our JS payload.

Step4: Execution of the attack
*POST with content=alert() works , now use content(-alert(1)-]=-1- through burp suite gives the redirection link checking it, we fetched the xss from here we can share this to tj mike which it'll execute the xss over there now we need to fetch the 

Step5: Solving the challenge
*Using Hookbing https://hookbin.com/ Hookbin is a free service that enables you to collect, parse, and view HTTP requests.
Create your unique endpoints to inspect headers, body, query strings, cookies, uploaded files, and much more.
*Craft the xss with the fetch and use the hookbin private end point and sharing this with Tjmike gives the cookie where you'll get the flag
*secret=CTF{Express_t0_Tr0ubl3s}


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
How to chat with me :💬
Discord : https://discord.gg/MtQdFygumr​​
Instagram : https://www.instagram.com/qmarkonline/​​
Website : https://qmarkonline.com​​    //coming-soon 

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
