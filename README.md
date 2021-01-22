# open_graph_sample

大家在滑 FB 時常常會看到一些縮圖詭異的分享連結，或著是沒有縮圖跟介紹長得像是詐欺網頁的連結，今天我們就從技術的角度來了解這些連結到底發生了什麼事，同時檢視自己的網頁有沒有犯一樣的錯誤。

### 先了解元兇 OG 是什麼？

OG 全名 Open Graph Protocol，由 Facebook 提出，目的在於透過定義網站性質、Title、縮圖網址等等屬性，如果沒設定就是隨機產生的結果，這就是為什麼你看到很多詭異縮圖的原因。

### 看看 OG 從沒設定到完整設定給人的感覺吧
>讀者可以把連結貼上 FB 建立貼文的地方來看看結果喔

1. 如果完全沒設定 OG，你分享的連結根本沒人知道內容是什麼
    ![image](/img/README/none_open_graph.png)
    https://dean9703111.github.io/open_graph_sample/none_open_graph.html
2. 只設定標題就會有懷舊的詐騙網站既視感
    ![image](/img/README/only_title.png)
    https://dean9703111.github.io/open_graph_sample/only_title.html
3. 有了標題跟描述後就給人多一點安心的錯覺
    ![image](/img/README/title_description.png)
    https://dean9703111.github.io/open_graph_sample/title_description.html
4. 加上縮圖後網站的專業感直線上升
    ![image](/img/README/small_thumbnail.png)
    https://dean9703111.github.io/open_graph_sample/small_thumbnail.html
5. 依據不同的業務需求，在了解 OG 如何設定後你可以決定要使用大縮圖還是小縮圖
    ![image](/img/README/big_thumbnail.png)
    https://dean9703111.github.io/open_graph_sample/big_thumbnail.html


### OG 怎麼設定呢？

設定上真的毫無難度，先了解每個參數的含義
```html
<head>
    <meta property="og:url" content="你的網址"/>
    <meta property="og:locale" content="網站語系，ex:zh_TW" />
    <meta property="og:type" content="類型，ex：website" />
    <meta property="og:title" content="文章的標題" />
    <meta property="og:description" content="內容的簡短說明"/>
    <meta property="og:image" content="縮圖圖片連結" />
    <meta property="og:image:type" content="圖像的 MIME 類型，可為 image/jpeg、image/gif 或 image/png" />
    <meta property="og:image:width" content="縮圖 width" />
    <meta property="og:image:height" content="縮圖 height" />
</head>
```

瞭解參數函義後填上自己的資訊就好嚕，完整範例如下
```html
<head>
	<meta property="og:url" content="https://github.com/dean9703111/open_graph_sample" />
	<meta property="og:locale" content="zh_TW" />
	<meta property="og:type" content="website" />
	<meta property="og:description" content="相對於小縮圖而言，大縮圖能顯示的文字量是比較少的，所以圖片上的資訊更加重要" />
	<meta property="og:title" content="大縮圖分享連結" />
	<meta property="og:image:type" content="image/png" />
	<meta property="og:image"
		content="https://github.com/dean9703111/open_graph_sample/blob/master/img/big_thumbnail.png?raw=true" />
	<meta property="og:image:width" content="1400" />
    <meta property="og:image:height" content="770" />
</head>
```
如果你想要更深入的了解FB對這塊的定義請參考他們[給網站管理員的分享功能指南](https://developers.facebook.com/docs/sharing/webmasters?locale=zh_TW)

### 使用官方工具預覽確認元素
1. 進入 FB 提供的工具：https://developers.facebook.com/tools/debug/
2. 貼上自己的網址下下偵錯就能在下方看到預覽嚕
    ![image](/img/README/debug.png)
3. 如果發現顯示結果跟預期的不一樣，請觀看`應處理的警告`
    ![image](/img/README/debug2.png)
4. 處理完警告後就能看到美美的預覽圖嚕(fb:app_id可忽略)
    ![image](/img/README/debug3.png)
5. 如果發現設定都改了，為什麼預覽圖都還是有問題的化，請按`再次抓取`
    ![image](/img/README/debug4.png)

### 注意事項

1. FB 分享連結有分成大圖及小圖，比例如下
    * 0 x 0 ~ 199 x 199 **抓不到圖**
    * 200 x 200 ~ 599 x 314 **小圖**
    * 600 x 315 ~ 1500 x 1500 **大圖**
    * 1501 x 1501 以上 **小圖**
2. 特殊規則
    * 超過 1500 x 1500 會變成小圖喔！！！(之前我卡了很久)
    * 圖片大小不可超過 5MB 喔！
    * 如果你的圖片尺寸特殊(ex: 210 * 350)也會被 FB 判定為不合格的圖片，而且 FB 提示的訊息居然是：



