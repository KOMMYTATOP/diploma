# diploma
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Расчет размера платы за использование радиочастотного спектра</title>
</head>
<body>
<H2 align="center">Расчет размера ежегодной платы за использование радиочастотного спектра в Республике Беларусь.
    Определение размера ежегодной платы произ-водится в порядке, установленном Постановлением Совета министров Республики Беларусь от 15.06.2006 № 890 с изменениями и дополнениями по состоянию на 01.01.2013</H2>
<h2 align="center">Выберите режим расчета</h2>
<button name="inter" onclick="disp(document.getElementById('typeRS'))">Интерактивный для одного РЭС или радиолюбителя</button>
<button name="pack">Пакетный для группы РЭС или радиолюбителей</button>
<button name="help">Помощь</button>
<form id="typeRS" name="typeRS" style="display:none">
    <h3>Выберите тип радиослужбы</h3>
    <select id="typeID" name="type" multiple onclick="disp(document.getElementById('markUseID')),createArr0()">
        <option name="radioBr">радиовещательная</option>
        <option name="sat">спутниковая</option>
        <option name="lanMob">сухопутная подвижная</option>
        <option name="fix">фиксированная</option>
        <option name="amateur">любительская или любительская спутниковая</option>
    </select>
</form>
<script>
    var A= [];
    function disp(form) {
        if (form.style.display == "none") {
            form.style.display = "block";
        } else {
            form.style.display = "none";
        }
    }
    function createArr0() {
        var objSelRS=document.typeRS.type;
        if ( objSelRS.selectedIndex != -1)
        {
            A[0]=objSelRS.options[objSelRS.selectedIndex].value;
        }
    }
    function createArr1() {
        var objSelMarkUse=document.markUse.markUse;
        if ( objSelMarkUse.selectedIndex != -1)
        {
            A[1]=objSelMarkUse.options[objSelMarkUse.selectedIndex].value;
        }
    }
    function createArr2() {
        var objSelTypeUse=document.typeUse.typeUse;
        if ( objSelTypeUse.selectedIndex != -1)
        {
            A[2]=objSelTypeUse.options[objSelTypeUse.selectedIndex].value;
        }
    }
    function createArr3() {
        var objSelPurp=document.Purp.purp;
        if ( objSelPurp.selectedIndex != -1)
        {
            A[3]=objSelPurp.options[objSelPurp.selectedIndex].value;
        }
    }
    function createArr4() {
        var objSelPlace=document.Place.place;
        if ( objSelPlace.selectedIndex != -1)
        {
            A[4]=objSelPlace.options[objSelPlace.selectedIndex].value;
        }
    }
    function createArr5() {
        var objSelTypeRES=document.typeRES.typeRES;
        if ( objSelTypeRES.selectedIndex != -1)
        {
            A[5]=objSelTypeRES.options[objSelTypeRES.selectedIndex].value;
        }
    }
    function dispPurp(form) {
        if ((form.style.display == "none") & (A[2]=='проектирование, строительство (установка)')){
            form.style.display = "block";
        } else {
            form.style.display = "none";
        }
    }
    function dispTypeRES(form) {
        if ((form.style.display == "none") & (A[3]=='технологическая сеть электросвязи')){
            form.style.display = "block";
        } else {
            form.style.display = "none";
        }
    }
    function addOption (olistbox, text, value, isDefaultSelected, isSelected)
    {
        var oOption = document.createElement("option");
        oOption.appendChild(document.createTextNode(text));
        oOption.setAttribute("value", value);

        if (isDefaultSelected) oOption.defaultSelected = true;
        else if (isSelected) oOption.selected = true;

        olistbox.appendChild(oOption);
    }
    function options() {
        var objSel=document.typeRES.typeRES;
        if (A[0]=='радиовещательная'){
            addOption(objSel, "микроволновая система распределения телевизионных сигналов", "microwave", true);
            addOption(objSel, "звуковое наземное вещание", "soundBroadcast", false);
            addOption(objSel, "аналоговое телевизионное наземное вещание", "analogTeleBroadcast", false);
            addOption(objSel, "цифровое телевизионное наземное вещание", "digitTeleBroadcast", false);
        }
        else if (A[0]=='спутниковая'){
            addOption(objSel, "земная станция спутниковой связи", "satCom", true);
        }
        else if (A[0]=='сухопутная подвижная'){
            addOption(objSel, "базовая станция сотовой подвижной электросвязи", "baseMob", true);
            addOption(objSel, "базовая станция, ретранслятор", "relay", false);
            addOption(objSel, "возимое (носимое) РЭС", "mobile", false);
        }
        else {
            addOption(objSel, "радиорелейная станция", "radioRelay", true);
            addOption(objSel, "радиолокационная станция", "rls", false);
            addOption(objSel, "станция беспроводного широкополосного доступа", "wi-fi", false);
            addOption(objSel, "станция других систем радиосвязи", "other", false);
        }
    }
</script>
<form id="markUseID" name="markUse" style="display:none">
    <h3>Выберите признак использования РЧС</h3>
    <select name="markUse" multiple onclick="disp(document.getElementById('typeUseID')),createArr1()">
        <option name="primary">на первичной основе</option>
        <option name="second">на вторичной основе</option>
    </select>
</form>
<form id="typeUseID" name="typeUse" style="display:none">
    <h3>Выберите тип права на использование РЧС</h3>
    <select name="typeUse" multiple onclick="createArr2(),dispPurp(document.getElementById('PurpID'))">
        <option name="build">проектирование, строительство (установка)</option>
        <option name="use">эксплуатация</option>
    </select>
</form>
<form id="PurpID" name="Purp" style="display:none">
    <h3>Выберите назначение РЭС</h3>
    <select name="purp" multiple onclick="dispTypeRES(document.getElementById('PlaceID')),createArr3()">
        <option name="serv">предоставление услуг электросвязи</option>
        <option name="tech">технологическая сеть электросвязи</option>
    </select>
</form>
<form id="PlaceID" name="Place" style="display:none">
    <h3>Выберите место установки РЭС</h3>
    <select name="place" multiple onclick="dispTypeRES(document.getElementById('typeRESID')),createArr4(),options()">
        <option name="minsk">Минск</option>
        <option name="brest">Брест</option>
        <option name="vitebsk">Витебск</option>
        <option name="gomel">Гомель</option>
        <option name="grodno">Гродно</option>
        <option name="mogilev">Могилев</option>
        <option name="minsk obl">Минская обл.</option>
        <option name="brest obl">Брестская обл.</option>
        <option name="vitebsk obl">Витебская обл.</option>
        <option name="gomel obl">Гомельская обл.</option>
        <option name="grodno obl">Гродненская обл.</option>
        <option name="mogilev obl">Могилевская обл</option>
    </select>
</form>
<form id="typeRESID" name="typeRES" style="display:none">
    <h3>Выберите тип РЭС</h3>
    <select id="RESID" name="typeRES" multiple onclick="createArr5()">
        <option>--Выберите--</option>
    </select>
</form>
</body>
</html>
