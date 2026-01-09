# 2005/6 beta wii shop/vc channel files.
(if your confused, heres what im talkin about: <a target="_blank" href="https://nintendoeverything.com/a-look-at-an-early-version-of-the-wii-shop-channel-and-a-scrapped-channel/">early wii shop screenshots</a>
<h3>link down? no worries i backed up the photos here:</h3>
<a herf="https://github.com/betawii/early-shopping-channel/tree/main">https://github.com/betawii/early-shopping-channel/tree/main</a>
<br>
<br>
<h3>Huge credit to <a href="https://github.com/MrRM05">RM05 (github)</a> /// <a href="https://www.youtube.com/@Mr_RM05">RM05 (youtube)</a>  for taking the previously impossible to use CVS files (history log files with filename,v) and removing the ,v to make them usable again using cvs checkout. <br><br> edit Sep 21, 2025: /oss/ folder and a cvs/noncvs version were uploaded here, i replaced the original files from rm05 since when i uploaded them here i accidently deleted some files and no longer had a copy of the files rm05 sent, i checked out the cvs files and cleaned up things.</h3>

<h1>⬇️ with that out of the way, lets get to the goodies ⬇️</h1>

<p>files are sourced from: <i>archive.org/download/silver-space-world-1997-roms (iqcvs.tar.7z --> iqcvs.tar --> \cvstree-2.0\sw\infra\modules\oss\)</i><br>
<p>A more reliable link is at: https://downloads.deadlyfoez.com/?dir=files%2FNintendo%20Leaks%2FJuly%2020th%202021  (or just search "iqcvs.tar.7z" on google)</p>
<b>(please do not download, it has tons of files not related to the shop (sdk & unreleated ique things), if you just want the beta wii shop code in the \cvstree-2.0\sw\infra\modules\oss\, i provided it in the oss(INFO).zip files here but its missing some files that are SDK related cause i dont want to be distributing those things.. <i>(more info below)</i> </b>
</p>
<br> the <a href="https://github.com/betawii/early-shopping-channel/tree/nintendo-code-archive/oss">/oss/</a> folder provided here is the checkedout zip unzipped for viewing on github

<h3>in this branch, i have provided 
<br>the raw/uncheckout-d /oss/ folder from this archive called "oss-cvs-notcheckedout---10-14-2006-642AM.zip"
<br> + a checked out version  (no ,v and actual html/jsp) called "oss-cvs-checkedout.zip" 
<br> this is so you dont have to download the giant folder & just download whats needed.</h3>


<h3><i>info on date of folder and files: </i><BR> 
OSS folder dated <i>(last modified/sourcehereisfrom: 10/14/2006-october 14th, 2006 at 6:42AM)</i> <BR><BR>
earliest file in the folder is dated "5/9/2006"<BR><BR> 
the last time they edited a shop related file was "7/27/2006" or August 8th, 2006.
</h3><hr>

# it seems to be for the scrapped virtual console channel/ early shop channel!
<br> basically you would go to a home menu with these options:<br>
<img src="https://github.com/user-attachments/assets/9e9fd939-694b-4c5d-8734-348e6ba972d4"><br>

and some of those options lead you to the "early wii shop screenshots" seen here:<Br>
https://nintendoeverything.com/a-look-at-an-early-version-of-the-wii-shop-channel-and-a-scrapped-channel/
<br><br>
<p>digging through teh oss folder will give you more info, it is JSP (Jakarta Server Pages) not sure how to use those so i just put them here, hopefully someone can get them to work with apache tomcat or something..</p>
<br>
here are some screenshots of it on localhost btw (kinda broken cuz i tried to convert it to html:<br>
<img src="https://github.com/user-attachments/assets/c0a609d4-e765-4e4f-b3d6-cb7e3d825f7b"><br>
<p>(notice that blue button, in the code it says RENT (theres references to renting in the javascript & the image name), meaning you could at one point rent titles!)</p>
<Br><img src="https://github.com/user-attachments/assets/9bb39767-58b4-4936-8bd5-4e31806fc19e"><br>
<p>(a title description page with placeholder text [sadly the under button hover and some stuff are lost..]</p>
<Br><img src="https://github.com/user-attachments/assets/09d49aca-57d3-4569-9611-4aebdb191d5d"><br>
<p>(a catalog thats unfortunately empty (no titles like in the screenshots), but the title images exist in the <b>/oss/oss/WebContent/common/titles/</b> folder</p>
<Br><br>
<p>one final intresting thing to note (i havent fully dug through the code yet) <br>
is that in <b>in /oss/oss/WebContent/en_US/txt/license.txt</b>, it reads <br> 
<b>
  "Nintendo <b>Revolution</b> Virtual Console"
<br>
"Usage Terms and Privacy Statement"
</b>
  <br>
  Proving that these files are older then the final "Wii" name, yet they stuck with this design and htmls until <b>August 2006!</b> (probably)
</p>

<p>
    <br>
  <i>Another intresting thing is that it seems the modern wii shop was built off this original code as <a href="https://github.com/betawii/early-shopping-channel/blob/nintendo-code-archive/oss/WebContent/common/jsp/UseSettings.jsp">/oss/WebContent/common/jsp/UseSettings.jsp</a>s code seems to be present in a unused page on the wii shop, but it is modified: <a href="https://oss-auth.shop.wii.com/oss/serv/TestSettings.jsp">https://oss-auth.shop.wii.com/oss/serv/TestSettings.jsp</a>  </i>
</p>
  <br><hr>
  <h3>heres a snippit of both pages code to compare:</h3>
  <p>UseSettings.jsp:</p>
<pre>
  <%@ include file="Common.jspf" %>

<html>
<head>
  <%@ include file="Header.jspf" %>
  <title>Use Settings</title>
</head>

<jsp:useBean id="countries" class="com.broadon.cas.CountryListBean" scope="request">
</jsp:useBean>

<SCRIPT language="JavaScript">
		function showSelectedOption(listId, value)
		{
			var list = document.getElementById(listId);
			if (list != null) {
				list.selectedIndex = -1;
				for (i = 0; i < list.options.length; i++) {
					var option = list.options[i];					
					if (option.value == value) {
						list.selectedIndex = option.index;
					}
				}
			}
		}

		function initPage()
		{
			var agefield = document.getElementById("ageField");
			if (agefield != null) {
				agefield.value = '<c:out value="${age}" />';			
			}

			showSelectedOption("regionList", '<c:out value="${region}" />');
			showSelectedOption("countryList", '<c:out value="${country}" />');
			showSelectedOption("languageList", '<c:out value="${language};${locale}" />');
		}
		
		function changeRegion()
		{
			var regionlist = document.getElementById("regionList");
			if (regionlist != null) {
				var region = regionlist.options[regionlist.selectedIndex].value;
				ec.setRegion(region);				
				location.replace("UseSettings.jsp?region=" + region);
			}
		}

		function changeLanguage()
		{
			var languagelist = document.getElementById("languageList");
			if (languagelist != null) {
				var s = languagelist.options[languagelist.selectedIndex].value;
				var i = s.indexOf(';');
				var language = s.substr(0, i);
				var locale = s.substr(i+1);
				ec.setLanguage(language);
				location.replace("UseSettings.jsp?language=" + language + "&locale=" + locale);
			}
		}

		function changeCountry()
		{
			var countrylist = document.getElementById("countryList");
			if (countrylist != null) {
				var country = countrylist.options[countrylist.selectedIndex].value;
				ec.setCountry (country);
				location.replace("UseSettings.jsp?country=" + country);
			}
		}

		function validate()
		{
			var submitOK = true;

			var agefield = document.getElementById("ageField");
			if (agefield != null) {
				var age = agefield.value;
				if (age.length > 0 && (isNaN(age)||age<1||age>100))
				{
					alert("The age must be a number between 1 and 100");
					submitOK = false;
	 			} else {
					ec.setAge(age);
				}
			}
			
			return submitOK;
		}

</SCRIPT>
<%
	pageContext.setAttribute("countryCount", String.valueOf(countries.getCountries().size()));
%>

<body onload="initPage()">

<CENTER>

<FORM action="Terms.jsp" onsubmit="return validate()" method="post">
<c:catch var="error">
<c:choose>
<c:when test="${countryCount eq '0'}">
No countries found for region <c:out value="${countries.region}" />
</c:when>
<c:otherwise>
Country<BR>
<c:set var="currentCountry" value="${countries.countries[0]}" />
<select name="country" size="1" id="countryList" onchange="changeCountry()">	
	<!-- Display country name using selected locale, if not available use default locale for country -->
	<c:forEach items="${countries.countries}" var="c">
		<option value="<c:out value="${c.code}"/>">
		<c:out value="${c.name}" default="${c.code}"/>
		</option>		
		<c:if test="${c.code eq country}">
			<c:set var="currentCountry" value="${c}" />
		</c:if>	
	</c:forEach>
</select>
</c:otherwise>
</c:choose>
</c:catch>
<c:if test="${not empty error}">
	<c:out value="${error}"/>
</c:if>

<BR><BR>
<button type="button" onclick="showBack()" id="ReturnButton"><fmt:message key="button.back"/></button>
<input type="submit" name="submit" value="<fmt:message key="button.next"/>"/>

<BR><BR>
<HR>
The following settings are for testing purposes and will not be part of the Virtual Console.
<BR><BR>
Region<BR>
<select name="region" size="1" id="regionList" onchange="changeRegion()">
	<option value="EU">EU</option>
	<option value="JP">JP</option>
	<option value="US">US</option>
</select>
<BR>Current region: <c:out value="${region}" />

<BR><BR>

<c:catch var="error">
<c:choose>
<c:when test="${empty currentCountry}">
No country selected
</c:when>
<c:when test="${currentCountry.languageCount eq '0'}">
No languages found for country <c:out value="${country.code}" />
</c:when>
<c:otherwise>
language<BR>
<select name="langLocale" size="1" id="languageList" onchange="changeLanguage()">
<c:forEach items="${currentCountry.languages}" var="lang">
	<%
		String lang = (String) pageContext.getAttribute("lang");
    	java.util.Locale languageLocale = new java.util.Locale(lang);
    	String langName = languageLocale.getDisplayLanguage();
    	pageContext.setAttribute("langName", langName);
    %>
	<option value="<c:out value="${lang};${currentCountry.locales[lang]}"/>">
		<c:out value="${langName}" default="${lang}"/></option>
</c:forEach>	
</select>
<BR>Current language: <c:out value="${language}"/>, locale: <c:out value="${locale}" />
</c:otherwise>
</c:choose>
</c:catch>
<c:if test="${not empty error}">
	<c:out value="${error}"/>
</c:if>

<BR><BR>
Age: <input type="text" name="age" id="ageField"/>
<BR><BR>

</FORM>

</CENTER>

</body>
</pre>
<br>
  <p>TestSettings.jsp:</p>
<pre>
  <title>???settings.title???</title>
<SCRIPT language="JavaScript">
	function initPage()
	{	
		initPageCommon();
		initCommonFields("commonFields");
		showTestSettings();
	}
	
	function showSelectedOption(listId, value)
	{
		var list = document.getElementById(listId);
		if (list != null) {
			list.selectedIndex = -1;
			for (i = 0; i < list.options.length; i++) {
				var option = list.options[i];					
				if (option.value == value) {
					list.selectedIndex = option.index;
					return list.selectedIndex;
				}
			}
		}
		return null;
	}

	function setDefault(listId)
	{
		var list = document.getElementById(listId);
		if (list != null) {
			if (list.options.length > 0) {
				list.selectedIndex = 0;
				return list.selectedIndex;
			}
		}
		return null;
	}

	function showTestSettings()
	{
		var agefield = document.getElementById("ageField");
		if (agefield != null) {
			agefield.value = '';			
		}
		var ind;
		ind = showSelectedOption("regionList", 'USA');
		ind = showSelectedOption("countryList", 'US');
		if (ind == null) {
			ind = setDefault("countryList");
			if (ind >= 0) {
				changeCountry();
			}
		} 
		ind = showSelectedOption("languageList", 'en;en_US');
		
		if (ind == null) {
			ind = setDefault("languageList");
			if (ind >= 0) {
				changeLanguage();
			}
		}
	}

	function changeRegion()
	{
		var regionlist = document.getElementById("regionList");
		if (regionlist != null) {
			var region = regionlist.options[regionlist.selectedIndex].value;
			ec.setRegion(region);				
			replacePage("TestSettings.jsp?region=" + region);
		}
	}

	function changeLanguage()
	{
		var languagelist = document.getElementById("languageList");
		if (languagelist != null) {
			var s = languagelist.options[languagelist.selectedIndex].value;
			var i = s.indexOf(';');
			var language = s.substr(0, i);
			var locale = s.substr(i+1);
			ec.setLanguage(language);
			replacePage("TestSettings.jsp?language=" + language + "&locale=" + locale);
		}
	}

	function changeCountry()
	{
		var countrylist = document.getElementById("countryList");
		if (countrylist != null) {
			var country = countrylist.options[countrylist.selectedIndex].value;
			ec.setCountry (country);
			replacePage("TestSettings.jsp?country=" + country);
		}
	}

	function validate()
	{
		var submitOK = true;

		var agefield = document.getElementById("ageField");
		if (agefield != null) {
			var age = agefield.value;
			if (age.length > 0 && (isNaN(age)||age<1||age>100))
			{
				alert("The age must be a number between 1 and 100");
				submitOK = false;
 			} else {
				ec.setAge(age);
			}
		}
		
		return submitOK;
	}

</SCRIPT>
</head>

<body onload="initPage()">
<center>
<H2>Thanks you for visiting the online store</H2>

<TABLE width="60%">
<BR>
</TABLE>
</center>

</body>
</pre>
<br>
<a href="https://wiibrew.org/wiki/Accessing_Wii_Shop_Channel_from_PC">guide to access the wii shop on browser</a>
  
<br><br><h2>&copy; Nintendo, 2005/6. i do not own these files.</h2>










