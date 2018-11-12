# Auto Drawing Prouction Flow Diagram Tool
此工具可以藉由讀取生產線描述檔(.json)自動繪出此生產線的流程圖（Flow Diagram），可用於視覺化生產線模型以及MES監控頁面等用途使用

## 生產線描述檔（Production Line Description File）
生產線描述檔是一個用來描述生產線上的所有單元的描述檔，藉由這個檔案可以容易得了解整個生產線的組成
* 所有單元包含生產線上的所有工作站、其他站點（如輸送帶）及物流等
* 採用json格式儲存

以下是一小段片段範例，用來描述生產線上所有的工作站（範例中有s1,s2兩個工作站）
>     {
>       "production_line": {
>         "station": {
>           "s1": {
>             "Name": "s1",
>             "Text": "Initial Station"
>           },
>           "s2": {
>             "Name": "s2",
>             "Text": "Final Station"
>           }
>          },
>       ...
>     }

## 工作原理簡述
* 利用pandas套件讀取生產線描述檔，並對該json檔進行剖析萃取，以獲得必要的資料
* 藉由graphviz套件生成各個節點（Node）及流線（Flow），並填上上個步驟獲得的資料
* 輸出圖檔

## 此工具優勢
* 自動讀檔分析並繪圖，無須人工介入，盡可能貼近工業3.0以上之需求
* 即使生產線非常複雜，利用是透過讀取生產線描述檔繪圖的特性以及graphviz套件具備自動最佳化流程圖佈局的能力，仍可快速繪製出複雜的流程圖
