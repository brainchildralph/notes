```
一、基本概念：

RSSI：Received Signal Strength Indication接收的信號強度指示，無線發送層的可選部分，用來判定鏈接質量，以及是否增大廣播發送強度。

因為無線信號多為mW級別，所以對它進行了極化，轉化為dBm而已，不表示信號是負的。1mW就是0dBm，小於1mW就是負數的dBm數。

接收的信號強度指示：RSSI只是信號強度的一個指示值！ 

   指示體現在兩方面：

   1） RSSI的值對應的單位是dbm。  dbm(Decibel-milliwatts)：分貝毫瓦，表示某一功率與1mw的相對關係，數值x(dbm)與功率P（mw）的具體計算公式如下，


可以看出0.5毫瓦約為-3dbm。  所以RSSI並不是功率，db是分貝，實際上常常用來表示信噪比的單位。上面的dbm是一個帶用量綱（毫瓦）的兩個功率的比值的表示方法。這下徹底明白了為什麼RSSI的值對應的dbm值不具備物理意義了吧。

註：（關於dB與dBm） 

dB是一個純計數單位，dB = 10logX，可以輕易把一個很大的數表示出來，因為2倍就是3dB，10倍就是10dB，即2^n＝3*n dB，X = 1000000000000000= 10logX = 150 dB，便於表達。

dBm是一個表示功率絕對值的單位，計算公式為：10lg功率值/1mW。例如：如果發射功率為1mW，按dBm單位進行折算後的值應為：10 lg 1mW/1mW = 0dBm；對於40W的功率,則10 lg(40W/1mW)=46dBm。最常用的2W＝33dBm，20W＝43dBm。
dBm與dBm之間的差值就可以用dB來表示。比如46dBm-43dBm=3dB，表示40W功率是20W功率的2倍。

 

    2）無線局域網供應商可以按照私有的方式定義RSSI值。RSSI的範圍可由供應商自己選擇從0到最大值(小於等於255)，許多供應商在產品文檔和網站上中把RSSI的執行數值發佈出來，而有些供應商並沒有這麼做。因為RSSI指標的規定是私有的，在比較不同製造商的無線網卡的RSSI值時會出現兩個問題。首先，不同供應商可能選擇不同的RSSI最大值，例如A供應商可能選擇RSSI範圍從0到100，而B供應商選擇從0到30，於是A供應商表明當前信號為25時，B供應商針對相同信號可能表達為8。另外，A供應商製造的無線網卡使用了更多的指標，在評估信號和信噪比時可能會顯得更靈敏。


 
作者：麻子来了 
来源：CSDN 
原文：https://blog.csdn.net/sinat_22991367/article/details/61921223 
版权声明：本文为博主原创文章，转载请附上博文链接！

```
