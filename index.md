---
deployed_app: https://script.google.com/macros/s/AKfycbwf0JYoX-SCa3p3nWRJ0DinLXenfsqr1_LY9glfl4IfHsTlj7c/exec
fields: 
  - name: name
    input_type: text
    placeholder: Name
    required: true
  - name: email
    input_type: email
    placeholder: Email address
    required: true
  - name: sex
    input_type: radio
    placeholder: male
    required: true
  - name: sex
    input_type: radio
    placeholder: female
    required: true
  - name: message
    input_type: textarea
    placeholder: Message
    required: false
  - name: terms
    input_type: checkbox
    placeholder: I accept the terms and conditions
    required: true
  - name: submit
    input_type: submit
    placeholder: Submit form
    required: true
---


<script src="https://code.jquery.com/jquery-3.4.1.js" integrity="sha256-WpOohJOqMqqyKL9FccASB9O0KwACQJpFTUBLTYOVvVU=" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-serialize-object/2.5.0/jquery.serialize-object.min.js" integrity="sha512-Gn0tSSjkIGAkaZQWjx3Ctl/0dVJuTmjW/f9QyB302kFjU4uTNP4HtA32U2qXs/TRlEsK5CoEqMEMs7LnzLOBsA==" crossorigin="anonymous"></script>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.css" integrity="sha384-AfEj0r4/OFrOo5t7NnNe46zW/tFgW6x/bCJG8FqQCEo3+Aro6EYUG4+cU+KJWu/X" crossorigin="anonymous">

<script defer src="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.js" integrity="sha384-g7c+Jr9ZivxKLnZTDUhnkOnsh30B4H0rpLUpJ4jAIKs4fnJI+sEnkvrMWph2EDg4" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/contrib/auto-render.min.js" integrity="sha384-mll67QQFJfxn0IYznZYonOWZ644AWYC+Pt2cHqMaRhXVrursRwvLnLaebdGIlYNa" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>


# Quiz

<form>

  {% for field in page.fields %}
    <label>{{ field.name }}</label>
    <br/>
    <input name="{{ field.name }}" />
    <br/>
  {% endfor %}


  <button id="submit-form">Submit</button>

</form>


<script>
$('#submit-form').on('click', function(e) {
  e.preventDefault();
  var jqxhr = $.ajax({
    url: '{{ page.deployed_app }}',
    method: "GET",
    dataType: "json",
    data: $('form').serializeObject()
  }).success(
    alert("GREAT SUCCESS")
    // do something
  );
})
</script>
