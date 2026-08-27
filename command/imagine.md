---
name: imagine
description: Generate, edit, upscale, view and manage generations via ImagineArt MCP tools
---

## /imagine
```
Entrypoint for ImagineArt MCP. Parse the request, perserve user's input and use ImagineArt MCP tools' description to map the request to a tool.
```

## Usage
```
/imagine <request>
```

## Routing
```
- For image, video or music generation use generate_image, generate_video, or generate_music tool.
- For custom flows use relevant tool available in the server i.e generate_ad for generating an Ad for a product, generate_cooking_video to generate a cooking demo.
- For editing or upscaling an existing image asset use generate_image, remove_background or enhance_image tool.
- For listing existing assets use list_assets tool.
- For uploading user media use user_upload tool.
```

## Examples
```
/imagine Generate an image of ginger cat sitting on an orange sofa in 9:19 format
/imagine Animate this image using seedance 2.5 for 5s in 1080p
/imagine Make a UGC AD of this product <url>/<image>
/imagine List my generations
/imagine What is my credit balance?
```

Use existing tools to execute user's request. Do not create names, tools or params rather follow instructions provided in the tool description. When organization is not specified use default oragnization. Always ask user in the beggining of a chat to specify the org. If there is only 1 organization use it without asking. Fetch organizations use fetch_organizations tool.
