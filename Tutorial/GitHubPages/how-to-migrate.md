# how-to-migrate.md

## How to migrate from wiki to Github Pages

1. Create/prepare a repository: Under https://github.com/OpenChain-Project , create/prepare your repository. In this example, "OpenChain-JWG" is used.  
   
1. Create "docs" folder: After preparing "OpenChain-Project/OpenChain-JWG" repository, create "docs" folder.  
   Create "index.md": By using [jekyll](https://jekyllrb.com/), "index.md" is ftransformed from "index.html".  
   > [OpenChain tooling WG](https://www.openchainproject.org/news/2019/07/25/openchain-launches-tooling-work-group)のMLでも意見が出ていたと思うが、[reStructuredText](https://www.sphinx-doc.org/ja/master/usage/restructuredtext/basics.html)など、どのフォーマットが良いのかは議論の余地あり。  
1. Setting for GitHub Pages: The following instruction needs an admin attributen.
   1. OpenChain-JWGリポジトリのClick ```Settings``` tab in "OpenChain-JWG" repository.  
   ![settings](images/settings.png)  
   1. In Settings->Github Pages, change **```Source```** to **```master branch/docs folder```**.  
   ![source](images/docs.png)
   1. If you want, you can change theme of the page.  **```Change theme```** . In this example, [Cayman](https://pages-themes.github.io/cayman/) is used. 
   [docs/_config.yml](https://github.com/NorioKobota/OpenChain-JWG/blob/master/docs/_config.yml) Other settings can be refered in [Github Pagesのヘルプ](https://help.github.com/ja/github/working-with-github-pages/about-github-pages-and-jekyll), and jekyll  
   ![themes](images/themes.png)
1. Create contents of your Website in the "docs" folder. index.md, etc.  
Note: GitHub Pages has folder size limitation 1GB. [Github Pagesを試用するためのガイドライン](https://help.github.com/ja/github/working-with-github-pages/about-github-pages) 
   ```GitHub Pages ソースリポジトリには、1GB の推奨上限があります。```  
  It is recommended to place text only files in the "docs" folder, and large size files like images should be placed in other folders. 
Note: It is easy and useful to use Emoji instead of an image file.[Emoji](https://unicode.org/emoji/charts/full-emoji-list.html)。 **```Code```** に記載された文字コードが、```U+1F600```の場合は、```&#x1F600;```と記載することによって、絵文字が出ます。  
Note: Photos are not allowed to store in GitHub. 
1. An example of repository structure:  
   ```
   OpenChain-JWG +- docs-------+- index.md  
                 |             +- meetings   
                 |             +- subgroups   
                 |             +- outcomes    
                 +- Onboarding : 今まで通り  
                 +- General    : 今まで通り  
   ```
## EOF
