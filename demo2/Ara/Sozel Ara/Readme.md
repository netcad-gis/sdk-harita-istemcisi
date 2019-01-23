

## Sözel Ara

Netgis üzerinden spatial verileri aramak için "ol.nc.Util.getFeaturesFromNetgis" fonksiyonu kullanılır.

Arama sonrası bulunan feature listesini harita üzerinde highlight etmek için ol.nc.NetgisSearch.highlightFeatures fonksiyonu kullanılır.

    ol.nc.NetgisSearch.highlightFeatures({
        map: ncol3map,
        features: features,
    });


Feature listesinin harita üzerindeki konumuna gitmek için ol.Map objesinin getView.fit() fonksiyonu kullanılır.

    ncol3map.getView().fit(ol.nc.NetgisSearch._ncGAVectorLayer.getSource().getExtent(), ncol3map.getSize());


Highlight temizlemek için "ol.nc.NetgisSearch.clear" fonksiyonu kullanılır.

    ol.nc.NetgisSearch.clear();