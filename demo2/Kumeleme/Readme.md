# Kümeleme

![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/Kumeleme.png)


    var testc = new ol.nc.Cluster({
        map: ncol3map
    });

    testc.executeCluster({
        layerName: "geoyol",
        distance: 10,
        plotFeatures: true
    });