
![Tab Panel Örnek](https://raw.githubusercontent.com/netcad-gis/sdk-harita-istemcisi/master/img/tabPanel.png)



Tab panel içeriği html olarak hazırlanır.

    <div class="tab-pane _nctab-pane" id="_ncTabPanelTest" style="display:none">
        <h4 class="_nctab-title"></h4>
        <div class="_nctab-item-container">
            <h4 class="text-center">Hello World</h4>
            <p class="text-center"></p>
        </div>
    </div>
    

Tab paneli açmak için kullanılacak buton hazırlanır.

    <li id="_navLinkTest" style="display:none" _ncOrdinal="0">
        <a href="#_ncTabPanelTest" data-toggle="tab"><i class="icon-baslangic" aria-hidden="true"></i></a>
    </li>
 

Hazırlanan panel içeriğinin tab olarak eklenmesi için ol.nc.Util sınıfının addTabPanel fonksiyonu kullanılır.


    ol.nc.Util.addTabPanel("_navLinkTest", "_ncTabPanelTest");
 

Eklenen panelin aktif olması için setActiveTabPanel fonksiyonu kullanılır.


    ol.nc.Util.setActiveTabPanel("_navLinkTest", "_ncTabPanelTest", true);
 
