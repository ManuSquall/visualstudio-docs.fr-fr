---
title: API de test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ea28bba2d59515ce8080d577248dd7bddee0c570
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049903"
---
# <a name="how-to-use-the-load-test-api"></a>Procédure : utiliser l’API de test de charge

Visual Studio prend en charge des plug-ins de test de charge qui peuvent contrôler ou améliorer un test de charge. Les plug-ins de test de charge sont des classes définies par l'utilisateur qui implémentent l'interface <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> qui se trouve dans l'espace de noms <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. Les plug-ins de test de charge permettent de bénéficier d'un contrôle de test de charge personnalisé, tel que l'abandon d'un test de charge lorsqu'un seuil d'erreur ou de compteur est atteint. Utilisez les propriétés sur la classe <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> pour obtenir ou définir des paramètres de test de charge à partir de code défini par l'utilisateur. Utilisez les événements sur la classe <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> pour joindre des délégués pour les notifications lorsque le test de charge s'exécute.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Utilisez l'Explorateur d'objets pour examiner l'espace de noms <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. Les éditeurs Visual C# et Visual Basic offrent tous deux la prise en charge IntelliSense du codage avec les classes de l'espace de noms.

Vous pouvez également créer des plug-ins pour les tests de performances web. Pour plus d'informations, voir [Procédure : créer un plug-in de test de performances web](../test/how-to-create-a-web-performance-test-plug-in.md) et [Guide pratique pour créer un plug-in au niveau de la requête](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Pour utiliser l'espace de noms LoadTesting

1.  Ouvrez un projet de test de performances web et de charge contenant un test de charge.

2.  Ajoutez un projet de bibliothèque de classes Visual Basic ou Visual C# à votre solution de test.

3.  Ajoutez une référence dans le projet de test de performances web et de charge au projet de bibliothèque de classes.

4.  Ajoutez une référence à la DLL Microsoft.VisualStudio.TestTools.LoadTestFramework dans le projet de bibliothèque de classes.

5.  Dans le fichier de classe situé dans le projet de bibliothèque de classes, ajoutez une instruction `using` pour l'espace de noms <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

6.  Créez une classe publique qui implémente l'interface <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

7.  Générez le projet.

8.  Ajoutez le nouveau plug-in de test de charge à l'aide de l'éditeur de test de charge :

    1.  Cliquez avec le bouton droit sur le nœud racine du test de charge, puis choisissez **Ajouter un plug-in de test de charge**.

    2.  La boîte de dialogue **Ajouter un plug-in de test de charge** s’affiche.

    3.  Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

        > [!NOTE]
        > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins. Il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pourrez modifier ultérieurement les propriétés du plug-in du test de charge dans la fenêtre **Propriétés**.

9. Exécutez votre test de charge.

     Pour obtenir une implémentation de <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, consultez [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Guide pratique pour utiliser l’API de test de performances web](../test/how-to-use-the-web-performance-test-api.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)