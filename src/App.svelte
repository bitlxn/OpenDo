<script>
	let fileLocation = "Browse Location";
	let fileName = "";

	function browseResult(){
		var fileInput = document.getElementById('fileInput');
		fileLocation = fileInput.value;
		console.log(fileLocation);
	}

	function createFile() {
		const fileNameHtml = document.getElementById("fileName");
		// if something is typed in the input box
		if (fileNameHtml.value != "") {
			document.getElementById("needName").style.display = "none";


		}
		else {
			document.getElementById("needName").style.display = "flex";


			return;
		}
	}
</script>

<div class="App" id="App">
	<div class="createProject">
		<input type="text" name="fileNameInputName" class="fileNameInput" id="fileName" placeholder="type name of project here">
		<input type="file" onchange="browseResult(event)" id="fileInput" class="fileInput">
		<button class="createProjectButton" on:click={createFile}>Create <span class="hideProject">Project</span></button>
		<span class="needName" id="needName">You need a name, please enter a name for your project.</span>
		<span class="importFile">import a file</span>
	</div>
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

	.createProject {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	.createProject .fileNameInput {
		width: 15%;
		text-align: center;
		height: 50px;
		border: none;
		border-bottom: 1px solid rgba(255, 255, 255, 0.13);
		background: transparent;
		color: rgb(255, 255, 255);
		font-size: 20px;
		font-family: 'Roboto', sans-serif;
		outline: none;
	}

	.createProject .fileNameInput:focus {
		border-bottom: 1px solid rgba(255, 255, 255, 0.452);
	}

	.createProject .fileNameInput:placeholder-shown {
		color: rgba(255, 255, 255, 0.466);
	}

	.createProject .fileInput {
		background: transparent;
		color: rgba(255, 255, 255, 0.466);
		border: solid 1px rgba(255, 255, 255, 0.13);
		border-radius: 5px;
		outline: none;
		width: 15%;
		cursor: pointer;
	}

	.createProject .fileInput:hover {
		background: rgba(255, 255, 255, 0.2);
		color: rgb(255, 255, 255);
		box-shadow: 0 10px 17px rgba(0, 0, 0, 0.233);
	}

	.createProject .fileInput:active {
		background: rgba(255, 255, 255, 0.466);
		color: rgb(255, 255, 255);
		box-shadow: 0 0px 0px rgba(0, 0, 0, 0.233);
	} 

	.createProject .fileInput:focus {
		background: rgba(255, 255, 255, 0.308);
		color: rgba(255, 255, 255, 0.836);
		box-shadow: 0 0px 0px rgba(0, 0, 0, 0.233);
	} 

	.createProject .createProjectButton {
		text-align: center;
		background: rgba(255, 255, 255, 0.13);
		color: rgba(255, 255, 255, 0.466);
		border: solid 1px rgba(255, 255, 255, 0.13);
		border-radius: 5px;
		font-size: 20px;
		font-family: 'Roboto', sans-serif;
		outline: none;
		width: 15%;
		cursor: pointer;
	}

	.createProject .createProjectButton:hover {
		background: rgba(255, 255, 255, 0.2);
		color: rgb(255, 255, 255);
		box-shadow: 0 10px 17px rgba(0, 0, 0, 0.233);
	}

	.createProject .createProjectButton:active {
		background: rgba(255, 255, 255, 0.466);
		color: rgb(255, 255, 255);
		box-shadow: 0 0px 0px rgba(0, 0, 0, 0.233);
	}

	.createProject .importFile {
		color: rgba(255, 255, 255, 0.267);
		font-size: 18px;
		cursor: pointer;
	}

	.createProject .importFile:hover {
		color: rgba(255, 255, 255, 0.801);
		text-decoration: underline;
	}

	.createProject .needName {
		position: relative;
		display: none;
		color: rgba(255, 124, 124, 0.514);
		font-size: 16px;
		cursor: pointer;
	}

	@media only screen and (max-width: 1635px) {
		.createProject .fileNameInput:placeholder-shown {
			color: transparent;
		}
		
		.createProject .hideProject {
			display: none;
		}
	}

</style>