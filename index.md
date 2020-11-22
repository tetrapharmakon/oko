---
layout: default
deployed_app: https://script.google.com/macros/s/AKfycbwf0JYoX-SCa3p3nWRJ0DinLXenfsqr1_LY9glfl4IfHsTlj7c/exec
fields: 
  - name: full_name
    label: Full name
  - name: email
    label: Email
  - name: q_1
    label: >
      Ma tipo $\sum_{x=0}^\infty \frac{1}{x}$
---

# Quiz

<form>

  {% for field in page.fields %}
    <label>{{ field.label }}</label>
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
