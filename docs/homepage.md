# Classes

<div>
    <div id = "classesEntry">
        [Render classes and description here]
    </div>
    
</div>

<script>
    fetch("./metadata/bricks-css-classes.json").then(function (response){
        return response.json();
    }).then(function(object){
        const filtered = object.filter(data => 
            data._categoryData?.name
        );
        
        document.getElementById("classesEntry").innerHTML = filtered.map(cls => 
        `
            <div>
                <h1>${cls.name}</h1>
                <p><strong>Category:</strong> ${cls._categoryData?.name}</p>
                <p><strong>Description:</strong>${cls.description}</p>
            </div>
        `).join('');
    })
</script>