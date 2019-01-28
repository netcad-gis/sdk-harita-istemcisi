## Spatial Ara

Spatial arama yapabilmek için geometry objesine ihtiyacımız bulunuyor.

X ve Y koordinatları ile Point geometry objesini oluşturuyoruz,

    var geom = new ol.geom.Point([494780.449218749, 4426020.35156249]);


Spatial arama işlemini Netgis ile yapacağımız için geometry objesini GML formatına dönüştürüyoruz,

    //Gelen geometrinin OGC kriteri oluşturulur.
    var criteria = "<Intersects>" +
                        "<PropertyName>Geometry</PropertyName>" +
                        ol.nc.Util.getNetgisGML(ncol3map, geom) + //Geometrinin GML metni oluşturulur.
                    "</Intersects>";    


Ve Netgis getinfo servisini çağırıyoruz,


    ol.nc.Util.getInfoFromNetgis(
    {
        layerName: 'geomahalle',
        filter: criteria,
        maxRecordCount: 100,
        webgisUrl: ncol3map.get("startupParameters").getWebgisUrl(),
        workspaceName: ncol3map.get("startupParameters")["Workspace"],
        sessionId: ncol3map.get("startupParameters")["SessionId"],
        successFunction: function (result, context) {
            //Dönen veri xml'e çevirilir.
            result = $.parseXML(result.documentElement.firstChild.nodeValue);
            //Xml verisindeki "Data" etiketinde dönen kayıtlar yer alır.
            $data = $(result).find("Data");
            if ($data.length == 0 || $data.children().length == 0) {
                return;
            }
        },
    });