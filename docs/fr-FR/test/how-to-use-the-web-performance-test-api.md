---
title: API de test de performances web dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 330e0aa9bcf51b0ce9d57ea93a13303b7a356982
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-the-web-performance-test-api"></a>Comment : utiliser l'API du test des performances de site Web

Vous pouvez écrire du code pour vos tests de performances de site Web. L’API de test de performances de site Web permet de créer des tests de performances de site Web codés, des plug-ins de test de performances de site Web, des plug-ins de requête, des requêtes, des règles d’extraction et des règles de validation. Les classes qui composent ces types sont les classes principales dans cette API. Les autres types dans cette API sont utilisés pour prendre en charge la création d'objets <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Vous utilisez l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting> pour créer des tests de performances de site Web personnalisés.

 Vous pouvez également utiliser l'API de test de performances de site Web pour créer par programmation et enregistrer des tests de performances de site Web déclaratifs. Pour ce faire, utilisez les classes <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> Utilisez l'Explorateur d'objets pour examiner l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>. Les éditeurs Visual C# et Visual Basic offrent tous deux la prise en charge IntelliSense du codage avec les classes de l'espace de noms.


 Vous pouvez également créer des plug-ins pour les tests de charge. Pour plus d’informations, consultez [Guide pratique pour utiliser l’API de test de charge](../test/how-to-use-the-load-test-api.md) et [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Pour utiliser l'espace de noms WebTesting

1.  Ouvrez un projet de test de performances de site web et de charge qui contient un test de performances de site web.

2.  Ajoutez un projet de bibliothèque de classes Visual Basic ou Visual C# à votre solution de test.

3.  Ajoutez une référence dans le projet de test de performances de site web et de charge au projet de bibliothèque de classes.

4.  Ajoutez une référence à la DLL Microsoft.VisualStudio.QualityTools.WebTestFramework dans le projet de bibliothèque de classes.

5.  Dans le fichier de classe situé dans le projet de bibliothèque de classes, ajoutez une `using` instruction pour l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7.  Générez le projet.

8.  Ajoutez le nouveau plug-in de test de performances de site Web à l'aide de l'éditeur de tests de performances de site Web :

    1.  Choisissez **Ajouter un plug-in de test web** dans la barre d’outils.

         La boîte de dialogue **Ajouter un plug-in de test web** s’affiche.

    2.  Sous **Sélectionner un plug-in**, sélectionnez votre classe de plug-in de test de performances web.

    3.  Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

        > [!NOTE]
        > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pouvez également modifier ultérieurement les propriétés du plug-in de test de performances de site Web dans la fenêtre Propriétés.

    4.  Cliquez sur **OK**.

9. Exécutez votre test de performances de site web.

     Pour obtenir un exemple d’implémentation de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, consultez [Guide pratique pour créer un plug-in de test de performances web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Guide pratique pour utiliser l’API de test de charge](../test/how-to-use-the-load-test-api.md)
- [Guide pratique pour créer un plug-in de test des performances web](../test/how-to-create-a-web-performance-test-plug-in.md)