tinyGS = (function(global) {
	//Cria a função gtag
	global.dataLayer = global.dataLayer || [];

	var conversionId = null;

	function extractUrlValue(key, url) {
		if (typeof(url) === 'undefined') {
			url = window.location.href;
		}

		var match = url.match('[?&]' + key + '=([^?&]+)');
		return match ? match[1] : null;
	}

	function gtag() {
		global.dataLayer.push(arguments);
	}

	function getOwnScript(ownUrl) {
		var scripts = document.getElementsByTagName("script");
		for (var i = 0; i < scripts.length; i++) {
			if (scripts[i].src && scripts[i].src.indexOf(ownUrl) >= 0) {
				return scripts[i];
			}
		}
	}

	function addAsyncScript(url) {
		var scriptGlobal = document.createElement("script");
		scriptGlobal.src = url;
		scriptGlobal.async = true;

		var head = document.getElementsByTagName("head")[0];
		head.appendChild(scriptGlobal);
	}

	function run() {
		var script = getOwnScript("https://tiny-google-snippets.s3-sa-east-1.amazonaws.com/nuvemshop/global.js");
		if (script) {
			conversionId = extractUrlValue("conversion_id", script.src);

			addAsyncScript("https://www.googletagmanager.com/gtag/js?id=" + conversionId);

			gtag('js', new Date());
			gtag('config', conversionId);
		}
	}

	function getConversionId() {
		return conversionId;
	}

	run();

	return {
		extractUrlValue: extractUrlValue,
		getOwnScript: getOwnScript,
		gtag: gtag,
		getConversionId: getConversionId
	}
})(window);
