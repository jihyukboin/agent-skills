# Recipe (Recipe)

[Source: Naver Search Advisor](https://searchadvisor.naver.com/guide/structured-data-recipe)

###  Recipe

* Displays recipe information.
![image](https://searchadvisor-phinf.pstatic.net/MjAyNjEwMTVfMTg4/MDAxNzkyMDQxMzk2NDMz.XpGjNlDCHhPcnU5TCTZm8dYtCuZadGrFpq5kiQUaQP4g.V_sdjGo5oXRq3S3AKZU-qp_ulV4QTdlGH3pkRCJ-L_cg.PNG/%EC%9B%B9%EB%A7%88%EC%8A%A4%ED%84%B0_%EB%A0%88%EC%8B%9C%ED%94%BC_%EC%98%88%EC%8B%9C%ED%99%94%EB%A9%B4.png)
> The image above is an example of what may appear in search results. The actual search results may differ from the actual search results.
> This information can be used auxiliary to web document analysis, etc., like other structured markup, and is not guaranteed to be exposed in the relevant content or format.


### Recipe

#### basic guidelines
* Please do not write it under HowTo property.
 #### Image Guidelines
* Please use images of the finished dish that best represent the recipe.
* Please use the original image, not a thumbnail, etc.
* Please avoid duplication between images.
* Please avoid using logos, default images, or broken images.
#### Types and Properties
  [Recipe](https://schema.org/Recipe) defined by schema.org is used and the property values ​​below must be specified.

| attribute | Required? | explanation |
| --- | --- | --- |
| name | Not required | This is the recipe title. |
| image | Not required | This is a recipe image.|
| recipeYield | Not required | The amount of dishes. Please enter a number or “numeric unit”. (Unit example: serving) |
| totalTime | Not required | This is the total cooking time.  Please write in [ISO-8601 duration](https://schema.org/Duration) format. (Example: PT30M)  |
| recipeIngredient | Not required | These are the ingredients for the recipe.  Please enter them one by one. Please do not enter metadata such as order information.|
| recipeInstruction | **essential** | Here is a step-by-step explanation of the recipe. Please enter them one by one. Please do not enter metadata such as order information. |


* Example implemented in JSON-LD format
```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "김치찌개 레시피",
  "image": "https://example.com/photos/recipe_sample.jpg",
  "recipeYield": "2 servings",
  "totalTime": "PT30M",
  "recipeIngredient": [
    "신김치 1그릇",
    "식용유 2스푼",
    "대파 1뿌리",
    "참치 1캔",
    "물 500ml",
    "고추가루 1스푼"
  ],
  "recipeInstructions": [
    {"@type":"HowToStep","text":"냄비에 김치를 넣는다."},
    {"@type":"HowToStep","text":"김치 위에 식용유를 뿌리고 약불에서 볶는다."},
    {"@type":"HowToStep","text":"볶은 김치에 참치를 넣고 함께 볶는다."},
    {"@type":"HowToStep","text":"물을 넣고 끓인다."},
    {"@type":"HowToStep","text":"끓는 김치찌개에 대파를 넣고 추가로 끓인다."},
    {"@type":"HowToStep","text":"고추가루를 넣고 끓인 후 마무리한다."},
  ]
}
</script>
```

* Example implemented in Microdata format
```html
<div itemscope itemtype="https://schema.org/Recipe">
  <span itemprop="name">김치찌개 레시피</span>
  <img itemprop="image" src="https://example.com/photos/recipe_sample.jpg" />
  <span itemprop="recipeYield">2 servings</span>
  <meta itemprop="totalTime" content="PT30M">
  <span itemprop="recipeIngredient">신김치 1그릇</span>
  <span itemprop="recipeIngredient">식용유 2스푼</span>
  <span itemprop="recipeIngredient">대파 1뿌리</span>
  <span itemprop="recipeIngredient">참치 1캔</span>
  <span itemprop="recipeIngredient">물 500ml</span>
  <span itemprop="recipeIngredient">고추가루 1스푼</span>
  <span itemprop="recipeInstructions">냄비에 김치를 넣는다.</span>
  <span itemprop="recipeInstructions">김치 위에 식용유를 뿌리고 약불에서 볶는다.</span>
  <span itemprop="recipeInstructions">볶은 김치에 참치를 넣고 함께 볶는다.</span>
  <span itemprop="recipeInstructions">물을 넣고 끓인다.</span>
  <span itemprop="recipeInstructions">끓는 김치찌개에 대파를 넣고 추가로 끓인다.</span>
  <span itemprop="recipeInstructions">고추가루를 넣고 끓인 후 마무리한다.</span>
</div>
```
