# Doodle-Fish
使用了``CSS-Doodle``和``Javascript``

CSS-Doodle官网：[URL](https://css-doodle.com)

原文章：[URL](https://csscoco.com/inspiration/#/./cssdoodle/fish-seaweed)

**声明：本程序在源代码上稍作修改，已附上原文链接**
***

HTML代码：
```html
<css-doodle>
    :doodle { @grid: 1x35 / 100vw 100vh; } 
    
    :container { 
        background: linear-gradient(to top, rgba(0, 0, 0, .1) 0%, #aaf9ff 70%, transparent 100%); 
        margin: 0 auto;
        background-repeat: no-repeat; 
        max-width: 740px;
        overflow: hidden;
        transform-style: preserve-3d;
        perspective: 15px;
        animation: move 15s infinite linear alternate;
    } 
    
    @nth(2n) {
        --hslh: @pick(90, 100);
        --hsls: @pick(80%, 85%, 90%);
        --color: hsla(var(--hslh), var(--hsls), 50%, 0.9);
        position: relative; 
        width: 1vw;
        height: 2vw;
        border-radius: 50%;
        background: var(--color);
        top: @r(20, 70)vh;
        transform: scale(@r(0.5, 1.3));
        --n: @p(-1, 1, 1.2, -1.2);
        --c: var(--color);
        box-shadow: @m100(
            calc(@sin(@n() / 10) * 2.4vmin * @var(--n))
            calc(@n() * 1vmin) 0
            hsla(var(--hslh), var(--hsls), calc(50% - 1% * 0.2 * @n()), calc(0.9 - 0.011 * @n()))
        );
        transform: translateZ(@r(-5)px);
        z-index: 10;
    }
    
    @nth(4n + 1) {
        position: relative;
        width: 4.5vh;
        height: 4vh;
        --c: @pick(#bb2d00, #00aaff, #6644a3);
        background: var(--c);
        top: @r(15, 90)vh;
        @shape: @pick(fish, whale);
        transform: translate3d(@r(-200, 200)%, @r(-200, 200)%, @r(-20)px) scale(@r(.8, 1.4)) rotate(calc(@pick(0deg, 180deg)));
        z-index: @pick(5, 15);
        opacity: .8;
        animation: forward .8s infinite @r(0, 1.2)s alternate linear;
    
        ::before {
            position: absolute;
            content: "";
            width: .5vh;
            height: .5vh;
            background: #fff;
            border-radius: 50%;
            left: 70%;
            top: 45%;
            z-index: 2;
        }
    }
    
    @nth(7, 27) {
        width: .6vw;
        height: .6vw;
        border-radius: 50%;
        background: rgba(255, 255, 255, .3);
        top: @r(10, 50)%;
        box-shadow:
            0 -8vh .3vh 1.2px rgba(255, 255, 255, .4),
            0 -18vh .3vh 1.6px rgba(255, 255, 255, .5),
            0 -30vh .3vh 2px rgba(255, 255, 255, .6);
        z-index: 1;
        transform: translate(@r(-1000, 1000)%, 0);
    }

    @keyframes move {
        100% {
            perspective: 40px;
        }
    }
    
    @keyframes forward {
        0% {
            left: 0;
        }
        100% {
            left: -3px;
        }
    }
</css-doodle>

<script src="https://cdnjs.cloudflare.com/ajax/libs/css-doodle/0.6.1/css-doodle.min.js"></script>

```

CSS代码：
```css
html, body {
  margin: 0;
  height: 100%;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

Javascript代码：
```javascript
document.addEventListener('click', function (e) {
  e.target.update && e.target.update();
});
```
