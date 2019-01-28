

# Tematik

Tematik yapmak için "ol.nc.Thematic.thematicFeatures()" collection oluşturulur.

Her bir tematik kriteri için "ol.Feature()" oluşturularak setProperties fonksiyonu ile attribute tanımı yapılarak collection'a eklenir.


    var thematicFeature = new ol.Feature();
    var properties = {};
    properties['COLUMNNAME'] = 'THEME1';
    thematicFeature.setProperties(properties)
    thematicFeatures.features.push(thematicFeature);
 

Tematik kriterleri belirlendikten sonra stil tanımı yapmak için "ol.nc.Thematic.thematicStyle()" objesi oluşturulur.

    var thematicStyle = new ol.nc.Thematic.thematicStyle();
    //Tematik yapılan kayıtlarda görüntülenecek etiket belirlenir.
    thematicStyle.label = 'THEME1';
    //Tematik stiline girecek kayıtları süzmek için kriter belirlenir.
    thematicStyle.criteria = '[#COLUMNNAME]=="THEME1"';
    //Tematik yapılan kayıtların görüntüleneceği stil belirlenir.
    thematicStyle.style = new ol.style.Style({
        fill: new ol.style.Fill({
            color: 'rgba(110,207,246, 0.7)'
        }),
        stroke: new ol.style.Stroke({
            color: 'rgba(110,207,246, 1)',
            width: 5
        }),
        text: new ol.style.Text({
            fill: new ol.style.Fill({
                color: 'rgba(110,207,246, 1)'
            })
        })
    });
 

"applyThematic" fonksiyonu ile tematik işlemi başlatılır.

    ol.nc.Thematic.applyThematic(thematicStyles, thematicFeatures);
 