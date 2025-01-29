> **⚠️ NOTIFICATION: You may experience a delay in receiving a response from the server due to server spin-downs by our cloud services.**

Functional Overview of the Service

![sudeto-read-time drawio](https://github.com/user-attachments/assets/819c36e6-a387-4e98-8777-4e52af97ef92)

## What is ReadTime Estimation Service?

The Content ReadTime Estimation Service is a tool for calculating the estimated reading time of a static blog or any web content in any language based on metadata like character, word, and space count.

Whether you're a content creator, developer, or marketer, our API / service makes the process effortless.

### Who Can Use ReadTime API?

- **Non-Developers**: You don’t need to be a coding expert! Use our API without worrying about technical complexities. Simply integrate the pre-built CDN link into your website, and you're ready to go.

- **Developers:** Prefer control over your API calls? We've got you covered with direct API access.


# Get started in 3 steps
### 1. Add the CDN Script

Paste the code below in your `<head>` tag of your web page

```html
<script src="https://cdn.jsdelivr.net/gh/sudeto/cdn-deliver@main/read-time/1.1.0/api-client.js"
integrity="sha384-zhLifh6TFfyzkTZgZl1tiXDYrzgyQkGZhOjvqmkpkLqD5H/z/Gse1ZWsnp1YY2re" crossorigin="anonymous" defer></script>
```
> ⚠️ Important: Do not make any changes in the integrity value of the above code (SRI) & use `1.1.0` version of the script only to avoid mistakes
> 
> If you don't know what is SRI, please read about it [here](https://developer.mozilla.org/en-US/blog/securing-cdn-using-sri-why-how/).

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

Since the service only returns a number (time in minutes) customise the text in the template literal and also convert minutes to hours!
```
`${res} Mins` or `${res} MIN READ`
```


### And that's it!
The ReadTime API Service will read the content by only parsing the readable text from your blog, compute the estimated time needed to read your blog, and return the number in minutes.

![image](https://github.com/user-attachments/assets/e9e79f19-b3d6-4746-a1a5-134a7ba00a57)


## API Docs
Check out our [API Documentation](https://sudeto-services.onrender.com/api-docs/) to interact with our API with sample data, and check sample responses
> **⚠️ NOTIFICATION: You may experience a delay in opening our API Docs page due to server spin-downs by our cloud services.**

## Sample Request & Response
#### REQUEST

`POST /api/read-time/v1` 
```json
{
  "character_count": 4500,
  "word_count": 560,
  "space_count": 40
}
```

#### RESPONSE

STATUS CODE: 200
```JSON
{
  "estimated_read_time": 3
}
```


## Why Sudeto's ReadTime API Service?
- **Multi-language Support**. Based on simple heuristics, the service recognises the language and adjusts the WPM (Words Per Minute) rate for that language

- **No Payload Required**. Unlike most services, we don't ask for your content. With our simple metric system, we
  can calculate reading time with derived metadata.
  
- **Zero Maintenance**. Just add our script to your site, and we’ll handle the rest

- **Perfect for Everyone**. Whether you're a marketer, blogger, or developer, Sudeto's ReadTime API Service fits your needs.

## Contact Us
Email [Karan Kakati](mailto:karanpkofficial@gmail.com) to resolve any issue or if you need any clarification regarding integration.

## System Status
Visit [System Status Page](https://status-sudetoservices.onrender.com/) to check if this service is running.
