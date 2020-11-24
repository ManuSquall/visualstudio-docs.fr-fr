---
title: Créer un test de service web
description: Découvrez comment utiliser un test de performances pour les services Web et personnaliser les demandes dans le éditeur de test de performances Web pour localiser des pages de service Web.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 32b5a6a91221e8942faeefcb89cfc52dd0cc5895
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439925"
---
# <a name="how-to-create-a-web-service-test"></a>Guide pratique pour créer un test de service web

Vous pouvez utiliser un test de performances web pour tester des services web. À l’aide des options **Insérer** une requête et **Insérer un service Web** , vous pouvez personnaliser les demandes individuelles dans le **éditeur de test de performances Web** pour localiser les pages du service Web. En général, vous n'affichez pas ces pages dans l'application web. Par conséquent, vous devez personnaliser la requête pour accéder à ces pages.

>[!NOTE]
> Les fonctionnalités de performances Web et de test de charge sont dépréciées dans Visual Studio 2019. Par Application Insights, les tests Web à plusieurs étapes dépendent des fichiers Visual Studio WebTest. Il a été [annoncé](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) que Visual Studio 2019 est la dernière version avec la fonctionnalité de test web. Il est important de comprendre que même si aucune nouvelle fonctionnalité ne sera ajoutée, les fonctionnalités de test web dans Visual Studio 2019 sont toujours prises en charge et continueront d’être prises en charge pendant le cycle de vie du support du produit. L’équipe de produit Azure Monitor a répondu aux questions concernant l’avenir des tests de disponibilité à plusieurs étapes [ici](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101).

**Configuration requise**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Pour créer un service Web simple

Pour tester, vous pouvez utiliser votre propre service Web ou utiliser le modèle de service Web de base (ASMX) inclus dans Visual Studio. Pour créer un service Web simple à l’aide de ce modèle :

1. Dans Visual Studio, créez un projet à l’aide du modèle d’application Web ASP.NET (.NET Framework), puis sélectionnez le modèle **vide** quand vous y êtes invité. Tapez un nom et créez le projet.

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet, choisissez **Ajouter**  >  **un nouvel élément**, puis choisissez **service Web (asmx)**. Ajoutez le service Web.

1. Ouvrez *WebService1. asmx* et remplacez la méthode Web par défaut par `HelloWorld` le code suivant.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Installer le composant de test de charge

Si le composant des outils de test de performances web et de charge n’est pas installé, utilisez pour cela Visual Studio Installer.

1. Ouvrez **Visual Studio installer** à partir du menu **Démarrer** de Windows. Vous pouvez également y accéder dans Visual Studio à partir de la boîte de dialogue Nouveau projet ou en choisissant **Outils**  >  **afficher les outils et les fonctionnalités** dans la barre de menus.

1. Dans **Visual Studio Installer**, choisissez l’onglet **Composants individuels** et faites défiler jusqu’à la section **Débogage et test**. Sélectionnez **Outils de test de performances web et de test de charge**.

   ![Composant Outils de test de performances web et de test de charge](media/web-perf-load-testing-tools-component.png)

1. Choisissez le bouton **Modifier**.

   Le composant des outils de test de performances web et de charge est installé.

## <a name="create-a-web-test-project"></a>Créer un projet de test Web

Un test Web requiert le modèle de projet projet de test de performances Web et de charge. Dans cette section, nous créons un projet de test de charge C#. Vous pouvez également créer un projet de test de charge Visual Basic si vous préférez.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

   Si vous utilisez l’exemple de modèle de service Web (ASMX), vous pouvez ajouter le projet de test Web à la même solution.

2. Choisissez **Fichier** > **Nouveau** > **Projet** dans la barre de menus.

   La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans la boîte de dialogue **Nouveau Projet**, développez **Installé** et **Visual C#**, puis sélectionnez la catégorie **Test**. Choisissez le modèle **Projet de performances web et de test de charge**.

   ![Projet de performances web et de test de charge](media/web-perf-load-test-project-template.png)

4. Entrez un nom pour le projet si vous ne voulez pas utiliser le nom par défaut, puis choisissez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

   Si vous utilisez l’exemple de modèle de service Web (ASMX), vous pouvez ajouter le projet de test Web à la même solution.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Dans la page **Créer un projet**, tapez **test web** dans la zone de recherche, puis sélectionnez le modèle **Projet de test de performance web et de charge \[déprécié]** pour C#. Choisissez **Suivant**.

4. Entrez un nom pour le projet si vous ne voulez pas utiliser le nom par défaut, puis choisissez **Créer**.

::: moniker-end

   Visual Studio crée le projet et affiche les fichiers dans **Explorateur de solutions**. Le projet contient initialement un fichier de test Web nommé *WebTest1. WebTest*.

## <a name="to-test-a-web-service"></a>Pour tester un service web

1. Démarrez votre service Web et, si nécessaire, choisissez **arrêter** pour suspendre le service.

1. Dans le projet de test Web, ouvrez *WebTest1. WebTest*, qui ouvre le éditeur de test de performances Web. Dans l’éditeur de test, cliquez avec le bouton droit sur le test de performances de site Web et sélectionnez **Ajouter une demande de service Web**.

1. Dans la propriété **Url** de la nouvelle requête, tapez le nom du service web, par exemple **https://localhost:44318/WebService1.asmx**.

1. Pour le service Web, ouvrez une session distincte du navigateur et tapez l’URL de la page *. asmx* dans la barre d’outils **adresse** . En haut de la page Web, sélectionnez la méthode que vous souhaitez tester et examinez le message SOAP. (Dans l’exemple de service Web, la méthode est HelloWorld.) Lorsque vous ouvrez la méthode, vous voyez qu’elle contient un `SOAPAction` .

1. Dans **l’éditeur de test de performances web**, cliquez avec le bouton droit sur la requête et sélectionnez **Ajouter un en-tête** pour ajouter un nouvel en-tête. Dans la propriété **Nom**, tapez `SOAPAction`. Dans la propriété **valeur** , tapez la valeur que vous voyez dans `SOAPAction` , par exemple *http://tempuri.org/HelloWorld* .

1. Développez le nœud URL dans l’éditeur de test, choisissez le nœud **corps de chaîne** et dans la propriété **type de contenu** , entrez la valeur `text/xml` .

1. Retournez au navigateur à l'étape 4, sélectionnez la partie XML de la requête SOAP à partir de la page de description du service web et copiez-la dans le Presse-papiers.

   Le contenu XML ressemble à l'exemple suivant :

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Revenez au éditeur de test de performances Web, puis choisissez les points de suspension **(...)** dans la propriété **corps de chaîne** . Collez le contenu du Presse-papiers dans la propriété.

1. Remplacez toutes les valeurs d’espace réservé dans le code XML par des valeurs valides afin que le test puisse réussir. Dans l’exemple précédent, vous remplaceriez l’instance de `string` par un nom.

1. Cliquez avec le bouton droit sur la demande de service Web et sélectionnez **Ajouter un paramètre QueryString d’URL**.

1. Assignez un nom et une valeur au paramètre de chaîne de requête. Dans l’exemple précédent, le nom est `op` et la valeur `HelloWorld`. Cela identifie l'opération de service web à exécuter.

    > [!NOTE]
    > Vous pouvez utiliser la liaison de données dans le corps SOAP pour remplacer toute valeur d’espace réservé par des valeurs liées aux données à l’aide de la `{{DataSourceName.TableName.ColumnName}}` syntaxe.

1. Exécutez le test. Dans le volet supérieur de l'**Afficheur des résultats des tests de performances web**, sélectionnez la requête de service web. Dans le volet inférieur, sélectionnez l’onglet **navigateur Web** . Le code XML retourné par le service Web, ainsi que les résultats de toutes les opérations, s’affichent.

   Recherchez les résultats de votre demande de service Web.

## <a name="see-also"></a>Voir aussi

- [Créer un code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
