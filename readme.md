### Single Variable
Example
```html
<!-- name = "Peter" -->
<p>{{ var|name }}</p>
```

Will produce
```html
<p>Peter</p>
```

### Indexed Variable
Example
```html
<!-- names = ["Peter", "Parker", "Molly"] -->
<p>{{ var|names|2 }}</p>
```

Will produce
```html
<p>Molly</p>
```

### Function Call
Example
```html
<!-- function returns "Peter" -->
<p>{{ func|getName }}</p>
```

Will produce
```html
<p>Peter</p>
```

### Function Call with Parameters
Example
```html
<!-- function returns name + age -->
<p>{{ func|getNameAndAge|<string>"Peter",<int>37 }}</p>
```

Will produce
```html
<p>Peter, 37</p>
```

### Function Call with Parameters, using Reflection
Example
```html
<!-- function returns name + age -->
<p>{{ func|getNameAndAge|"Peter",37 }}</p>
```

Will produce
```html
<p>Peter, 37</p>
```

### Check if Variable Exists
Example
```html
<!-- name exists and is "Peter" -->
<p>{% if name %}Hi {{ var|name }}{% end %}</p>
```

Will produce
```html
<p>Peter</p>
```

### Check if Multiple Variables Exists
Example
```html
<!-- name exists and is "Peter", age does not exist -->
<p>{% if name && age %}Hi {{ var|name }}, {{ var|age }}{% end %}</p>
```

Will produce
```
<p></p>
```

### Reverse If-Check
Example
```html
<!-- name does not exist -->
<p>{% !if name %}Something something darkside..{% end %}</p>
```

Will produce
```html
<p>Something something darkside..</p>
```

### Check if Variable is Equal to Something
Example
```html
<!-- name is "Peter" -->
<p>{% if name == "Peter" %}Hi Peter{% end %}</p>
```

Will produce
```html
<p>Peter</p>
```

### Check if Multiple Variables are Equal to Something
Example
```html
<!-- name is "Peter", age is 27 -->
<p>{% if name == "Peter" && age == 37 %}Hi Peter{% end %}</p>
```

Will produce
```html
<p>Peter</p>
```

### Reverse If-Check
Example
```html
<!-- name is "Parker" -->
<p>{% if name != "Peter" %}Where did Peter go?{% end %}</p>
```

Will produce
```html
<p>Where did Peter go?</p>
```

### If and Else
Example
```html
<!-- name is "Peter" -->
<p>{% if name %}Variable exists and is {{ var|name }}{% else %}Variable does not exists{% end %}</p>
```

Will produce
```html
<p>Peter</p>
```

### Do a Loop
Example
```html
<!-- people = ["Peter", "Parker", "Molly"] -->
<ul>
{% loop people %}
	<li>{{ var|%index }}</li>
{% end %}
</ul>
```

Will produce
```html
<ul>
	<li>Peter</li>
	<li>Parker</li>
	<li>Molly</li>
</ul>
```

### Do a Fixed Loop
Example
```html
<!-- people = [{name: "Peter"}, {name: "Parker"}, {name: "Molly"}] -->
<ul>
{% loop people steps 0,1 %}
	<li>{{ var|name }}</li>
{% end %}
</ul>
```

Will produce
```html
<ul>
	<li>Peter</li>
	<li>Parker</li>
</ul>
```

### Do a Nested Loop
Example
```html
<!-- companies = [{name: "Microsoft", people = ["Peter", "Parker"]},
                  {name: "Apple", people = ["Molly", "Holly"]}] -->
{% if companies %}<ul>{% end %}
{% loop companies %}
	<li>
		<h1>{{ var|name }}</h1>
		{% if people %}<ul>{% end %}
		{% loop people %}
			<li>{{ var|%index }}</li>
		{% end %}
		{% if people %}</ul>{% end %}
	</li>
{% end %}
{% if companies %}</ul>{% end %}
```

Will produce
```html
<ul>
	<li>
		<h1>Microsoft</h1>
		<ul>
			<li>Peter</li>
			<li>Parker</li>
		</ul>
	</li>
	<li>
		<h1>Apple</h1>
		<ul>
			<li>Molly</li>
			<li>Holly</li>
		</ul>
	</li>
</ul>
```