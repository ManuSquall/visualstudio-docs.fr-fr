---
title: API de test de performances web
description: En savoir plus sur l’API de test de performances de site Web, qui prend en charge les tests de performances Web codés, les plug-ins de test, les plug-ins de requête, les demandes et les règles d’extraction/validation.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4802d95c46d1187911f4bbc134cc0c50ce08b18
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329716"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Guide pratique pour utiliser l’API de test de performances web

Vous pouvez écrire du code pour vos tests de performances web. L’API de test de performances web permet de créer des tests de performances web codés, des plug-ins de test de performances web, des plug-ins de demande, des demandes, des règles d’extraction et des règles de validation. Les classes qui composent ces types sont les classes principales dans cette API. Les autres types dans cette API sont utilisés pour prendre en charge la création d'objets <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Pour créer des tests de performances web personnalisés, utilisez l’espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez également utiliser l’API de test de performances web pour créer par programmation et enregistrer des tests de performances web déclaratifs. Pour ce faire, utilisez les classes <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> Utilisez l'Explorateur d'objets pour examiner l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>. Les éditeurs Visual C# et Visual Basic offrent tous deux la prise en charge IntelliSense du codage avec les classes de l'espace de noms.

Vous pouvez également créer des plug-ins pour les tests de charge. Pour plus d’informations, consultez [Guide pratique pour utiliser l’API de test de charge](../test/how-to-use-the-load-test-api.md) et [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Pour utiliser l'espace de noms WebTesting

1. Ouvrez un projet de test de performances web et de charge contenant un test de performances web.

2. Ajoutez un projet de bibliothèque de classes Visual Basic ou Visual C# à votre solution de test.

3. Ajoutez une référence dans le projet de test de performances web et de charge au projet de bibliothèque de classes.

4. Ajoutez une référence à la DLL Microsoft.VisualStudio.QualityTools.WebTestFramework dans le projet de bibliothèque de classes.

5. Dans le fichier de classe situé dans le projet de bibliothèque de classes, ajoutez une `using` instruction pour l'espace de noms <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6. Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7. Créez le projet.

8. Ajoutez le nouveau plug-in de test de performances web avec l’éditeur de test de performances web :

    1. Choisissez **Ajouter un plug-in de test web** dans la barre d’outils.

         La boîte de dialogue **Ajouter un plug-in de test web** s’affiche.

    2. Sous **Sélectionner un plug-** in, sélectionnez votre classe de plug-in de test de performances de site Web.

    3. Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

        > [!NOTE]
        > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pourrez également modifier par la suite les propriétés du plug-in de test de performances web, dans la fenêtre Propriétés.

    4. Choisissez **OK**.

9. Exécutez votre test de performances web.

     Pour obtenir un exemple d’implémentation de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, consultez [Guide pratique pour créer un plug-in de test de performances web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Créer un code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Comment : utiliser l’API de test de charge](../test/how-to-use-the-load-test-api.md)
- [Comment : créer un plug-in de test de performances de site Web](../test/how-to-create-a-web-performance-test-plug-in.md)
