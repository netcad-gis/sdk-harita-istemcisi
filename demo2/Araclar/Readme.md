
# Araçlar

Araçları aktif hale getirmek için "ol.Map" objesinin "initNGS" fonksiyonu yüklenirken visualOptions parametresi ile gerekli tanımların yapılması gerekiyor.


![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclar.png)


    ncol3map.initNGS(_startupParameters,
        {
            loadComponents: true,
            leftPanel: true,
            toolbar: true,
            layerManager: true,
            overviewMap: true,
            zoom: true,
            scaleLine: true
        },
        function (sucessResult) {
            console.debug(sucessResult);
        },
        function (errorResult) {
            console.debug(errorResult);
        }
    );


### loadComponents

Netgis server harita istemcisi için hazırlanmış özel componentlerin yüklenmesi sağlanır.

### leftPanel

Sol panel aktif edilir.

![Araçlar Toolbar](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclar2.png)

### toolbar

Üst araç çubukları aktif edilir.

![Araçlar Toolbar](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclartoolbar.png)

### layerManager

Kategori ağacı aktif edilir.

![Araçlar Toolbar](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclarLayermanager.png)

### overviewMap

Genel bakış panelin aktif edilir.

![Araçlar Toolbar](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclarOverview.png)


### zoom

Yakınlaşma/Uzaklaşma aracı aktif edilir.

![Araçlar Toolbar](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclarzoom.png)


### scaleLine

Ölçek bar aktif edilir.

![Araçlar Toolbar](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/araclarScaleline.png)
