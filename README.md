No diretório de destino dos arquivos de tradução é possível ajustar os termnos conforme sua necessidade com qualquer editor de textos e depois compactar os arquivos.
> zip languages.zip *.properties
> curl http://localhost:8080/api/admin/datasetfield/loadpropertyfiles -X POST --upload-file languages.zip -H "Content-Type: application/zip"
> curl http://localhost:8080/api/admin/settings/:Languages -X PUT -d '[{"locale":"pt","title":"Português"},{"locale":"en","title":"English"}]'

No arquivo de configuração faces-config.xml altere o idioma preferencial para Português, salve e reinicie o serviço do Payara.
> nano /usr/local/payara6/glassfish/domains/domain1/applications/dataverse/WEB-INF/faces-config.xml
    <locale-config>
        <default-locale>pt</default-locale>
        <supported-locale>en</supported-locale>
    </locale-config>
