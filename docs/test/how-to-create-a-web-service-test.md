---
title: Créer un test de service web dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: b7d7a864b7fc62527bdd2593523ccdc91bf913aa
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-create-a-web-service-test"></a>Comment : créer un test de service Web

Vous pouvez utiliser un test de performances de site web pour tester des services web. À l’aide des options **Insérer une requête** et **Insérer une requête de service web**, vous pouvez personnaliser les requêtes individuelles dans **l’éditeur de test de performances web** pour localiser des pages de service web. En général, vous n'affichez pas ces pages dans l'application web. Par conséquent, vous devez personnaliser la requête pour accéder à ces pages.

Les procédures suivantes utilisent un service web contenu dans le Starter Kit Commerce. Vous pouvez le télécharger à partir du lien [Starter Kit ASP.NET Commerce](http://go.microsoft.com/fwlink/?LinkId=181469).

 **Spécifications**

-   Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Pour tester un service web

1.  Créer un test de performances de site web. Dès que le navigateur s’ouvre, choisissez **Arrêter**.

2.  Dans **l’éditeur de test de performances web**, cliquez avec le bouton droit sur le test de performances web et sélectionnez **Ajouter une requête de service web**.

3.  Dans la propriété **Url** de la nouvelle requête, tapez le nom du service web (par exemple, **http://localhost/storecsvs/InstantOrder.asmx**).

4.  Ouvrez une session distincte du navigateur et tapez l’URL de la page .asmx dans la barre d’outils **Adresse**. Sélectionnez la méthode à tester et examinez le message SOAP. Il contient un `SOAPAction`.

5.  Dans **l’éditeur de test de performances web**, cliquez avec le bouton droit sur la requête et sélectionnez **Ajouter un en-tête** pour ajouter un nouvel en-tête. Dans la propriété **Nom**, tapez `SOAPAction`. Dans la propriété **Valeur**, tapez la valeur qui apparaît dans `SOAPAction` (par exemple, `"http://tempuri.org/CheckStatus"`).

6.  Développez le nœud d’URL dans l’éditeur, puis sélectionnez le nœud **Corps chaîne**. Dans la propriété **Type de contenu**, entrez la valeur `text/xml`.

7.  Retournez au navigateur à l'étape 4, sélectionnez la partie XML de la requête SOAP à partir de la page de description du service web et copiez-la dans le Presse-papiers.

8.  Le contenu XML ressemble à l'exemple suivant :

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Retournez à **l’éditeur de test de performances web**, puis cliquez sur le bouton de sélection (…) dans la propriété **Corps chaîne**. Collez le contenu du Presse-papiers dans la propriété.

10. Vous devez remplacer toutes les valeurs d'espace réservé par des valeurs valides pour que le test réussisse. Dans l'exemple précédent, vous devez remplacer les deux instances de `string` et un `int`. Cette opération de service web ne se termine que si un utilisateur inscrit passe une commande.

11. Cliquez avec le bouton droit sur la requête de service web et sélectionnez **Ajouter un paramètre QueryString d’URL**.

12. Assignez un nom et une valeur au paramètre de chaîne de requête. Dans l’exemple précédent, le nom est `op` et la valeur `CheckStatus`. Cela identifie l'opération de service web à exécuter.

    > [!NOTE]
    > Vous pouvez utiliser la liaison de données dans le corps SOAP pour remplacer n'importe quelle valeur d'espace réservé par des valeurs liées aux données à l'aide de la syntaxe `{{DataSourceName.TableName.ColumnName}}`.

13. Exécutez le test. Dans le volet supérieur de l'Afficheur des résultats des tests de performances de site web, sélectionnez la requête de service web. Dans le volet inférieur, sélectionnez l'onglet Navigateur Web. Le XML qui est retourné par le service web et les résultats de toutes les opérations sont affichés.

## <a name="see-also"></a>Voir aussi

- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)