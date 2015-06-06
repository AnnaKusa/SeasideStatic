function test() {
    setHead();
    setMonth();
    createDays();
    setDays();
};
var today = new Date();
var month = today.getMonth();
var year = today.getFullYear();
var DAYS_OF_WEEK = 7;
var DAYS_ROWS = 6;
var monthNames = ["Січень", "Лютий", "Березень", "Квітень", "Травень", "Червень",
        "Липень", "Серпень", "Вересень", "Жовтень", "Листопад", "Грудень"];

function clickLeft() {
    if (month === 0) {
        month = 11;
        year--;
    } else {
        month--;
    }
    setMonth();
    setDays();
}

function clickRight() {
    if (month === 11) {
        month = 0;
        year++;
    } else {
        month++;
    }
    setMonth();
    setDays();
}

function setMonth() {
    document.getElementById('month').innerHTML = '<span class="cell">' + monthNames[month] + ', ' + year + '</span>';
}

function createDays() {
    for (var i = 0; i < DAYS_OF_WEEK * DAYS_ROWS; i++) {
        var container = document.createElement('div');
        container.id = i;
        document.getElementsByClassName('data')[0].appendChild(container);
    }
}

function setDays() {
    var firstDay = new Date(year, month, 1).getDay();
    var daysOfMonth = new Date(year, month + 1, 0).getDate();
    (firstDay === 0) ? firstDay += 7 : firstDay;
    for (var i = 0; i < firstDay; i++) {
        nullDays(i);
    }
    for (i = 0 ; i < daysOfMonth; i++) {
        document.getElementById(i + firstDay-1).innerHTML = '<span class="cell">' + (i + 1) + '</span>';
        document.getElementById(i + firstDay-1).className = 'active';
        document.getElementById(i + firstDay-1).setAttribute('onclick', "openReporting(" + (i + 1) + ")");
    }
    for (i = daysOfMonth + firstDay-1; i < DAYS_OF_WEEK * DAYS_ROWS; i++) {
        nullDays(i);
    }
}

function nullDays(i) {
    var x = document.getElementById(i);
    x.innerHTML = '';
    x.className = 'not_active';
    x.onclick = null;
}

var daysNames = ["пн", "вт", "ср", "чт", "пт", "сб", "нд"];

function setHead() {
    var header = document.createElement('div');
    header.id = 'header';
    document.getElementById('calendar').appendChild(header);
    var imgLeft = document.createElement('img');
    imgLeft.src = 'http://localhost:8081/static/images/arrow-left.png';
    imgLeft.id = 'img-left';
    imgLeft.addEventListener('click', clickLeft);
    document.getElementById('header').appendChild(imgLeft);
    var month = document.createElement('div');
    month.id = 'month';
    document.getElementById('header').appendChild(month);
    var imgRight = document.createElement('img');
    imgRight.src = 'http://localhost:8081/static/images/arrow-right.png';
    imgRight.id = 'img-right';
    imgRight.addEventListener('click', clickRight);
    document.getElementById('header').appendChild(imgRight);
    var dh = document.createElement('div');
    dh.id = 'daysHeader';
    document.getElementById('calendar').appendChild(dh);
    for (var i = 0; i < DAYS_OF_WEEK; i++) {
        var container = document.createElement('div');
        container.className += 'days';
        container.innerHTML = '<span class="cell">' + daysNames[i] + '</span>';
        document.getElementById('daysHeader').appendChild(container);
    }
    var days = document.createElement('div');
    days.className += 'data';
    document.getElementById('calendar').appendChild(days);
}


