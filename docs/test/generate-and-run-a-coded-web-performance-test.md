---
title: Tests de performances web codés
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4297f60c74e32b904d7c36912a8377d33f23ebdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589576"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Générer et exécuter un test de performances de site Web codé

Les tests de performances web sont enregistrés lors de la navigation au sein de votre application web. Les tests sont inclus dans les tests de charge afin de mesurer les performances de votre application web soumise à l’activité de plusieurs utilisateurs. Un test de performances de site web peut être converti en un script basé sur le code que vous pouvez modifier et personnaliser comme tout autre code source. Par exemple, vous pouvez ajouter des boucles et des branchements.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Générer un test de performances Web codé

1. Si vous n’avez pas créé un test de performances web, consultez [Enregistrer un test de performances web](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Générez le test codé.

     ![Générer un test de performances Web codé](../test/media/web_test_coded_generate.png)

3. Nommez le test.

     ![Entrer un nom pour le test de performances web codé](../test/media/web_test_coded_generate_nametest.png)

     Le nouveau test codé s'ouvre dans l'éditeur de code.

     En fonction du modèle de projet de test de performances web et de charge que vous avez ajouté à votre solution, le code sera généré en Visual Basic ou en Visual C#.

     ![Le nouveau test codé s'ouvre dans l'éditeur de code](../test/media/web_test_coded_generate_opencodeeditor.png)

     Vous pouvez voir dans le code que la méthode GetRequestEnumerator() en C# ou la méthode Run() en Visual Basic contient chaque règle de validation et chaque requête web qui se trouvaient dans le test recodé.

4. Pour montrer comment ajouter du code simple, faites défiler le code jusqu'à la fin de la méthode et après le code de la dernière requête web, ajoutez le code suivant :

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. Générez la solution pour vérifier que votre code personnalisé se compile.

6. Exécutez le test.

     ![Exécuter le test de performances de site web codé](../test/media/web_test_coded_generate_run.png)

     Et puisque le jour d'exécution était un mercredi…

     ![Résultats du test de performances web codé](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Questions et réponses

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Q : Puis-je exécuter plusieurs tests simultanément ?
**R :** Oui, utilisez le menu contextuel en cliquant avec le bouton droit dans **Explorateur de solutions**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Q : Dois-je ajouter une source de données avant ou après la génération d'un test codé ?
**R :** Il est plus facile d’ajouter une [source de données](../test/add-a-data-source-to-a-web-performance-test.md) avant de générer le test codé, car le code sera généré automatiquement pour vous.

Lorsque vous exécutez un test codé avec une source de données, le message d'erreur suivant peut s'afficher :

**Impossible d’exécuter \<Test Name> le test sur l’agent \<Computer Name> : la référence d’objet n’est pas définie sur une instance d’un objet.**

Cette erreur peut se produire parce qu'un DataSourceAttribute a été défini pour la classe de test, sans DataBindingAttribute correspondant. Pour résoudre cette erreur, ajoutez un DataBindingAttribute approprié, supprimez-le ou commentez-le hors du code.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Q : Dois-je ajouter des règles de validation et d’extraction avant ou après la génération d’un test codé ?
**R :** Il est plus facile d’ajouter des règles de validation et d’extraction avant de générer le test codé. Cependant, nous vous recommandons d’utiliser des [tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md) à des fins de validation.
