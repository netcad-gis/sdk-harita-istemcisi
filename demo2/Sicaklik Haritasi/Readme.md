# Sıcaklık Haritası


![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/SicaklikHaritasi.png)

Sıcaklık analizi yapmak için öncelikle "ol.nc.Heatmap" objesinden oluşturmak gerekiyor.

    var testh = new ol.nc.Heatmap({
                            map: ncol3map
                        });
 

Heatmap objesi oluşturulduktan sonra executeHeatmap fonksiyonu çağrılır.

    testh .executeHeatmap({
        layerName: "layername",
        columnName: "columname",
        radius: 10,
        blur: 10,
        plotFeatures: true
    });
