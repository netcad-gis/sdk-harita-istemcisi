# sdk-harita-istemcisi
Bu repoda SDK harita istemcisine ait örnek API kullanımları bulunmaktadır.

# Netgis Server Harita İstemcisi

# Api ile neler yapılabilir?

- Kendi haritanızı oluşturulabilir
- Sıcaklık analizi yapılabilir
- Tematik harita üretilebilir
- Sözel veriler harita üzerinde görüntülenebilir
- Sade harita yapılabilir
- Gelişmiş harita yapılabilir
- Gelişmiş haritaya ek araçlar eklenebilir
- Harita üzerinde arama yapıp harici kaynaktan gelen veriler görüntülenebilir

![alt text](http://portal.netcad.com.tr/download/attachments/154894372/image2019-1-17%2011%3A50%3A47.png?version=1&modificationDate=1547715131263&api=v2)


# Genel Bakış

API kullanımında en önemli gereklilik harita nesnesine işaret eden değişkenin adının `ncol3map` olması gerekliliğidir. Netgis Server legacy fonksiyonlarının bir kısmının karşılanmasında scope ve OpenLayers’ın kendisinden kaynaklı sıkıntılar yaşanacağından sabit bir instance adına karar verilmiştir.

Kullanılacak harita nesnesinin adı mutlaka `ncol3map` olmalıdır.


  ```
var interactions = ol.interaction.defaults({ pinchRotate: false });
var ncol3map = new ol.Map({
       target: 'map',
       controls: [],
       interactions: interactions,
       loadTilesWhileInteracting: false,
       loadTilesWhileAnimating: false,
       layers: []
});  ```