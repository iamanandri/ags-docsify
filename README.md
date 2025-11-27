# Classes


<div>
    <form>
        <input id="classSearch" type="text" class="custom-input" placeholder="Enter class name"/>
    </form>
    <div id = "classesEntry">
        [Render classes and description here]
    </div>
    
</div>

<script>
    const search = document.getElementById("classSearch");
    search.addEventListener("change", () => {
        console.log("successful!");
    });

    fetch("/metadata/bricks-css-classes.json").then(function (response){
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