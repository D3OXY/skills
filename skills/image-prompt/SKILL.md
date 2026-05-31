---
name: image-prompt
description: Generate a prompt for an image generation model(gpt-image-2). Use when an image is requested by the user or you need an image to be generated and verify the image against your requirements.
---

# Image Prompt

Generate a prompt for an image generation model(gpt-image-2). Use when an image is requested by the user or you need an image to be generated and verify the image against your requirements. If variations or multiple images are requested, generate a prompt for each image, or mention how many times the image should be generated.

## Process

1. Analyze the user's request and understand the context and requirements.
2. Generate a prompt based on the context and requirements.
3. Return the prompt by creating a html file in the temporary directory. with copy button for each prompt. if multiple prompts are required in the session, include them all in the same html file.
4. Open the html file in the browser.
5. Return the url of the html file to the user.
6. Wait for the user to submit the generated images.
7. Once Submitted, Verify the image against your requirements and if not satisfied, generate a new prompt if required or ask the user to regenerate the image(s).

## Output Format

- Each prompt should be in a separate block.
- Each block should have a copy button.
- Each block should have Badges with the properties of the image. (Size, Aspect Ratio, Style etc..)
- Each block should have a "Open in ChatGPT" button. When clicked, it should open the prompt in the ChatGPT interface (temporary chat window).

## Must Have

- Use `html` file to return the prompt to the user.
- The prompt should include the following:
    - Size of the image (1024x1024, 2048x2048, 4096x4096, etc.)
    - Aspect Ratio of the image (16:9, 4:3, 1:1, etc.)
    - Style/Aesthetic of the image
    - Wether transparent background is required
    - Resolution of the image (4K, 8K, 16K, etc.)
    - Characteristics of the image (detailed, realistic, abstract, etc.)
    - Colors of the image (specific colors, color scheme, etc.)
    - Mood of the image (happy, sad, angry, etc.)
    - Theme of the image (nature, city, space, etc.)
    - Objects in the image (specific objects, objects in the scene, etc.)
    - Actions in the image (specific actions, actions in the scene, etc.)
    - Time of the image (specific time, time in the scene, etc.)
    - Location of the image (specific location, location in the scene, etc.)
    - People in the image (specific people, people in the scene, etc.)
    - Animals in the image (specific animals, animals in the scene, etc.)
    - Text in the image (specific text, text in the scene, etc.)
    - Icons in the image (specific icons, icons in the scene, etc.)
    - Logos in the image (specific logos, logos in the scene, etc.)
    - Brands in the image (specific brands, brands in the scene, etc.)
    - Products in the image (specific products, products in the scene, etc.)
    - Services in the image (specific services, services in the scene, etc.)
    - Technologies in the image (specific technologies, technologies in the scene, etc.)
    - Concepts in the image (specific concepts, concepts in the scene, etc.)
    - Emotions in the image (specific emotions, emotions in the scene, etc.)
    - Feelings in the image (specific feelings, feelings in the scene, etc.)
    - Themes in the image (specific themes, themes in the scene, etc.)
