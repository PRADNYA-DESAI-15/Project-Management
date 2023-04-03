# Project-Management
<!DOCTYPE html>


<head>
<title>Bootstrap Example</title>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<link rel="stylesheet"
	href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
	
	<script
		src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
	<script
		src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>

<body>
	<div class="container">
	<h2>Project Management Form</h2>
		<form id="empForm" method="post">
	<div class="form-group">
		<span><label for="Project-Id">Project ID:</label></span>
		<input type="text" class="form-control" name="Project-Id" id="Project-Id" placeholder="Enter Project ID" required>
 	</div>

	<div class="form-group">
		<label for="Project-Name">Project Name:</label>
		<input type="text" class="form-control" id="Project-Name" placeholder="Enter Project Name" name="Project Name">
	</div>

	<div class="form-group">
		<label for="Assigned-To">Assigned To</label>
		<input type="text" class="form-control" id="Assigned-To" placeholder="Enter Assigned date" name="Assigned To">
	</div>

	<div class="form-group">
		<label for="Assignment-Date">Assignment Date</label>
		<input type="text" class="form-control" id="Assignment-Date" placeholder="Enter Assignment Date" name="Assignment Date">
	</div>

	<div class="form-group">
		<label for="Deadline">Deadline</label>
		<input type="text" class="form-control" id="Deadline" placeholder="Enter Deadline" name="Deadline">
	</div>

	<input type="button" class="btn btn-primary" id="empSave" value="Save" onclick="savedetails();">
	<input type="button"  id="empSave" value="Reset" onclick="resetForm();">
	<input type="button"  id="empSave" value="Change" onclick="ChangeData();">
</form>

</div>


<script>
	$("#Project-Id").focus();
	function validateAndGetFormData() {
		var Project-IdVar = $("#Project-Id").val();
		if (Project-IdVar === "") {
		alert("Project ID Required Value");
		$("#Project-Id").focus();
		return "";
		}

		var Project-NameVar = $("#Project-Name").val();
		if (Project-NameVar === "") {
		alert("Project Name is Required Value");
		$("#Project-Name").focus();
		return "";
		}
	
		var Assigned-ToVar = $("#Assigned-To").val();
		if (Assigned-ToVar === "") {
		alert("Assigned-To is Required Value");
		$("#Assigned-To").focus();
		return "";
		}

		var Assignment-DateVar = $("#Assignment-Date").val();
		if (Assignment-DateVar === "") {
		alert("Assignment-Date is Required Value");
		$("#Assignment-Date").focus();
		return "";
		}

		var DeadlineVar = $("#Deadline").val();
		if (DeadlineVar === "") {
		alert("Deadline is Required Value");
		$("#Deadline").focus();
		return "";
		}

		var jsonStrObj = {
		Project-Id: Project-IdVar,
		Project-Name: Project-NameVar,
		Assigned-To: Assigned-ToVar,
		Assignment-Date: Assignment-DateVar,
		Deadline: DeadlineVar,
		};
	
	return JSON.stringify(jsonStrObj);
	}


function createPUTRequest(connToken, jsonObj, dbName, relName) {
	var putRequest = "{\n"
		+ "\"token\" : \""
		+ connToken
		+ "\","
		+ "\"dbName\": \""
		+ dbName
		+ "\",\n" + "\"cmd\" : \"PUT\",\n"
		+ "\"rel\" : \""
		+ relName + "\","
		+ "\"jsonStr\": \n"
		+ jsonObj
		+ "\n"
		+ "}";
	return putRequest;
	}

  	function executeCommand(reqString, dbBaseUrl, apiEndPointUrl) {
		var url = dbBaseUrl + apiEndPointUrl;
		var jsonObj;
		$.post(url, reqString, function (result) {
		jsonObj = JSON.parse(result);
		}).fail(function (result) {
		var dataJsonObj = result.responseText;
		jsonObj = JSON.parse(dataJsonObj);
		});
		return jsonObj;
		}

		function resetForm() {
		$("#Project-Id").val("")
		$("#Project-Name").val("");
		$("#Assiged-To").val("");
		$("#Assignment -Date").val("");
		$("#Deadline").val("");
		$("#Project-Id").prop("disabled", false);
		$("#save").prop("disabled", true);
		$("#change").prop("disabled", true);
		$("#reset").prop("disabled", true);
		$("#Project-Id").focus();
		}

   		function savedetails() {
		var jsonStr = validateAndGetFormData();
		if (jsonStr === "") {
		return;
		}
		
		function ChangeData() {
		$(change).prop("disabled", true);
		validateData();
		var updateRequest createLPDATERecordRequest(connToken, jsonChg, empDBNane, empRelationName, localStorage.getItem("
		jQuery.ajaxSetup({async: false));
		var resJsonObj = executeCommandAtGivenBaseUrl(updateRequest, jpdbBaseUR, JpdbIML); 
		jQuery.ajaxSetup({async: true});
		console.log(resJsonObj);
		resetForm();
		$('#Project-Id').focus();
		}
		



		var putReqStr = createPUTRequest("90932909|-31949282325612047|90948073",
		jsonStr, "Project", "Project-REL");
		alert(putReqStr);
		jQuery.ajaxSetup({async: false});
		var resultObj = executeCommand(putReqStr,
		"http://api.login2explore.com:5577", "/api/iml");
		alert(JSON.stringify(resultObj));
		jQuery.ajaxSetup({async: true});
		resetForm();
		}
</script>
</body>
</html>
