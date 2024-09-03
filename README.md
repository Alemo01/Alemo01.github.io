<html lang="en"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calendar</title>

    <style>
        body {
    font-family: 'Arial', sans-serif;
    background-color: #fff;
}

.wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
  flex-direction: column;
  min-height: 100%;
}

button::-moz-focus-inner { 
  border: 0;
  padding: 0;
}

#calendari {
    margin:  0 auto;
    /* height: 330px; */
    /* width: 350px; */
    font-size: 14px;
    /* box-shadow: 0px 1px 4px rgba(0,0,0,0.4); */
}
table {
    border-collapse: collapse;
    table-layout: fixed;
    box-shadow: 0px 1px 3px rgba(0,0,0,0.2);
    background-color: #fff;
    position: absolute;


}


td,th {
    text-align: center;
    background-color: #fff;
}
th {
    padding: 10px;
}
tr:first-child th {
    font-size: 20px;
    font-weight: bold;
    border-left: none;
    border-top: none;
}
td:last-child, th:last-child {
  border-right: none;
}

th {
    border-top: 1px solid rgba(0,0,0,0.1);
    border-right: 1px solid rgba(0,0,0,0.1);
    background-color: #93b63a;
    color: #fff;
    text-shadow: 0px -1px 0px rgba(0,0,0,0.2);
    font-weight: normal;
}
th .any {
    font-size: 12px;
    font-weight: normal;
    display: block;
    text-shadow: none;
    color: rgba(0,0,0,0.4);
}
tr:nth-child(2) th {
    padding: 5px;
}
td {
    padding: 0;
    border-bottom: 1px solid rgba(0,0,0,0.05);
}
td>span {
    color: #555;
    padding: 10px;
    display: block;
    border: 2px solid transparent;
    transition: border 0.3s ease;
}

td:nth-child(even)>span {
    background-color: rgba(0,0,0,0.02);
}
td:last-child>span,
td:nth-child(6)>span {
    color: #9b59b6;
}
td.avui>span {
    font-weight: bold;
    background-color: #93b63a;
    color: #fff;
    border: 2px solid rgba(0,0,0,0.1);
}
td.fora > span {
    opacity: 0.2;
}
td > span:hover {
    background: #a57cb6;
    color: #fff;
}
.boto-next, .boto-prev {
    background: rgba(0,0,0,0.1);
    color: #fff;
    font-family: inherit;
    border: none;
    font-size: 18px;
    font-weight: bold;
    text-shadow: inherit;
    padding: 2px 10px 5px 10px;
    line-height: 1px;
    height: 30px;
    width: 30px;
    vertical-align: middle;
    border-radius: 100%;
    position: absolute;
    top: 15px;
}
.boto-next { right: 10px; padding-left: 13px; }
.boto-prev { left: 10px; padding-right: 13px;}
.boto-next:hover,
.boto-prev:hover {
    background: rgba(0,0,0,0.2);
}
button:hover { cursor: pointer; }
button:focus { outline: none; }

footer {
  text-align: center;
  color: #ddd;
  font-weight: normal;
  text-shadow: 0px -1px 0px rgba(0, 0, 0, 0.2);
  font-size: 0.8em;
  padding: 20px;
}

footer a,
footer a:link {
  color: #fff;
  text-decoration: none;
}
    </style>
<style type="text/css"></style><style type="text/css" id="operaUserStyle">
  img {
    filter: -opera-shader(url(data:text/plain;base64,Ly8gaHR0cHM6Ly9naXRodWIuY29tL0dQVU9wZW4tRWZmZWN0cy9GaWRlbGl0eUZYLUNBUwovLyB2MwoKdW5pZm9ybSBzaGFkZXIgaUNodW5rOwp1bmlmb3JtIGZsb2F0MiBpQ2h1bmtTaXplOwp1bmlmb3JtIGZsb2F0MiBpTW91c2U7CnVuaWZvcm0gZmxvYXQgaUFyZ3NbMV07Cgpjb25zdCBmbG9hdCBFUFNJT04gPSAwLjE7CmNvbnN0IGZsb2F0IFZfTUlOID0gMDsKY29uc3QgZmxvYXQgVl9MT1cgPSAwLjI1Owpjb25zdCBmbG9hdCBWX01FRCA9IDAuNTsKY29uc3QgZmxvYXQgVl9ISUdIID0gMC43NTsKY29uc3QgZmxvYXQgVl9NQVggPSAxOwoKY29uc3QgZmxvYXQgVEhSRVNIT0xEX0FSRUEgPSA4MDAgKiA2MDA7CmNvbnN0IGZsb2F0IE1JTl9BUkVBID0gNDAwICogMTAwOwpjb25zdCBmbG9hdCBNSU5fU1RSSVAgPSAyMDsKY29uc3QgZmxvYXQgTUFSR0lOID0gMTsKCmZsb2F0MyBwaXhlbChpbnQgeCwgaW50IHksIGZsb2F0MiB4eSkgewogICAgcmV0dXJuIGlDaHVuay5ldmFsKHh5ICsgZmxvYXQyKHgsIHkpKS5yZ2I7Cn0KCmZsb2F0MyBzaGFycGVuKGZsb2F0MiB4eSkgewogICAgZmxvYXQzIGYgPQogICAgICAgIHBpeGVsKC0xLCAtMSwgeHkpICogIDEgKwogICAgICAgIHBpeGVsKCAwLCAtMSwgeHkpICogLTEgKwogICAgICAgIHBpeGVsKCAxLCAtMSwgeHkpICogIDEgKwoKICAgICAgICBwaXhlbCgtMSwgMCwgeHkpICogLTEgICsKICAgICAgICBwaXhlbCggMCwgMCwgeHkpICogLTEgICsKICAgICAgICBwaXhlbCggMSwgMCwgeHkpICogLTEgICsKCiAgICAgICAgcGl4ZWwoLTEsIDEsIHh5KSAqIDEgICArCiAgICAgICAgcGl4ZWwoIDAsIDEsIHh5KSAqIC0xICArCiAgICAgICAgcGl4ZWwoIDEsIDEsIHh5KSAqIDE7CiAgICByZXR1cm4gZiAvIC0xOwp9CgpmbG9hdDQgUkdYMihmbG9hdDIgeHkpIHsKICAgIGZsb2F0NCBjb2xvciA9IGlDaHVuay5ldmFsKHh5KTsKCiAgICBpZiAoaUNodW5rU2l6ZS54ICogaUNodW5rU2l6ZS55IDwgTUlOX0FSRUEpIHsKICAgICAgICByZXR1cm4gY29sb3I7CiAgICB9CgogICAgaWYgKGlDaHVua1NpemUueSA8IE1JTl9TVFJJUCB8fCBpQ2h1bmtTaXplLnggPCBNSU5fU1RSSVApIHsKICAgICAgICByZXR1cm4gY29sb3I7CiAgICB9CgogICAgaWYgKHh5LnggPCBNQVJHSU4gfHwgeHkueCA+IChpQ2h1bmtTaXplLnggLSBNQVJHSU4pIHx8CiAgICAgICAgeHkueSA8IE1BUkdJTiB8fCB4eS55ID4gKGlDaHVua1NpemUueSAtIE1BUkdJTikpIHsKICAgICAgICByZXR1cm4gY29sb3I7CiAgICB9CgogICAgcmV0dXJuIGZsb2F0NChzaGFycGVuKHh5KSwgMSk7Cn0KCmZsb2F0IG1pbjMoZmxvYXQgeCwgZmxvYXQgeSwgZmxvYXQgeikgewogICAgcmV0dXJuIG1pbih4LCBtaW4oeSwgeikpOwp9CgpmbG9hdCBtYXgzKGZsb2F0IHgsIGZsb2F0IHksIGZsb2F0IHopIHsKICAgIHJldHVybiBtYXgoeCwgbWF4KHksIHopKTsKfQoKZmxvYXQgcmNwKGZsb2F0IHYpIHsKICAgIHJldHVybiAxIC8gdjsKfQoKZmxvYXQzIFJHWDMoZmxvYXQyIHh5LCBmbG9hdCBzdHJlbmd0aCkgewogICAgZmxvYXQzIGEgPSBwaXhlbCgtMSwgLTEsIHh5KTsKICAgIGZsb2F0MyBiID0gcGl4ZWwoIDAsIC0xLCB4eSk7CiAgICBmbG9hdDMgYyA9IHBpeGVsKCAxLCAtMSwgeHkpOwoKICAgIGZsb2F0MyBkID0gcGl4ZWwoLTEsIDAsIHh5KTsKICAgIGZsb2F0MyBlID0gcGl4ZWwoIDAsIDAsIHh5KTsKICAgIGZsb2F0MyBmID0gcGl4ZWwoIDEsIDAsIHh5KTsKCiAgICBmbG9hdDMgZyA9IHBpeGVsKC0xLCAxLCB4eSk7CiAgICBmbG9hdDMgaCA9IHBpeGVsKCAwLCAxLCB4eSk7CiAgICBmbG9hdDMgaSA9IHBpeGVsKCAxLCAxLCB4eSk7CgogICAgZmxvYXQgbW5SID0gbWluMyhtaW4zKGQuciwgZS5yLCBmLnIpLCBiLnIsIGgucik7CiAgICBmbG9hdCBtbkcgPSBtaW4zKG1pbjMoZC5nLCBlLmcsIGYuZyksIGIuZywgaC5nKTsKICAgIGZsb2F0IG1uQiA9IG1pbjMobWluMyhkLmIsIGUuYiwgZi5iKSwgYi5iLCBoLmIpOwoKICAgIGZsb2F0IG1uUjIgPSBtaW4zKG1pbjMobW5SLCBhLnIsIGMuciksIGcuciwgaS5yKTsKICAgIGZsb2F0IG1uRzIgPSBtaW4zKG1pbjMobW5HLCBhLmcsIGMuZyksIGcuZywgaS5nKTsKICAgIGZsb2F0IG1uQjIgPSBtaW4zKG1pbjMobW5CLCBhLmIsIGMuYiksIGcuYiwgaS5iKTsKCiAgICBtblIgPSBtblIgKyBtblIyOwogICAgbW5HID0gbW5HICsgbW5HMjsKICAgIG1uQiA9IG1uQiArIG1uQjI7CgogICAgZmxvYXQgbXhSID0gbWF4MyhtYXgzKGQuciwgZS5yLCBmLnIpLCBiLnIsIGgucik7CiAgICBmbG9hdCBteEcgPSBtYXgzKG1heDMoZC5nLCBlLmcsIGYuZyksIGIuZywgaC5nKTsKICAgIGZsb2F0IG14QiA9IG1heDMobWF4MyhkLmIsIGUuYiwgZi5iKSwgYi5iLCBoLmIpOwoKICAgIGZsb2F0IG14UjIgPSBtYXgzKG1heDMobXhSLCBhLnIsIGMuciksIGcuciwgaS5yKTsKICAgIGZsb2F0IG14RzIgPSBtYXgzKG1heDMobXhHLCBhLmcsIGMuZyksIGcuZywgaS5nKTsKICAgIGZsb2F0IG14QjIgPSBtYXgzKG1heDMobXhCLCBhLmIsIGMuYiksIGcuYiwgaS5iKTsKCiAgICBteFIgPSBteFIgKyBteFIyOwogICAgbXhHID0gbXhHICsgbXhHMjsKICAgIG14QiA9IG14QiArIG14QjI7CgogICAgZmxvYXQgcmNwTVIgPSByY3AobXhSKTsKICAgIGZsb2F0IHJjcE1HID0gcmNwKG14Ryk7CiAgICBmbG9hdCByY3BNQiA9IHJjcChteEIpOwoKICAgIGZsb2F0IGFtcFIgPSBzYXR1cmF0ZShtaW4obW5SLCAyIC0gbXhSKSAqIHJjcE1SKTsKICAgIGZsb2F0IGFtcEcgPSBzYXR1cmF0ZShtaW4obW5HLCAyIC0gbXhHKSAqIHJjcE1HKTsKICAgIGZsb2F0IGFtcEIgPSBzYXR1cmF0ZShtaW4obW5CLCAyIC0gbXhCKSAqIHJjcE1CKTsKCiAgICBhbXBSID0gc3FydChhbXBSKTsKICAgIGFtcEcgPSBzcXJ0KGFtcEcpOwogICAgYW1wQiA9IHNxcnQoYW1wQik7CgogICAgZmxvYXQgcGVhayA9IC1yY3AobWl4KDgsIDUsIHN0cmVuZ3RoKSk7CgogICAgZmxvYXQgd1IgPSBhbXBSICogcGVhazsKICAgIGZsb2F0IHdHID0gYW1wRyAqIHBlYWs7CiAgICBmbG9hdCB3QiA9IGFtcEIgKiBwZWFrOwoKICAgIGZsb2F0IHJjcFdlaWdodFIgPSByY3AoMSArIDQgKiB3Uik7CiAgICBmbG9hdCByY3BXZWlnaHRHID0gcmNwKDEgKyA0ICogd0cpOwogICAgZmxvYXQgcmNwV2VpZ2h0QiA9IHJjcCgxICsgNCAqIHdCKTsKCiAgICByZXR1cm4gZmxvYXQzKAogICAgICAgIHNhdHVyYXRlKChiLnIgKiB3UiArIGQuciAqIHdSICsgZi5yICogd1IgKyBoLnIgKiB3UiArIGUucikgKiByY3BXZWlnaHRSKSwKICAgICAgICBzYXR1cmF0ZSgoYi5nICogd0cgKyBkLmcgKiB3RyArIGYuZyAqIHdHICsgaC5nICogd0cgKyBlLmcpICogcmNwV2VpZ2h0RyksCiAgICAgICAgc2F0dXJhdGUoKGIuYiAqIHdCICsgZC5iICogd0IgKyBmLmIgKiB3QiArIGguYiAqIHdCICsgZS5iKSAqIHJjcFdlaWdodEIpKTsKfQoKCmZsb2F0NCBtYWluKGZsb2F0MiB4eSkgewoKICAgIGZsb2F0NCBvcmlnaW5hbENvbG9yID0gaUNodW5rLmV2YWwoeHkpOwogICAgaWYgKG9yaWdpbmFsQ29sb3IuYSA8IDEpIHsKICAgICAgICByZXR1cm4gaUNodW5rLmV2YWwoeHkpOwogICAgfQoKICAgIGZsb2F0IGludGVuc2l0eSA9IGlBcmdzWzBdOwogICAgZmxvYXQgc3RyZW5ndGggPSAwOwogICAgZmxvYXQzIGNvbG9yOwoKICAgIGlmIChpbnRlbnNpdHkgPCBWX01JTiArIEVQU0lPTikgewogICAgICAgIHN0cmVuZ3RoID0gMC4xMDsKICAgICAgICBjb2xvciA9IFJHWDMoeHksIHN0cmVuZ3RoKTsKCiAgICB9IGVsc2UgaWYgKGludGVuc2l0eSA+IFZfTE9XIC0gRVBTSU9OICYmIGludGVuc2l0eSA8IFZfTE9XICsgRVBTSU9OKSB7CiAgICAgICAgc3RyZW5ndGggPSAwLjMzOwogICAgICAgIGNvbG9yID0gUkdYMyh4eSwgc3RyZW5ndGgpOwoKICAgIH0gZWxzZSBpZiAoaW50ZW5zaXR5ID4gVl9NRUQgLSBFUFNJT04gJiYgaW50ZW5zaXR5IDwgVl9NRUQgKyBFUFNJT04pIHsKICAgICAgICBzdHJlbmd0aCA9IDAuNTsKICAgICAgICBjb2xvciA9IFJHWDMoeHksIHN0cmVuZ3RoKTsKCiAgICB9IGVsc2UgaWYgKGludGVuc2l0eSA+IFZfSElHSCAtIEVQU0lPTiAmJiBpbnRlbnNpdHkgPCBWX0hJR0ggKyBFUFNJT04pIHsKICAgICAgICBzdHJlbmd0aCA9IDAuOTk7CiAgICAgICAgY29sb3IgPSBSR1gzKHh5LCBzdHJlbmd0aCk7CgogICAgfSBlbHNlIGlmIChpbnRlbnNpdHkgPiBWX01BWCAtIEVQU0lPTikgewogICAgICAgIHN0cmVuZ3RoID0gMTsKICAgICAgICBjb2xvciA9IFJHWDIoeHkpLnJnYjsKICAgIH0KCiAgICByZXR1cm4gZmxvYXQ0KGNvbG9yLCBvcmlnaW5hbENvbG9yLmEpOwp9) -opera-args(0.25 calc(env(-opera-gx-accent-color-r)/255) calc(env(-opera-gx-accent-color-g)/255) calc(env(-opera-gx-accent-color-b)/255)));
  }
</style></head>
<body>
    <div class="">
        <div id="calendari"><table class="actiu" data-actual="2024/08/02"><tr><th colspan="7"><button class="boto-prev">◂</button><span>September<span class="any">2024</span></span><button class="boto-next">▸</button></th></tr><tr><th>Mo</th><th>Tu</th><th>We</th><th>Th</th><th>Fr</th><th>Sa</th><th>Su</th></tr><tr><td class="fora"><span>26</span></td><td class="fora"><span>27</span></td><td class="fora"><span>28</span></td><td class="fora"><span>29</span></td><td class="fora"><span>30</span></td><td class="fora"><span>31</span></td><td><span>1</span></td></tr><tr><td class="avui"><span>2</span></td><td><span>3</span></td><td><span>4</span></td><td><span>5</span></td><td><span>6</span></td><td><span>7</span></td><td><span>8</span></td></tr><tr><td><span>9</span></td><td><span>10</span></td><td><span>11</span></td><td><span>12</span></td><td><span>13</span></td><td><span>14</span></td><td><span>15</span></td></tr><tr><td><span>16</span></td><td><span>17</span></td><td><span>18</span></td><td><span>19</span></td><td><span>20</span></td><td><span>21</span></td><td><span>22</span></td></tr><tr><td><span>23</span></td><td><span>24</span></td><td><span>25</span></td><td><span>26</span></td><td><span>27</span></td><td><span>28</span></td><td><span>29</span></td></tr><tr><td><span>30</span></td><td class="fora"><span>1</span></td><td class="fora"><span>2</span></td><td class="fora"><span>3</span></td><td class="fora"><span>4</span></td><td class="fora"><span>5</span></td><td class="fora"><span>6</span></td></tr></table></div>
      </div>
      <script>
        var mesos = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
    'July',
    'August',
    'September',
    'October',
    'November',
    'December'
];

var dies = [
    'Sunday',
    'Monday',
    'Tuesday',
    'Wedensday',
    'Thursday',
    'Friday',
    'Saturday'
];

var dies_abr = [
    'Su',
    'Mo',
    'Tu',
    'We',
    'Th',
    'Fr',
    'Sa'
];

Number.prototype.pad = function(num) {
    var str = '';
    for(var i = 0; i < (num-this.toString().length); i++)
        str += '0';
    return str += this.toString();
}

function calendari(widget, data)
{

    var original = widget.getElementsByClassName('actiu')[0];

    if(typeof original === 'undefined')
    {
        original = document.createElement('table');
        original.setAttribute('data-actual',
			      data.getFullYear() + '/' +
			      data.getMonth().pad(2) + '/' +
			      data.getDate().pad(2))
        widget.appendChild(original);
    }

    var diff = data - new Date(original.getAttribute('data-actual'));

    diff = new Date(diff).getMonth();

    var e = document.createElement('table');

    e.className = diff  === 0 ? 'amagat-esquerra' : 'amagat-dreta';
    e.innerHTML = '';

    widget.appendChild(e);

    e.setAttribute('data-actual',
                   data.getFullYear() + '/' +
                   data.getMonth().pad(2) + '/' +
                   data.getDate().pad(2))

    var fila = document.createElement('tr');
    var titol = document.createElement('th');
    titol.setAttribute('colspan', 7);

    var boto_prev = document.createElement('button');
    boto_prev.className = 'boto-prev';
    boto_prev.innerHTML = '&#9666;';

    var boto_next = document.createElement('button');
    boto_next.className = 'boto-next';
    boto_next.innerHTML = '&#9656;';

    titol.appendChild(boto_prev);
    titol.appendChild(document.createElement('span')).innerHTML = 
        mesos[data.getMonth()] + '<span class="any">' + data.getFullYear() + '</span>';

    titol.appendChild(boto_next);

    boto_prev.onclick = function() {
        data.setMonth(data.getMonth() - 1);
        calendari(widget, data);
    };

    boto_next.onclick = function() {
        data.setMonth(data.getMonth() + 1);
        calendari(widget, data);
    };

    fila.appendChild(titol);
    e.appendChild(fila);

    fila = document.createElement('tr');

    for(var i = 1; i < 7; i++)
    {
        fila.innerHTML += '<th>' + dies_abr[i] + '</th>';
    }

    fila.innerHTML += '<th>' + dies_abr[0] + '</th>';
    e.appendChild(fila);

    /* Obtinc el dia que va acabar el mes anterior */
    var inici_mes =
        new Date(data.getFullYear(), data.getMonth(), -1).getDay();

    var actual = new Date(data.getFullYear(),
			  data.getMonth(),
			  -inici_mes);

    /* 6 setmanes per cobrir totes les posiblitats
     *  Quedaria mes consistent alhora de mostrar molts mesos 
     *  en una quadricula */
    for(var s = 0; s < 6; s++)
    {
        var fila = document.createElement('tr');

        for(var d = 1; d < 8; d++)
        {
	    var cela = document.createElement('td');
	    var span = document.createElement('span');

	    cela.appendChild(span);

            span.innerHTML = actual.getDate();

            if(actual.getMonth() !== data.getMonth())
                cela.className = 'fora';

            /* Si es avui el decorem */
            if(data.getDate() == actual.getDate() &&
	       data.getMonth() == actual.getMonth())
		cela.className = 'avui';

	    actual.setDate(actual.getDate()+1);
            fila.appendChild(cela);
        }

        e.appendChild(fila);
    }

    setTimeout(function() {
        e.className = 'actiu';
        original.className +=
        diff === 0 ? ' amagat-dreta' : ' amagat-esquerra';
    }, 20);

    original.className = 'inactiu';

    setTimeout(function() {
        var inactius = document.getElementsByClassName('inactiu');
        for(var i = 0; i < inactius.length; i++)
            widget.removeChild(inactius[i]);
    }, 1000);

}

calendari(document.getElementById('calendari'), new Date());

    </script>


</body></html>
