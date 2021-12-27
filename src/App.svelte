<script>
	console.log("hello");

	let filePath = "import";
	let fileName = "unnamed";

	let canCreate = false;
	let isInFile = false;

	function browse() {
		console.log("browse");
		filePath = document.getElementById("fileUpload").value;
		console.log(filePath);
		// if filePath is not empty or "Browse", then canCreate is true
		if (filePath != "Browse" && filePath != "") {
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
			isInFile = true;
		}
		else {
			console.log("cannotCreate");
			document.getElementById("needFile").style.display = "flex";
			isInFile = false;
		}
	}
</script>

<div class="App" id="App">
	{#if isInFile == true}
		<div class="projectFile" id="projectFile" style="text-align: center;">
			<h1 style="color: white;">{fileName}</h1>
			<h2 style="color: white;">{filePath}</h2>
		</div>
	{:else}
		<div class="importProject" id="importProject">
			<span class="pleaseImport" id="pleaseImport">please import a file</span>
			<label for="fileUpload" class="customFileUpload">
				{filePath}
			</label>
			<input id="fileUpload" type="file" on:change={browse}/>
			<button class="importProjectButton" on:click={openProject}>open <span class="hideProject">project</span></button>
			<span class="needFile" id="needFile">you need a file, please enter a file for your project. <br> if you dont know how to create a file please click "learn more".</span>
			<span class="learnMore">learn more</span>
		</div>
	{/if}
</div>

<style>
	.App {
		background: rgb(26, 26, 26);
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.importProject {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	.importProject .importProjectButton {
		text-align: center;
		background: rgba(255, 145, 0, 0.171);
		color: rgba(255, 255, 255, 0.466);
		border: solid 1px rgba(255, 145, 0, 0.171);
		border-radius: 5px;
		font-size: 20px;
		font-family: 'Roboto', sans-serif;
		outline: none;
		width: 15%;
		cursor: pointer;
	}

	.importProject .importProjectButton:hover {
		background: rgba(255, 145, 0, 0.37);
		color: rgb(255, 255, 255);
		box-shadow: 0 10px 17px rgba(0, 0, 0, 0.233);
	}

	.importProject .importProjectButton:active {
		background: rgba(255, 174, 68, 0.5);
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
		font-size: 1.05vw;
		font-family: 'Roboto', sans-serif;
		outline: none;
		width: 15%;
		padding: 7.5px 0px;
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
		cursor: pointer;
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