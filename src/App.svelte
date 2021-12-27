<script>
	console.log("hello");

	let fileName = "import";

	let file = "0";
	let reader = "0";

	let canCreate = false;
	let isInFile = false;

	function browse() {
		console.log("browse");
		fileName = document.getElementById("fileUpload").files[0].name; ;
		console.log(fileName);
		// if filePath is not empty or "Browse", then canCreate is true
		if (fileName != "Browse" && fileName != "") {
			canCreate = true;
			document.getElementById("pleaseImport").style.display = "none";
		}
		else {
			canCreate = false;
		}
	}

	function openProject() {
		console.log("openProject");
		if (canCreate) {
			var file = document.getElementById("fileUpload").files[0];
			if (file) {
				// if file has extension .opendo
				if (file.name.endsWith(".opendo") || file.name.endsWith(".od")) {
					var reader = new FileReader();
					reader.readAsText(file, "UTF-8");
					isInFile = true;
					reader.onload = function (evt) {
						document.getElementById("fileContents").innerHTML = evt.target.result;
					}
					reader.onerror = function (evt) {
						document.getElementById("fileContents").innerHTML = "error reading file, please retry";
					}
				}
				else {
					document.getElementById("needOpenDo").style.display = "flex";
				}
			}
		}
		else {
			console.log("cannotCreate");
			document.getElementById("needFile").style.display = "flex";
			isInFile = false;
		}
	}

	function goBack() {
		console.log("goBack");
		fileName = "import";

		file = "0";
		reader = "0";

		canCreate = false;
		isInFile = false;

		document.getElementById("fileContents").innerHTML = "";
		document.getElementById("needFile").style.display = "none";
		document.getElementById("pleaseImport").style.display = "flex";
	}
</script>

<svelte:head>
	{#if isInFile == true}
		<title>OpenDo / {fileName}</title>
	{:else}
		<title>OpenDo / Import</title>
	{/if}
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/svelte-bulma@latest/dist/svelte-bulma.min.css">
</svelte:head>

<div class="App" id="App">
	{#if isInFile == true}
		<div class="projectFile" id="projectFile" style="text-align: center;">
			<div class="header">
				<div class="goBack" on:click={goBack}>go back</div>
				<div class="title">{fileName}</div>
				<div class="siteInfo">
					<div class="siteName">OPEN DO</div>
					<img src="./favicon.png" alt="icon">
				</div>
			</div>
			<div class="body">
				<div id="fileContents" class="fileContents">
					loading...
				</div>
			</div>
		</div>
	{:else}
		<div class="importProject" id="importProject">
			<div class="siteInfo">
				<img src="./favicon.png" class="icon" alt="icon">
				<span class="title">OPEN <span class="titleSpecial">DO</span></span>
				<span class="desc">A fully open source, modular and customizable todo list app. </span>
				<a href="https://github.com/bietlxn/OpenDo" class="githubSource">github</a>
			</div>
			<span class="pleaseImport" id="pleaseImport">please import a file</span>
			<label for="fileUpload" class="customFileUpload">
				{fileName}
			</label>
			<input id="fileUpload" type="file" on:change={browse}/>
			<button class="importProjectButton" on:click={openProject}>open <span class="hideProject">project</span></button>
			<span class="needFile" id="needFile">you need a file, please enter a file for your project.</span>
			<span class="needOpenDo" id="needOpenDo">you need a file with the extension .opendo or .od, please enter a new file for your project.</span>
			<a href="https://github.com/bietlxn/OpenDo/blob/main/CreatingFiles.md" class="learnMore">learn more</a>
		</div>
	{/if}
</div>

<style>
	.App {
		background: rgb(26, 26, 26);
	}

	.projectFile .header {
		display: flex;
		position: absolute;
		width: 100vw;
		align-items: center;
		padding: 10px 0px;
		background: rgb(20, 20, 20);
		color: white;
	}

	.projectFile .header .goBack {
		color: rgba(255, 255, 255, 0.747);
		cursor: pointer;
		background: rgba(255, 255, 255, 0.062);
		border: solid 1px rgba(255, 255, 255, 0.068);
		border-radius: 5px;
		height: 100%;
		padding: 10px 30px;
		margin-left: 20px;
	}

	.projectFile .header .goBack:hover {
		color: white;
		background: rgba(255, 255, 255, 0.288);
		border-color: rgba(255, 255, 255, 0.288);
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.233);
	}

	.projectFile .header .goBack:active {
		background: rgba(255, 255, 255, 0.473);
		border-color: rgba(255, 255, 255, 0.473);
		box-shadow: 0 0px 0px transparent;
	}

	.projectFile .header .siteInfo {
		display: flex;
		align-items: center;
		margin-left: auto;
		margin-right: 20px;
	}

	.projectFile .header .siteInfo .siteName {
		font-weight: bolder;
		float: right;
		margin-right: 10px;
		letter-spacing: 2px;
	}

	.projectFile .header .siteInfo img {
		width: 40px;
		height: 40px;
		border-radius: 50%;
		margin-right: 10px;
	}

	.projectFile .fileContents {
		color: white;
		margin: 100px;
		padding: 10px;
		width: 50%;
		background: rgba(255, 255, 255, 0.062);
		border: solid 1px rgba(255, 255, 255, 0.068);
		border-radius: 5px;
		height: calc(100vh - 100px);
		overflow-y: scroll;
	}

	.projectFile .header .title {
		color: rgba(255, 255, 255, 0.747);
		text-align: center;
		justify-content: center;
		align-items: center;
		font-weight: bold;
		margin-left: 30px;
	}

	.projectFile .body {
		width: 100%;
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	.importProject {
		width: 100vw;
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	.importProject .siteInfo {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
		margin-bottom: 10px;
		padding: 15px;
		border-bottom: solid 1px rgba(255, 255, 255, 0.068);
	}

	.importProject .siteInfo .icon {
		width: 100px;
		height: 100px;
		border-bottom: solid 1px rgba(255, 255, 255, 0.068);
	}

	.importProject .title {
		font-size: 40px;
		letter-spacing: 6px;
		font-weight: bold;
		color: rgb(255, 255, 255);
	}

	.importProject .titleSpecial {
		background: linear-gradient(90deg, rgb(46, 189, 255) 0%,rgb(255, 31, 240)100%);
		background-clip: text;
		color: transparent;
	}

	.importProject .desc {
		font-size: 20px;
		letter-spacing: 1px;
		color: rgba(255, 255, 255, 0.555);
	}

	.importProject .githubSource {
		color: rgba(255, 255, 255, 0.397);
		text-decoration: none;
		font-size: 17px;
		letter-spacing: 3px;
		margin-top: 2px;
	}

	.importProject .githubSource:hover {
		background: linear-gradient(90deg, rgb(46, 189, 255) 0%,rgb(255, 31, 240)100%);
		background-clip: text;
		text-decoration: underline;
	}

	.importProject .importProjectButton {
		text-align: center;
		background: rgba(255, 255, 255, 0.219);
		color: rgba(255, 255, 255, 0.822);
		border: solid 0px;
		border-radius: 5px;
		font-size: 20px;
		font-family: 'Roboto', sans-serif;
		outline: none;
		width: 15%;
		cursor: pointer;
	}

	.importProject .importProjectButton:hover {
		background: rgb(0, 174, 255);
		background: linear-gradient(90deg, rgb(0, 143, 209) 0%, rgb(218, 0, 203)100%);
		color: rgb(255, 255, 255);
		box-shadow: 0 10px 17px rgba(0, 0, 0, 0.233);
	}

	.importProject .importProjectButton:active {
		background: rgb(0, 174, 255);
		background: linear-gradient(90deg, rgb(38, 139, 185) 0%, rgb(196, 61, 187)100%);
		color: rgb(255, 255, 255);
		box-shadow: 0 0px 0px rgba(0, 0, 0, 0.233);
	}

	.importProject input[type="file"] {
		display: none;
	}

	.importProject .customFileUpload {
		max-width: 15%;
		text-align: center;
		background: rgba(255, 255, 255, 0.082);
		color: rgba(255, 255, 255, 0.37);
		border: solid 1px rgba(255, 255, 255, 0.082);
		border-radius: 5px;
		font-size: 20px;
		font-family: 'Roboto', sans-serif;
		outline: none;
		width: 15%;
		padding: 6px 0px;
		cursor: pointer;
		margin: 10px;
	}
	
	.importProject .customFileUpload:hover {
		background: rgba(255, 255, 255, 0.24);
		color: rgb(255, 255, 255);
		box-shadow: 0 10px 17px rgba(0, 0, 0, 0.233);
	}

	.importProject .learnMore {
		color: rgba(255, 255, 255, 0.267);
		font-size: 18px;
		cursor: pointer;
	}

	.importProject .learnMore:hover {
		color: rgba(255, 255, 255, 0.801);
		text-decoration: underline;
	}

	.importProject .needFile {
		position: relative;
		display: none;
		color: rgba(255, 124, 124, 0.514);
		font-size: 16px;
	}

	.importProject .needOpenDo {
		position: relative;
		display: none;
		color: rgba(255, 124, 124, 0.514);
		font-size: 16px;
	}

	.importProject .pleaseImport {
		color: rgba(255, 255, 255, 0.267);
		font-size: 17px;
	}

	@media only screen and (max-width: 1635px) {
		.importProject .hideProject {
			display: none;
		}
	}
</style>