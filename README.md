# ๐ค TypingGame
### vanilla, API๋ฅผ ์ด์ฉํ ๊ฐ๋จํ ์์ด๋จ์ด ํ์ดํ ๊ฒ์ ๋ง๋ค๊ธฐ

# ๐ค ์ฌ์ฉ๊ธฐ์  & ๊ฐ๋ฐํ๊ฒฝ
<img src="https://img.shields.io/badge/html-E34F26?style=for-the-badge&logo=html5&logoColor=white">&nbsp;
<img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white">&nbsp;
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"><br>
<img src="https://img.shields.io/badge/Visual Studio Code-0769AD?style=for-the-badge&logo=Visual Studio Code IDEA&logoColor=white">

# ๐ค ํ๋ฉด๊ตฌ์ฑ ๋ฐ ๊ธฐ๋ฅ
https://user-images.githubusercontent.com/97427387/215437018-eab487a6-ed48-4f60-ae98-723ac25ba986.mp4

- ๊ฒ์ ๋ก๋ฉ์ค์ด ๋จผ์  ๋จ๊ณ  ์๊ฐ์ด ์ง๋๋ฉด ๊ฒ์์์ ๋ฒํผ์ด ํ์ฑํ ๋จ
- ๊ฒ์ ์์ click -> 5์ด์ ์๊ฐ์ด ์นด์ดํธ๋ค์ด ๋จ
- input์ ๋จ์ด๋ฅผ ์๋ ฅ์[์๋ฌธ์, ๋๋ฌธ์ ์๊ด์์ด] ์ ์๊ฐ ์ค๋ฆ

---

### ๐๐ป ๋ด ๋ง๋๋ก ๊ธฐ๋ฅ ์ถ๊ฐ 
<details>
<summary>๊ฒ์ ์์ ์  input์ฐฝ ๋นํ์ฑํ</summary><br>

```javascript
function init() {
    buttonChange('๊ฒ์ ๋ก๋ฉ์คยทยทยท');
    wordInput.disabled  = true;      // ์ถ๊ฐ
    getWords();
    wordInput.addEventListener('input', checkMatch);
};

function buttonChange(text) {
    but.innerText = text;
    text === '๊ฒ์์์' ? 
    (but.classList.remove('loading'),wordInput.disabled  = true) : 
    (but.classList.add('loading'), wordInput.disabled  = false);
    
    // ๋ฒํผ text๊ฐ ๊ฒ์์์์ด๋ผ๋ฉด input์ ๋นํ์ฑํ ์ํด
};
```
</details>

<details>
<summary>์ ๋ต ์ alert์ ๋์ ์ฌ๋ฏธ++</summary><br>
  
```javascript
function checkMatch () {
    if(wordInput.value.toLowerCase() === wordDisplay.innerText.toLowerCase()) {
        wordInput.value = '';
        if(!isPlaying) { return; }
        score++;
        scoreDisplay.innerText = score;
        time = Game_Time;
        const randomeIndex = Math.floor(Math.random() * words.length);
        wordDisplay.innerText = words[randomeIndex];
        // alert ์ถ๊ฐ
        alert(
            '\n์ ์ ์ฌ๋ผ๊ฐ๋น ์ \n\n' +
            'หโง๏ผฟโง  ใ+        โฬณอออ๐ \n' + 
            '(  โขโฟโข )ใค  โฬณอออ ๐         โฬณอออ๐ +\n' +
            '(ใคใ <                โฬณอออ๐\n' +
            '๏ฝใ _ใค      +  โฬณอออ๐         โฬณอออ๐ ห\n' +
            '`ใยด'
        );
    };
};
```
</details>

<details>
<summary>์ ๊ฒ์์์ ํ ์ ๋ต ์๋ ฅ ์ ์ด์ ๊ฒ์ ์ ์ ๋ฐ์ ์ค๋ฅ ํด๊ฒฐ && input ์ด๊ธฐํ</summary><br> 
                
```javascript
function run() {
    if(isPlaying) { return; }
    isPlaying = true;
    time = Game_Time;
    wordInput.value = null;   // ๊ฒ์์คํ ์ input ๊ฐ ์ด๊ธฐํ
    wordInput.focus();
    score = 0;                // ๊ฒ์์คํ ์ ์ ์ ์ด๊ธฐํ
    scoreDisplay.innerText = 0;
    timeInterval = setInterval(countDown, 1000);
    checkInterval = setInterval(checkStatus, 50);
    buttonChange('๊ฒ์ ์ค')
};
```
</details>
