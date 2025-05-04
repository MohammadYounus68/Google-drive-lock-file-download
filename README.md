# Google-drive-lock-file-download
google drive lock file jut pdf file download free

1. first lock file open and inspact open (ctlr+shift+L)
2. then console runt this code but first time error
3. then read (allow pasting)
4. let trustedURL;
if (window.trustedTypes && trustedTypes.createPolicy) {
	// Create a trusted policy for the script URL
	const policy = trustedTypes.createPolicy('myPolicy', {
    	createScriptURL: (input) => input
	});
	trustedURL = policy.createScriptURL('https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.2/jspdf.min.js');
} else {
	console.warn("Trusted Types are not supported in this browser. Falling back to using a plain URL.");
	trustedURL = 'https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.2/jspdf.min.js';
}

let jspdf = document.createElement("script");
jspdf.onload = function () {
	// Create the PDF document once jsPDF is loaded
	let pdf = new jsPDF();
	let elements = document.getElementsByTagName("img");
	for (let i in elements) {
    	let img = elements[i];
    	if (!/^blob:/.test(img.src)) {
        	continue;
    	}
    	let canvasElement = document.createElement('canvas');
    	let con = canvasElement.getContext("2d");
    	canvasElement.width = img.width;
    	canvasElement.height = img.height;
    	con.drawImage(img, 0, 0, img.width, img.height);
    	let imgData = canvasElement.toDataURL("image/jpeg", 1.0);
    	pdf.addImage(imgData, 'JPEG', 0, 0);
    	pdf.addPage();
	}
	pdf.save("download.pdf");
};

// Use the trusted URL as the script source
jspdf.src = trustedURL;
document.body.appendChild(jspdf);

//past this  code and auto download your pdf file
