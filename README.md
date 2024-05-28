# tampermonkey

安装tamper monkey

https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo/related?hl=vi


如何使用脚本：

https://www.youtube.com/watch?v=RpjvLpyiras

脚本：

// ==UserScript==
// @name         New Userscript
// @namespace    http://tampermonkey.net/
// @version      2024-05-25
// @description  try to take over the world!
// @author       You
// @match        https://photon-sol.tinyastro.io/en/lp/*
// @icon         https://www.google.com/s2/favicons?sz=64&domain=tinyastro.io
// @grant        none
// ==/UserScript==

(function () {
    'use strict';
    function createPhotonButton() {
        const targetDiv = document.querySelector("body > div.c-body > div.p-show > div.l-row.l-row-gap--xxs.u-flex-lg-row-reverse > div.l-col-12.l-col-lg-auto > div > div.p-show__widget.p-show__pair.u-py-s-lg > div.u-d-flex.u-flex-lg-column.u-justify-content-between.u-justify-content-lg-center.u-align-items-lg-center.u-align-items-start");
        if (targetDiv && !document.querySelector('.open-pumpfun') && !document.querySelector('.dexscreener') && !document.querySelector('.open-dexscreener')) {
            const dexscreenerHeader = document.createElement('img');
            dexscreenerHeader.className = 'dexscreener';
            const headerImage = `https://dd.dexscreener.com/ds-data/tokens/solana/${window.taConfig.show["token-address"]}/header.png`;
            dexscreenerHeader.width = "300";
            dexscreenerHeader.src = headerImage
            targetDiv.appendChild(dexscreenerHeader);

            const photonLink = document.createElement('a');
            photonLink.className = 'open-pumpfun';
            photonLink.textContent = 'Pumpfun';
            photonLink.href = 'https://pump.fun/' + window.taConfig.show["token-address"];
            photonLink.target = '_blank';

            const photonTab = document.createElement('div');
            photonTab.className = 'c-info__tab';
            photonTab.appendChild(photonLink);

            const dexscreenerLink = document.createElement('a');
            dexscreenerLink.className = 'open-dexscreener';
            dexscreenerLink.textContent = 'Dexscreener';
            dexscreenerLink.href = 'https://dexscreener.com/solana/' + window.taConfig.show["pool-address"];
            dexscreenerLink.target = '_blank';

            const dexscreenerTab = document.createElement('div');
            dexscreenerTab.className = 'c-info__tab';
            dexscreenerTab.appendChild(dexscreenerLink);

            const tabsContainer = document.createElement('div');
            tabsContainer.className = 'c-info__tabs';
            tabsContainer.appendChild(photonTab);
            tabsContainer.appendChild(dexscreenerTab);
            targetDiv.appendChild(tabsContainer);

        }
    }
    setInterval(createPhotonButton, 1000);
})();
