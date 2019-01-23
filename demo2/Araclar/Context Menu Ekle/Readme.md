## Context Menu Ekle

![Araçlar Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/addContextMenu.png)

Context menu eklemek için harita objesinin "addContextMenuItem" sınıfı kullanılır.

    ncol3map.addContextMenuItem({
        data: { ordinal: 7, seperator: true },
        text: "Test Menu",
        callback: function (evt) {
            alert(evt.coordinate);
        }
    });