## Araç Ekle

Yeni bir araç oluşturmak için "ol.control.ToolbarElement" sınıfı kullanılır.


![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/aracEkle.png)


    var newt = new ol.control.ToolbarElement({
        map: ncol3map,
        title: "Test",
        className: "icon-konum-gir",
        callbackFunction: function (params) {
            
            alert(params.message);
            
        },
        callbackParameters: {
            message: "Harita üzerinden bir konum seçin"
        },
        sticky: true,
        ordinal: 7
    });

Oluşturulan yeni araç harita objesinin "addToolbarElement" fonksiyonu ile arayüze eklenir.

    ncol3map.addToolbarElement(newt );


Yeni araç seçildiğinde harita üzerinden bir işlem başlatmak için harita objesinin setCurrentHandler sınıfı kullanılır.


    ncol3map.setCurrentHandler(new selectMapBegin(params));


Harita üzerinde bir konumun seçilebilmesi için çizim işlemi başlatıyoruz .

    function selectMapBegin(e){
        this.interaction = new ol.interaction.Draw({
            type: "Point",
            condition: window.isClientMobile ?
                ol.events.condition.noModifierKeys :
                function (event) {
                    return event.type == "pointerdown" && event.originalEvent.button == 0;
                }
        });
        this.interaction.on("drawend", selectMapEnd);
        
        this.initialize = function () {
            ncol3map.addInteraction(this.interaction);
        }
        this.clear = function () {
            ncol3map.removeInteraction(this.interaction);
        }
    }
    
    function selectMapEnd(e){
        alert(e.feature.getGeometry().getCoordinates());
    }