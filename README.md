# jeromecaruso.greenfireelectronportfolio

Project setup
```
I ran all of this locally with Visual Studio Code
Operating system: Windows 7 64bit
Node.js v12.19.0
"electron": "^13.0.0"

Run/Pull the greenfireelectronportfolioB repo first and run :
npm i
then 
npm run devStart
-----
on the greenfireelectronportfolio(current repo)
npm install
npm run electron:serve

----
On one of three computers I tested this with, one of the times I had to reinstall on the Electron/Vue app
npm i @electron/remote
and 
npm install --save html2canvas

----
On line 66 in the App.vue file you can change how often the api updates, I have it set for every 10 seconds.



