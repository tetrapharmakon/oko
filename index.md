---
layout: default
deployed_app: https://script.google.com/macros/s/AKfycbwf0JYoX-SCa3p3nWRJ0DinLXenfsqr1_LY9glfl4IfHsTlj7c/exec
fields: 
  - name: full_name
    type: text
    label: Full name
  - name: email
    type: text
    label: Email
  - name: q_1
    type: text
    label: >
      Ma tipo $\sum_{x=0}^\infty \frac{1}{x}$
  - name: q_2
    type: choice
    label: >
      Ma tipo $\sum_{x=0}^\infty \frac{1}{x}$
    options:
      - value: 1
        label: >
          $1$
      - value: 2
        label: >
          $\infty$
      - value: 3
        label: >
          $\omega$
---

# Quiz

<form>

  {% for field in page.fields %}

    <div class="input-group">
    {% case field.type %}
      {% when "text" %}
        <label>{{ field.label }}</label>
        <input name="{{ field.name }}" />
      {% when "choice" %}
        <label>{{ field.label }}</label>
        {% for option in field.options %}
          <div class="option-group">
            <input type="radio" name="{{ field.name }}" value="{{ option.value }}">
            <label for="{{ field.name }}">{{ option.label }}</label>
          </div>
        {% endfor %}
    {% endcase %}
    </div>

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
