## Ajuste os termnos conforme sua necessidade e depois compacte os arquivos:
    zip languages.zip *.properties

## Use esse comando para inserir os arquivos no Dataverse: 
    curl http://localhost:8080/api/admin/datasetfield/loadpropertyfiles -X POST --upload-file languages.zip -H "Content-Type: application/zip"

## Use esse comando para que seja possível selecionar o novo idioma:
    curl http://localhost:8080/api/admin/settings/:Languages -X PUT -d '[{"locale":"pt","title":"Português"},{"locale":"en","title":"English"}]'

## Para que o idioma PT-BR seja o padrão altere o arquivofaces-config.xml:
    nano /usr/local/payara6/glassfish/domains/domain1/applications/dataverse/WEB-INF/faces-config.xml

    <locale-config>
        <default-locale>pt</default-locale>
        <supported-locale>en</supported-locale>
    </locale-config>
## Reinicie o serviço do Payara para que as alterações tenham efeito:
    /usr/local/payara6/glassfish/bin/asadmin stop-domain
    /usr/local/payara6/glassfish/bin/asadmin start-domain
