---
title: Ajouter une source de données à un test de performances de site Web
description: Découvrez comment lier des données pour fournir différentes valeurs au même test, par exemple, pour fournir des valeurs différentes à vos paramètres de publication de formulaire.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761002"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Ajouter une source de données à un test de performances de site Web

Liez les données pour fournir différentes valeurs au même test, par exemple, pour fournir différentes valeurs à vos paramètres de publication de formulaire.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Lier les données à un test des performances de site web](../test/media/web_test_databinding_conceptual.png)

Nous allons utiliser un exemple d'application ASP.NET. Elle contient trois pages *.aspx* : la page par défaut, une page rouge et une page bleue. La page par défaut a une case d'option pour choisir Rouge ou Bleu et un bouton Envoyer. Les deux autres pages *.aspx* sont simples. L'une a une étiquette nommée Rouge et l'autre a une étiquette nommée Bleu. Lorsque vous choisissez Envoyer sur la page par défaut, nous affichons l'une des autres pages. Vous pouvez télécharger l’exemple [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) ou simplement suivre les étapes avec votre propre application web.

![Exécution de l'application web à tester](../test/media/web_test_databinding_runwebapp.png)

Votre solution doit également inclure un test de performances web qui parcourt les pages de l’application web.

![Solution avec le test des performances de site web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Créer une base de données SQL

::: moniker range="vs-2017"

1. Si vous n’avez pas Visual Studio Enterprise, vous pouvez le télécharger à partir de la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

2. Crée une base de données SQL.

     ![Ajouter une nouvelle base de données SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Créer un projet de base de données.

     ![Créer un projet à partir de la base de données](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Ajouter une table au projet de base de données.

     ![Ajouter une nouvelle table au projet de base de données](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Ajoutez des champs à la table.

     ![Ajouter des champs à la table](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publiez le projet de base de données.

     ![Publier le projet de base de données depuis l'Explorateur de solutions](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Ajoutez des données aux champs.

     ![Ajouter des données aux champs](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Si vous n’avez pas Visual Studio Enterprise, vous pouvez le télécharger à partir de la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads).

2. Crée une base de données SQL.

     ![Ajouter une nouvelle base de données SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Créer un projet de base de données.

     ![Créer un projet à partir de la base de données](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Ajouter une table au projet de base de données.

     ![Ajouter une nouvelle table au projet de base de données](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Ajoutez des champs à la table.

     ![Ajouter des champs à la table](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publiez le projet de base de données.

     ![Publier le projet de base de données depuis l'Explorateur de solutions](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Ajoutez des données aux champs.

     ![Ajouter des données aux champs](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Ajouter la source de données

1. Ajoutez une source de données.

     ![Ajouter la source de données au test des performances de site web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Choisissez le type de source de données et nommez-le.

     ![Nommer la source de la base de données](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Créez une connexion.

     ![Choisir un nouvelle connexion](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Entrez les détails de connexion.

     ![Entrer les propriétés de connexion de la base de données SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Sélectionnez la table que vous souhaitez utiliser pour votre test.

     ![Ajouter la table des couleurs en tant que source de données](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     La table est liée au test.

     ![Le nœud Source de données est ajouté au test des performances de site web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Enregistrez le test.

## <a name="bind-the-data"></a>Lier les données

1. Liez le champ **ColorName**.

     ![Lier le champ ColorName à la valeur RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Ouvrez le fichier *Local.testsettings* dans **l’Explorateur de solutions** et sélectionnez l’option **Une exécution par ligne de source de données**.

     ![Modifiez le fichier de paramètres de test.](../test/media/web_test_databinding_sql_testsettings.png)

3. Enregistrez le test de performances de site Web.

## <a name="run-the-test-with-the-data"></a>Exécuter le test avec les données

1. Exécutez le test.

     ![Exécuter le test des performances de site web pour vérifier la liaison](../test/media/web_test_databinding_sql_runtest.png)

     Les deux séries sont affichées pour chaque ligne de données. La série 1 envoie une requête pour la page *Red.aspx*, et la série 2 envoie une requête pour la page *Blue.aspx*.

     ![Résultats de la série de tests](../test/media/web_test_databinding_sql_runresults.png)

     Lorsque vous créez une liaison à une source de données, vous pouvez enfreindre la règle par défaut de l'URL de réponse. Dans ce cas, l’erreur dans la série 2 est provoquée par la règle qui attend la page *Red.aspx* de l’enregistrement de test d’origine, mais la liaison de données le dirige maintenant vers la page *Blue.aspx*.

2. Corrigez l’erreur de validation en supprimant la règle de validation de **l’URL de réponse** et en réexécutant le test.

     ![Supprimer la règle de validation de l'URL de la réponse](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Le test de performances de site Web réussit maintenant avec la liaison de données.

     ![Réussite du test à l'aide de la liaison de données](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Questions et réponses

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Q : Quelles bases de données puis-je utiliser comme source de données ?

**R :** Vous pouvez utiliser :

- Microsoft SQL Azure.

- Toute version de Microsoft SQL Server 2005 ou ultérieure.

- Fichier de base de données Microsoft SQL Server (y compris SQL Express).

- Microsoft ODBC.

- Fichier Microsoft Access à l'aide du fournisseur .NET Framework pour OLE DB.

- Oracle 7.3, 8i, 9i ou 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Q : Comment utiliser un fichier texte de valeurs séparées par des virgules (CSV) comme source de données ?

**R :** Voici comment procéder :

1. Créez un dossier pour organiser vos artefacts de base de données de projets et ajouter un élément.

     ![Ajouter un nouvel élément au dossier de données](../test/media/web_test_databinding_foldernewitem.png)

2. Créer un fichier texte.

     ![Nommer le nouveau fichier texte ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Modifiez le fichier texte et ajoutez ce qui suit :

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Utilisez les étapes décrites dans [Ajouter la source de données](#add-the-data-source), mais choisissez le fichier CSV comme source de données.

     ![Entrer un nom et choisir Fichier CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Q : Que se passe-t-il si le fichier CSV existant ne contient pas d'en-têtes de colonne ?

**R :** Si vous ne pouvez pas ajouter des en-têtes de colonnes, vous pouvez utiliser un fichier de description de schéma pour traiter le fichier CSV comme une base de données.

1. Ajoutez un nouveau fichier texte nommé *schema.ini*.

     ![Ajouter un fichier schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Modifiez le fichier *schema.ini* pour ajouter les informations qui décrivent la structure de vos données. Par exemple, un fichier de schéma qui décrit le fichier CSV peut se présenter de la manière suivante :

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Ajoutez une source de données au test.

     ![Ajouter la source de données au test des performances de site web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Si vous utilisez un fichier *schema.ini*, choisissez **Base de données** (pas Fichier CSV) comme source de données et nommez-la.

     ![Ajouter une source de données pour la base de données](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Créez une nouvelle connexion.

     ![Choisir un nouvelle connexion](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Sélectionnez le fournisseur de données .NET Framework pour OLE DB.

     ![Sélectionner le fournisseur de données .NET Framework pour OLE DB](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Choisissez **avancé**.

     ![Choisir Avancé](../test/media/web_test_databinding_advanced.png)

8. Pour la propriété Provider, sélectionnez Microsoft.Jet.OLEDB.4.0, puis définissez les **propriétés étendues** sur Text;HDR=NO.

     ![Appliquer les propriétés avancées](../test/media/web_test_databinding_advancedproperties.png)

9. Tapez le nom du répertoire qui contient le fichier de schéma et testez votre connexion.

     ![Entrer le chemin d'accès au dossier de données](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Sélectionnez le fichier CSV que vous voulez utiliser.

     ![Sélectionner le fichier texte](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Lorsque vous avez terminé, le fichier CSV apparaît sous forme de table.

     ![Source de données ajoutée au test](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Q : Comment utiliser un fichier XML comme source de données ?

**R :** Oui.

1. Créez un dossier pour organiser vos artefacts de base de données de projets et ajouter un élément.

     ![Ajouter un nouvel élément au dossier de données](../test/media/web_test_databinding_foldernewitem.png)

2. Créez un fichier XML.

     ![Ajouter le fichier ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Modifiez le fichier XML et ajoutez vos données :

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Utilisez les étapes décrites dans [Ajouter la source de données](#add-the-data-source), mais choisissez le fichier XML comme source de données.

     ![Entrer un nom et choisir Fichier XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Q : Puis-je ajouter la liaison de données à une requête de service Web qui utilise SOAP ?

**R :** Oui, vous devez modifier le code XML SOAP manuellement.

1. Choisissez la requête de service Web dans l'arborescence des requêtes et dans la fenêtre Propriétés, choisissez le bouton de sélection (...) dans la propriété Corps chaîne.

     ![Modifier le corps chaîne du service web](../test/media/web_test_databinding_webservicerequest.png)

2. Remplacez les valeurs du corps SOAP par les valeurs liées aux données en utilisant la syntaxe suivante :

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Par exemple, si vous avez le code suivant :

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Vous pouvez effectuer la modification comme suit :

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Enregistrez le test.
