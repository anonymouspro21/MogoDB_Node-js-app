<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>MongoDB Sample</title>
</head>

<body>
    <input type="text" placeholder="Search" id="search" />
    <button id="btn">Search</button>
    <pre>
        <code id="code"></code>
    </pre>

    <script>
        const btn = document.getElementById("btn");
        const code = document.getElementById("code");
        const search = document.getElementById("search");

        btn.addEventListener("click", async() => {
            code.innerText = "loading";

            const res = await fetch(
                "/get?search=" + encodeURIComponent(search.value)
            );
            const json = await res.json();

            code.innerText = "\n" + JSON.stringify(json, null, 4);
        });
    </script>
</body>

</html>
