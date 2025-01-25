## What is ReadTime API Service?

The ReadTime API is a powerful tool designed to calculate the estimated reading time for any content of any language based on character count, word count, and space count.

Whether you're a content creator, developer, or someone looking for quick content insights, our API makes the process effortless.

### Who Can Use ReadTime API?

- **Non-Developers**: You don’t need to be a coding expert! Use our API without worrying about technical complexities. Simply integrate the pre-built CDN link into your website, and you're ready to go.

- **Developers:** Prefer control over your API calls? We've got you covered with direct API access.


# Get started in 3 steps
### 1. Add the CDN Script

Paste the code below in your `<head>` tag of your web page

```html
<script src="https://cdn.jsdelivr.net/gh/sudeto/cdn-deliver@main/read-time/1.1.0/api-client.js"
integrity="sha384-zhLifh6TFfyzkTZgZl1tiXDYrzgyQkGZhOjvqmkpkLqD5H/z/Gse1ZWsnp1YY2re"
crossorigin="anonymous" defer>
</script>
```
> Important: Do not make any changes in the integrity code [(SRI - Subresource Integrity)](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity)

### 2. Setup the following function calls

> Important: Before you setup the function calls, ReadTime API reads your blog content from a single HTML element so ensure that you wrap your content under a single element
> Like:
> ```html
> <article id="blog-wrapper">
>   <p>The quick brown fox jumps over the lazy dog</p>
></article>
> ```

Note the IDs (identifiers) of 

- **ID1**. Your single element containing the blog content, in our case `blog-wrapper`
  
- **ID2**. The element where you will be mentioning your blog's reading time, in our case `readTime`

Copy the below code as it is under your `<body>` of the document, and follow the instructions:
```html
<script>
    const readableText = document.getElementById("blog-wrapper").innerText; // replace current ID with yours (refer ID1 above)

    async function updateReadTime() {
        let res = await fetchReadTime(calculateMetrics(readableText));
        document.getElementById("readTime").innerText = `${res} Min Read`; // replace current ID with yours (refer ID2 above)
    }

    window.onload = updateReadTime;
</script>
```

### Adjust result according to your needs

Since the service only returns a number (time in minutes) ustomise text in the template literal, and also convert minutes to hours!
```
`${res} Mins` or `${res} MIN READ`
```


### And that's it!
The ReadTime API Service will read the content by only parsing the readable text from your blog, compute the estimated time needed to read your blog, and return the number in minutes.

![image](https://github.com/user-attachments/assets/e9e79f19-b3d6-4746-a1a5-134a7ba00a57)



## Need an API access? Got you covered!

### 1. Copy the code below either under `<script>` of your body or you can store it in an external JS file.

```javascript

const readableText = document.getElementById("blog-wrapper").innerText; // replace current ID with yours (refer ID1 above)

function calculateMetrics(content) {
    const wordsArray = content.split(/\s+/).filter(word => word.length > 0);

    const characterCount = content.replace(/\s+/g, "").length;
    const wordCount = wordsArray.length;
    const spaceCount = (content.match(/\s/g) || []).length;

    return { characterCount, wordCount, spaceCount };
}

async function fetchReadTime(metrics){

    const response = await fetch("https://sudeto-services.onrender.com/api/read-time/v1", {
        method: "POST",
        headers: {
            "Content-Type": "application/json",
        },
        body: JSON.stringify({
            character_count: metrics.characterCount,
            word_count: metrics.wordCount,
            space_count: metrics.spaceCount,
        }),
    });

    const data = await response.json();
    return data.estimated_read_time;
}

async function updateReadTime() {
        let res = await fetchReadTime(calculateMetrics(readableText));
        document.getElementById("readTime").innerText = `${res} Min Read`; // replace current ID with yours (refer ID2 above)
}

window.onload = async function () {
    await updateReadTime();
};

```


## Why Sudeto's ReadTime API Service?
- **Multi-language Support**. Based on simple heuristics, the service recognises the language and adjusts the WPM (Words Per Minute) rate for that language

- **No Payload Required**. Unlike most services, we don't ask for your content. With our simple metric system, we
  can calculate reading time with just a few numbers.
  
- **Zero Maintenance**. Just add our script to your site, and we’ll handle the rest

- **Perfect for Everyone**. Whether you're a marketer, blogger, or developer, Sudeto's ReadTime API Service fits your needs.
