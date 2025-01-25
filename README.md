## What is ReadTime API?

The ReadTime API is a powerful tool designed to calculate the estimated reading time for any content based on character count, word count, and space count.

Whether you're a content creator, developer, or someone looking for quick content insights, our API makes the process effortless.

### Who Can Use ReadTime API?

- [x]  **Non-Developers**: You don’t need to be a coding expert! Use our API without worrying about technical complexities. Simply integrate the pre-built CDN link into your website, and you're ready to go.

- [x]  **Developers:** Prefer control over your API calls? We've got you covered with direct API access.


# Get started in 3 steps
### 1. Add the CDN Script

Paste the code below in your `<head>` tag of your web page

```html
<script src="https://cdn.jsdelivr.net/gh/sudeto/cdn-deliver@main/read-time/1.1.0/api-client.js" integrity="sha384-zhLifh6TFfyzkTZgZl1tiXDYrzgyQkGZhOjvqmkpkLqD5H/z/Gse1ZWsnp1YY2re" crossorigin="anonymous" defer></script>
```

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
        document.getElementById("readTime").innerText = `${res} Min read`; // replace current ID with yours (refer ID2 above)
    }

    window.onload = updateReadTime;
</script>
```


## Why Sudeto's Read Time Service?
- [x]  **No Payload Required**. Unlike most services, we don't ask for your content. With our simple metric system, we
  can calculate reading time with just a few numbers.
  
- [x]  **Zero Maintenance**. Just add our script to your site, and we’ll handle the rest

- [x]  **Perfect for Everyone**. Whether you're a marketer, blogger, or developer, Sudeto's Read Time Service fits your needs.
