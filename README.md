rybal.co.vu
===========

var home_page_url = location.href;  function showpageCount(json) { 	var thisUrl = home_page_url; 	var htmlMap = new Array(); 	var thisNum = 1; 	var postNum = 1; 	var itemCount = 0; 	var fFlag = 0; 	var eFlag = 0; 	var html = ''; 	var upPageHtml = ''; 	var downPageHtml = ''; 	for (var i = 0, post; post = json.feed.entry[i]; i++) { 		var timestamp1 = post.published.$t.substring(0, 19) + post.published.$t.substring(23, 29); 		timestamp = encodeURIComponent(timestamp1); 		var title = post.title.$t; 		if (title != '') { 			if (itemCount == 0 || (itemCount % pageCount == (pageCount - 1))) { 				if (thisUrl.indexOf(timestamp) != -1) { 					thisNum = postNum 				} 				if (title != '') postNum++; 				htmlMap[htmlMap.length] = '/search?updated-max=' + timestamp + '&amp;max-results=' + pageCount 			} 		} 		itemCount++ 	} 	for (var p = 0; p &lt; htmlMap.length; p++) { 		if (p >= (thisNum - displayPageNum - 1) &amp;&amp; p &lt; (thisNum + displayPageNum)) { 			if (fFlag == 0 &amp;&amp; p == thisNum - 2) { 				if (thisNum == 2) { 					upPageHtml = '&lt;span class="showpage">&lt;a href="/">' + upPageWord + '&lt;/a>&lt;/span>' 				} else { 					upPageHtml = '&lt;span class="showpage">&lt;a href="' + htmlMap[p] + '">' + upPageWord + '&lt;/a>&lt;/span>' 				} 				fFlag++ 			} 			if (p == (thisNum - 1)) { 				html += '&lt;span class="showpagePoint">' + thisNum + '&lt;/span>' 			} else { 				if (p == 0) { 					html += '&lt;span class="showpageNum">&lt;a href="/">1&lt;/a>&lt;/span>' 				} else { 					html += '&lt;span class="showpageNum">&lt;a href="' + htmlMap[p] + '">' + (p + 1) + '&lt;/a>&lt;/span>' 				} 			} 			if (eFlag == 0 &amp;&amp; p == thisNum) { 				downPageHtml = '&lt;span class="showpage"> &lt;a href="' + htmlMap[p] + '">' + downPageWord + '&lt;/a>&lt;/span>'; 				eFlag++ 			} 		} 	} 	if (thisNum > 1) { 		html = '' + upPageHtml + ' ' + html + ' ' 	} 	html = '&lt;div class="showpageArea">&lt;span style="COLOR: #000;" class="showpageOf"> Pages (' + (postNum - 1) + ')&lt;/span>' + html; 	if (thisNum &lt; (postNum - 1)) { 		html += downPageHtml 	} 	if (postNum == 1) postNum++; 	html += '&lt;/div>'; 	var pageArea = document.getElementsByName("pageArea"); 	var blogPager = document.getElementById("blog-pager"); 	if (postNum &lt;= 2) { 		html = '' 	} 	for (var p = 0; p &lt; pageArea.length; p++) { 		pageArea[p].innerHTML = html 	} 	if (pageArea &amp;&amp; pageArea.length > 0) { 		html = '' 	} 	if (blogPager) { 		blogPager.innerHTML = html 	} } function showpageCount2(json) { 	var thisUrl = home_page_url; 	var htmlMap = new Array(); 	var isLablePage = thisUrl.indexOf("/search/label/") != -1; 	var thisLable = isLablePage ? thisUrl.substr(thisUrl.indexOf("/search/label/") + 14, thisUrl.length) : ""; 	thisLable = thisLable.indexOf("?") != -1 ? thisLable.substr(0, thisLable.indexOf("?")) : thisLable; 	var thisNum = 1; 	var postNum = 1; 	var itemCount = 0; 	var fFlag = 0; 	var eFlag = 0; 	var html = ''; 	var upPageHtml = ''; 	var downPageHtml = ''; 	var labelHtml = '&lt;span class="showpageNum">&lt;a href="/search/label/' + thisLable + '?&amp;max-results=' + pageCount + '">'; 	var thisUrl = home_page_url; 	for (var i = 0, post; post = json.feed.entry[i]; i++) { 		var timestamp1 = post.published.$t.substring(0, 19) + post.published.$t.substring(23, 29); 		timestamp = encodeURIComponent(timestamp1); 		var title = post.title.$t; 		if (title != '') { 			if (itemCount == 0 || (itemCount % pageCount == (pageCount - 1))) { 				if (thisUrl.indexOf(timestamp) != -1) { 					thisNum = postNum 				} 				if (title != '') postNum++; 				htmlMap[htmlMap.length] = '/search/label/' + thisLable + '?updated-max=' + timestamp + '&amp;max-results=' + pageCount 			} 		} 		itemCount++ 	} 	for (var p = 0; p &lt; htmlMap.length; p++) { 		if (p >= (thisNum - displayPageNum - 1) &amp;&amp; p &lt; (thisNum + displayPageNum)) { 			if (fFlag == 0 &amp;&amp; p == thisNum - 2) { 				if (thisNum == 2) { 					upPageHtml = labelHtml + upPageWord + '&lt;/a>&lt;/span>' 				} else { 					upPageHtml = '&lt;span class="showpage">&lt;a href="' + htmlMap[p] + '">' + upPageWord + '&lt;/a>&lt;/span>' 				} 				fFlag++ 			} 			if (p == (thisNum - 1)) { 				html += '&lt;span class="showpagePoint">' + thisNum + '&lt;/span>' 			} else { 				if (p == 0) { 					html = labelHtml + '1&lt;/a>&lt;/span>' 				} else { 					html += '&lt;span class="showpageNum">&lt;a href="' + htmlMap[p] + '">' + (p + 1) + '&lt;/a>&lt;/span>' 				} 			} 			if (eFlag == 0 &amp;&amp; p == thisNum) { 				downPageHtml = '&lt;span class="showpage"> &lt;a href="' + htmlMap[p] + '">' + downPageWord + '&lt;/a>&lt;/span>'; 				eFlag++ 			} 		} 	} 	if (thisNum > 1) { 		if (!isLablePage) { 			html = '' + upPageHtml + ' ' + html + ' ' 		} else { 			html = '' + upPageHtml + ' ' + html + ' ' 		} 	} 	html = '&lt;div class="showpageArea">&lt;span style="COLOR: #000;" class="showpageOf"> Pages (' + (postNum - 1) + ')&lt;/span>' + html; 	if (thisNum &lt; (postNum - 1)) { 		html += downPageHtml 	} 	if (postNum == 1) postNum++; 	html += '&lt;/div>'; 	var pageArea = document.getElementsByName("pageArea"); 	var blogPager = document.getElementById("blog-pager"); 	if (postNum &lt;= 2) { 		html = '' 	} 	for (var p = 0; p &lt; pageArea.length; p++) { 		pageArea[p].innerHTML = html 	} 	if (pageArea &amp;&amp; pageArea.length > 0) { 		html = '' 	} 	if (blogPager) { 		blogPager.innerHTML = html 	} } var thisUrl = home_page_url; if (thisUrl.indexOf("/search/label/") != -1) { 	if (thisUrl.indexOf("?updated-max") != -1) { 		var lblname1 = thisUrl.substring(thisUrl.indexOf("/search/label/") + 14, thisUrl.indexOf("?updated-max")) 	} else { 		var lblname1 = thisUrl.substring(thisUrl.indexOf("/search/label/") + 14, thisUrl.indexOf("?&amp;max")) 	} } var home_page = "/"; if (thisUrl.indexOf("?q=") == -1 &amp;&amp; thisUrl.indexOf(".html") == -1) { 	if (thisUrl.indexOf("/search/label/") == -1) { 		document.write('&lt;script src="' + home_page + 'feeds/posts/summary?alt=json-in-script&amp;callback=showpageCount&amp;max-results=99999" >&lt;\/script>') 	} else { 		document.write('&lt;script src="' + home_page + 'feeds/posts/full/-/' + lblname1 + '?alt=json-in-script&amp;callback=showpageCount2&amp;max-results=99999" >&lt;\/script>') 	} }
