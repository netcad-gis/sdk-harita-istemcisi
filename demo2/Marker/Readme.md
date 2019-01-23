# Bilgi Balonu

Eklenen marker seçildiğinde bilgi balonu açıp içerik göstermenin iki farklı yöntemi bulunmaktadır.

## Info Card

Marker seçildiğinde, içeriğin pencerenin sağına dayalı şekilde görüntülenmesi sağlanır.


![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/markerInfoCard.png)

    var marker = ncol3map.addMarker({
        coordinate: pnt.getCoordinates(),
        showInfoCard: true,
        content: 'hello world',
        title : 'my title'
    });

## Popup

Marker seçildiğinde, içeriğin popup olarak harita üzerinde görüntülenmesi sağlanır.

![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/markerPopup.png)


    var marker = ncol3map.addMarker({
        coordinate: pnt.getCoordinates(),
        showPopup: true,
        content: 'hello world',
        title : 'my title'
    });



## Bilgi balonu içeriği

Bilgi balonu içeriği üç farklı yöntem ile hazırlanabilir.

- Html içerik
- Url (iframe)
- Netgis veri sözlüğü