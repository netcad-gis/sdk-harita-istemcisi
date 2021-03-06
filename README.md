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
});  

 ```

SDK API’si OpenLayers API’si ile (http://openlayers.org/en/latest/apidoc/) birlikte kullanılmak üzere, daha çok Netgis Server’la iletişim sağlamak ve OpenLayers API’sinde eksik görülen utility ya da shorthand fonksiyonları sağlamak üzere tasarlanmıştır. Dokümanın bu kısmında, belli başlı API fonksiyonları, kullanım amaçları ile birlikte verilecektir:


## Handler Kavramı

İstemci tarafında handler kavramını, harita nesnesine bir ya da daha fazla interaction ekleyen sınıflar için kullanmaktayız. Örneğin çizim aracı bir handler’dır.

Handler nesneler, haritanın setCurrentHandler metodu ile haritaya eklenir. clearCurrentHandler ya da cleanUp fonksiyonlarıyla kaldırılırlar.

Handler nesnelerinin birer initialize ve clear metotları olabilir. setCurrentHandler sonrası initialize metodu otomatik çağrılır.

Haritanın cleanUp metodu veya clearCurrentHandler metodu çağrılırsa da handler’ın clear metodu otomatik çağrılır.

Initialize ve clear metotları ilk ayarları yapmak ve deaktivasyon öncesi temizlik yapmak için özel metotlardır.

**Örnek handler**
 
    ol.nc = ol.nc || {};
 
    ol.nc.ImarYapiHandler = function (params) {
       this.callbackFunction = params.callbackFunction;
       this.callbackParameters = params.callbackParameters;
 
 
       this.interaction = new ol.interaction.Draw({
             type: "Point",
             condition: window.isClientMobile ?
                    ol.events.condition.noModifierKeys :
                    function (event) {
                           return event.type == "pointerdown" && event.originalEvent.button == 0;
                    }
       });
 
 
       this.interaction.functionType = params.type;
 
 
       this.interaction.on("drawend", ol.nc.ImarYapiHandler.process);
 
 
       this.initialize = function () {
             ncol3map.addInteraction(this.interaction);
       }
 
 
       this.clear = function () {
             ncol3map.removeInteraction(this.interaction);
       }
    }


## Modidifer Kavramı

İstemci tarafında modifier kavramını, harita nesnesine herhangi bir interaction eklemeyen, ancak uygulamada görsel değişiklikler yapabilen statik nesneler için kullanmaktayız. Örneğin heatmap bileşeni bir modifier’dır.

Handler’ların aksine, haritaya birden fazla modifier aynı anda eklenebilir. Haritanın addModifier metoduyla modifier’lar eklenir.

Modifier’ların özel metodu clear’dır. Ayağa kalkma ve diğer tüm işlerini kendileri yönetirler ya da dışarıdan yönetilir.

Modifier’lar haritanın cleanup metodunda temizlenirler.

**Örnek modifier**

    ol.nc = ol.nc || {};
    ol.nc.ClusterExecutor = ol.nc.ClusterExecutor || {};
 
 
    ol.nc.ClusterExecutor.fillNccTables = function (getCategoriesResult) {
       getCategoriesResult["Category"].forEach(function (element) {
             if (element["CatParams"]["RefKeyword"] == "NCSPATIAL") {
                    $("#_ncclLayerName").append("<option value='" + element["CatParams"]["LayerName"] + "'>" + element["CatParams"]["CatName"] + "</option>");
             }
       });
       $("#_ncclLayerName")[0].selectedIndex = 0;
    }
 
 
    ol.nc.ClusterExecutor.clusterInstance = null;
 
 
    ol.nc.ClusterExecutor.clear = function () {
       $("#_ncclDistanceGroup").hide();
       ol.nc.ClusterExecutor.clusterInstance.clear();
    }
    ncol3map.addModifier(ol.nc.ClusterExecutor); 
