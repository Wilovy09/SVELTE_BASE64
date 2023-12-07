<script>
    let Base64String = '';
    function uploadImage(){
        let file = document.querySelector('input[type=file]').files[0];
        let reader = new FileReader();

        reader.onload = function(){
            Base64String = reader.result.replace("data", "").replace(/^.+,/, "");
        }
        reader.readAsDataURL(file);
    }
    function showBase64(){
        const showTextArea = document.getElementById('base64result');
        showTextArea.value = Base64String;
    }
</script>

<h1>Convert Image to Base64</h1>
<form>

    <input type="file" id="fileId" on:change={uploadImage} name="resume">
    <textarea name="" id="base64result" cols="30" rows="10"></textarea>
    <button type="button" on:click={showBase64}>Encode</button>

</form>
<br>
<img src="data:image/jpeg;base64,{Base64String}" alt="IMAGEN">