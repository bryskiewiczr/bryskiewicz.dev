+++
title = "Contact"
layout = "simple"
showTitle = false
+++

<style>
</style>

<div id="notebook-loading" class="show-content">
    <div class="flex flex-col min-w-full items-center">
        <div class="flex flex-row">
            <h3 class="notebook-loading-blink">Notebook Loading</h3>
        </div>
    </div>
</div>

<div id="animated-notebook" class="notebook p-6 bg-gray-100 rounded-lg shadow-md hide-content">
    <div class="cell mb-4">
        <div class="cmd-label">Cmd 1</div>
            <div id="input1" class="input bg-gray-200 p-4 rounded-md">
                <div class="line-numbers">1</div>
                <div class="line-content"></div>
        </div>
    </div>
    <div class="cell mb-4">
        <div class="cmd-label">Cmd 2</div>
        <div id="input2" class="input bg-gray-200 p-4 rounded-md">
            <div class="line-numbers">1</div>
            <div class="line-content"></div>
        </div>
        <div id="output2" class="output bg-white p-4 rounded-md border-l-4 border-green-500 mt-2">
            <div class="loading">Loading...</div>
        </div>
    </div>
    <div class="cell mb-4">
        <div class="cmd-label">Cmd 3</div>
        <div id="input3" class="input bg-gray-200 p-4 rounded-md">
            <div class="line-numbers">1</div>
            <div class="line-content"></div>
        </div>
        <div id="output3" class="output bg-white p-4 rounded-md border-l-4 border-green-500 mt-2">
            <div class="loading">Loading...</div>
        </div>
    </div>
    <div class="cell mb-4">
        <div class="cmd-label">Cmd 4</div>
        <div id="input4" class="input bg-gray-200 p-4 rounded-md">
            <div class="line-numbers">1</div>
            <div class="line-content"></div>
        </div>
        <div id="output4" class="output bg-white p-4 rounded-md border-l-4 border-green-500 mt-2">
            <div class="loading">Loading...</div>
        </div>
    </div>
    <div class="cell mb-4">
        <div class="cmd-label">Cmd 5</div>
        <div id="input5" class="input bg-gray-200 p-4 rounded-md">
            <div class="line-numbers">1</div>
            <div class="line-content"></div>
        </div>
        <div id="output5" class="output bg-white p-4 rounded-md border-l-4 border-green-500 mt-2">
            <div class="loading">Loading...</div>
        </div>
    </div>
    <div class="cell mb-4">
        <div class="cmd-label">Cmd 6</div>
        <div id="input6" class="input bg-gray-200 p-4 rounded-md">
            <div class="line-numbers">1</div>
            <div class="line-content blinking-cursor">_</div>
        </div>
    </div>
</div>

<pre id="static-notebook" class="notebook p-6 bg-gray-100 rounded-lg shadow-md hide-content">
<b>Email:</b> <a href="mailto:your-email@example.com?subject=Hello!&body=Hi!" class="text-blue-500">your-email@example.com</a><br>
<b>Socials:</b><br>
- <b>Github:</b> <a href="https://www.github.com/bryskiewiczr" target="_blank" class="text-blue-500">https://www.github.com/bryskiewiczr</a><br>
- <b>LinkedIn:</b> <a href="https://www.linkedin.com/in/bryskiewiczr/" target="_blank" class="text-blue-500">https://www.linkedin.com/in/bryskiewiczr/</a><br>
- <b>Website:</b> <a href="https://www.bryskiewicz.dev" target="_blank" class="text-blue-500">https://www.bryskiewicz.dev <- you're here</a>
</pre>

<script>
    function isMobileDevice() {
        return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent);
    }

    function typeEffect(element, text, delay = 20) {
        let index = 0;
        const interval = setInterval(() => {
            if (index < text.length) {
                element.innerHTML += text.charAt(index);
                index++;
            } else {
                clearInterval(interval);
            }
        }, delay);
    }

    function simulateNotebook() {
        const inputs = document.querySelectorAll('.input');
        const cells = document.querySelectorAll('.cell');
        const input1 = document.getElementById('input1').querySelector('.line-content');
        const input2 = document.getElementById('input2').querySelector('.line-content');
        const output2 = document.getElementById('output2');
        const input3 = document.getElementById('input3').querySelector('.line-content');
        const output3 = document.getElementById('output3');
        const input4 = document.getElementById('input4').querySelector('.line-content');
        const output4 = document.getElementById('output4');
        const input5 = document.getElementById('input5').querySelector('.line-content');
        const output5 = document.getElementById('output5');
        const input6 = document.getElementById('input6');

        function activateCell(index) {
            cells.forEach((cell, i) => {
                if (i === index) {
                    inputs[i].classList.add('active');
                    /* cell.classList.add('active'); */
                    cell.style.display = 'block';
                } else {
                    inputs[i].classList.remove('active');
                    cell.classList.remove('active');
                }
            });
        }

        function deactivateCell(index) {
            cells[index].classList.remove('active');
        }

        function showLoading(output) {
            output.querySelector('.loading').style.display = 'block';
            output.style.display = 'block';
        }

        function hideLoading(output) {
            output.querySelector('.loading').style.display = 'none';
        }

        setTimeout(() => {
            document.querySelector('#notebook-loading').classList.add("hide-content");
            document.querySelector('#notebook-loading').classList.remove("show-content");
            document.querySelector(".notebook").classList.add("show-content");
        },  1500);

        setTimeout(() => {
            activateCell(0);
        }, 1500);
        setTimeout(() => {
            typeEffect(input1, 'contact = robert.get("contact_info")');
        }, 2000);

        setTimeout(() => {
            activateCell(1);
        }, 3250);
        setTimeout(() => {
            typeEffect(input2, 'contact.help()');
        }, 3750);

        setTimeout(() => {
            showLoading(output2);
        }, 4250);
        setTimeout(() => {
            hideLoading(output2);
            output2.innerHTML = '<b>Available commands:</b><br>- name() -> Show full name<br>- email() -> Show email address<br>- socials() -> Show social links';
            deactivateCell(1);
        }, 4500);

        setTimeout(() => {
            activateCell(2);
        }, 5000);
        setTimeout(() => {
            typeEffect(input3, 'contact.name()');
        }, 5500);

        setTimeout(() => {
            showLoading(output3);
        }, 6000);
        setTimeout(() => {
            hideLoading(output3);
            output3.innerHTML = '<b>Name:</b> Robert Bryśkiewicz';
            deactivateCell(2);
        }, 6250);

        setTimeout(() => {
            activateCell(3);
        }, 7000);
        setTimeout(() => {
            typeEffect(input4, 'contact.email()');
        }, 7500);

        setTimeout(() => {
            showLoading(output4);
        }, 8000);
        setTimeout(() => {
            hideLoading(output4);
            output4.innerHTML = '<b>Email:</b> <a href="mailto:robert@bryskiewicz.dev?subject=Hello!&body=Hi!" class="text-blue-500">robert@bryskiewicz.dev</a>';
            deactivateCell(3);
        }, 8250);

        setTimeout(() => {
            activateCell(4);
        }, 8750);

        setTimeout(() => {
            typeEffect(input5, 'contact.socials()');
        }, 9250);

        setTimeout(() => {
            showLoading(output5);
        }, 9750);
        setTimeout(() => {
            hideLoading(output5);
            output5.innerHTML = '<b>Socials:</b><br>- <b>Github:</b> <a href="https://github.com/bryskiewiczr" target="_blank" class="text-blue-500">https://github.com/bryskiewiczr</a><br>- <b>LinkedIn:</b> <a href="https://www.linkedin.com/in/bryskiewiczr/" target="_blank" class="text-blue-500">https://www.linkedin.com/in/bryskiewiczr/</a><br>- <b>Website:</b> <a href="https://bryskiewicz.dev" target="_blank" class="text-blue-500">https://bryskiewicz.dev</a> <- you\'re here!';
            deactivateCell(4);
        }, 10250);

        setTimeout(() => {
            activateCell(5);
            input6.style.display = 'block';
        }, 10750);
    }

    let staticNotebook = document.getElementById("static-notebook");
    let animatedNotebook = document.getElementById("animated-notebook");

    if (isMobileDevice()) {
        animatedNotebook.classList.remove("show-content");
        animatedNotebook.classList.add("hide-content");
        staticNotebook.classList.add("show-content");
        staticNotebook.classList.remove("hide-content");
    } else {
        simulateNotebook();
    }
</script>
