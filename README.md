live view : https://newgithubuser709.github.io/Count-onscroll 

```hash
 document.addEventListener("DOMContentLoaded", function() {
            const pElement = document.querySelector("p");
            let isCounting = false;
            let counterInterval;

            function updateCount() {
                const section2Top = document.getElementById("section2").offsetTop;
                const windowHeight = window.innerHeight;
                const scrollY = window.scrollY;

                if (scrollY >= section2Top && !isCounting) {
                    const targetCount = parseInt(pElement.getAttribute("data-count"));
                    countUp(targetCount);
                    isCounting = true;
                } else if (scrollY < section2Top && isCounting) {
                    resetCount();
                    isCounting = false;
                }
            }

            function countUp(targetCount) {
                let count = 0;
                const duration = 2000; // 2 seconds
                const interval = 10; // interval for smoother animation

                const increment = targetCount / (duration / interval);

                counterInterval = setInterval(function() {
                    count += increment;
                    pElement.textContent = Math.round(count);

                    if (count >= targetCount) {
                        clearInterval(counterInterval);
                    }
                }, interval);
            }

            function resetCount() {
                clearInterval(counterInterval);
                pElement.textContent = "0";
            }

            window.addEventListener("scroll", updateCount);
        });
```
