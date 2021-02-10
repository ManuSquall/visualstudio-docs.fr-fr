---
title: Insérer des commentaires dans la documentation XML
description: Apprenez à insérer des commentaires de documentation XML dans votre code, que vous pouvez utiliser pour créer un fichier XML généré par le compilateur à distribuer avec votre assembly .NET.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2c203d9a445d9426a8079801a856e20f7be82229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946564"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Guide pratique pour insérer des commentaires XML pour la génération de documentation

Visual Studio peut vous aider à documenter des éléments de code, comme les classes et les méthodes, en générant automatiquement la structure de commentaire de documentation XML standard. Au moment de la compilation, vous pouvez générer un fichier XML qui contient les commentaires de documentation.

> [!TIP]
> Pour plus d’informations sur la configuration du nom et de l’emplacement du fichier XML généré, consultez [Documentation de votre code avec des commentaires XML (Guide C#)](/dotnet/csharp/codedoc).

Le fichier XML généré par le compilateur peut être distribué avec votre assembly .NET pour permettre à Visual Studio et à d’autres IDE d’utiliser IntelliSense pour afficher des informations rapides concernant les types et les membres. De plus, le fichier XML peut être exécuté par l’intermédiaire d’outils tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) pour générer des sites web de références d’API.

> [!NOTE]
> La commande **Insérer un commentaire** qui insère automatiquement des commentaires de documentation XML est disponible en [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) et en [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Toutefois, vous pouvez insérer manuellement des [commentaires de documentation XML dans des fichiers C++](/cpp/build/reference/xml-documentation-visual-cpp) et générer des fichiers de documentation XML au moment de la compilation.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Pour insérer des commentaires XML pour un élément de code

1. Placez votre curseur sur l’élément que vous souhaitez documenter, par exemple, une méthode.

2. Effectuez l’une des actions suivantes :

   - Tapez `///` en C# ou `'''` en Visual Basic.

   - Dans le menu **Edition**, choisissez **IntelliSense** > **Insérer un commentaire**.

   - Dans le menu contextuel ou juste au-dessus de l’élément de code, choisissez **extrait**  >  **Insérer un commentaire**

   Le modèle XML est généré immédiatement au-dessus de l’élément de code. Par exemple, lorsque vous commentez une méthode, elle génère l' **\<summary\>** élément, un **\<param\>** élément pour chaque paramètre et un **\<returns\>** élément pour documenter la valeur de retour.

   ![Modèle de commentaire XML (C#)](media/doc-preview-cs.png)

   ![Modèle de commentaire XML (Visual Basic)](media/doc-preview-vb.png)

3. Entrez la description de chaque élément XML pour documenter entièrement l’élément de code.

   ![Capture d’écran montrant le commentaire terminé.](media/doc-result-cs.png)

Vous pouvez utiliser des styles dans des commentaires XML qui s’affichent dans Info Express lorsque vous pointez sur l’élément. Ces styles sont notamment les suivants : italique, gras, puces et lien hypertexte.

   ![Capture d’écran montrant le commentaire terminé avec des balises de style pour l’italique, le gras, les puces et un lien hypertexte.](media/doc-style-cs.png) 

> [!NOTE]
> Une [option](../../ide/reference/options-text-editor-csharp-advanced.md) permet d’activer et de désactiver les commentaires de documentation XML après la saisie des caractères `///` en C# ou `'''` en Visual Basic. Dans la barre de menus, choisissez **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** . Ensuite, accédez à **éditeur de texte**  >  **C#** ou avancé de **base**  >  . Dans la section **Aide sur l’éditeur**, recherchez l’option **Générer des commentaires sur la documentation XML**.

## <a name="see-also"></a>Voir aussi

- [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentation de votre code avec des commentaires XML (Guide C#)](/dotnet/csharp/codedoc)
- [Guide pratique pour créer une documentation XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Commentaires C++](/cpp/cpp/comments-cpp)
- [Documentation XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Génération de code](../code-generation-in-visual-studio.md)
