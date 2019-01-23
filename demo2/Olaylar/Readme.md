# Olaylar

## ol.Map.ready

Jquery’nin $(document).ready fonksiyonu gibi bir kullanıma sahiptir. İstenilen sayıda çağrılabilir. Harita nesnesinin ayağa kaldırılması sona erdiğinde bu şekilde sıraya eklenen fonksiyonlar bir bir işletilir. 


    ncol3map.ready(function () {
        console.log("map ready");
    });


## ol.Map.componentsReady

Netgis Server Client için hazırlanmış özel componentlerin tamamı istemci tarafında yüklendikten sonra componentsReady olayı çağrılır

    ncol3map.componentsReady(function () {
        console.log("component ready");
    });

## Click

    ncol3map.on('singleclick', function(e){
        console.log(evt.coordinate);
    });
 
 
## Move

    ncol3map.on('moveend', function(e){
        console.log(ncol3map.getView().getCenter());
    });
