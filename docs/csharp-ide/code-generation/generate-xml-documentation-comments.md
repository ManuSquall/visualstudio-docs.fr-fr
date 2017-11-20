---
title: "Générer des commentaires de documentation XML - génération de Code (c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bf34acffb037369458aa4a86a5ecf629f127004
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-c"></a>Générer des commentaires de documentation XML en c# #
**Ce que :** vous permet de générer immédiatement de la base de XML nécessaires à la documentation de l’élément sélectionné. 

**Quand :** vous souhaitez créer des commentaires de Document XML pour un traitement ultérieur par un outil de documentation tels que Sandcastle.

**Pourquoi :** vous pouvez créer manuellement le bloc de commentaires ensemble vous-même, mais cela gagner du temps et améliorer la précision en générant le modèle de base et les éléments supplémentaires. 

**Comment faire :**

1. Placez votre curseur au-dessus de l’élément que vous souhaitez documenter, par exemple, une méthode.

   ![Méthode au document](media/doc_highlight.png)

1. Ensuite, tapez  **///**  (3 barres obliques) qui crée automatiquement le modèle de base et tous les éléments supplémentaires si nécessaire.  Par exemple, lorsque vous mettez en commentaires une méthode, il génère le  **\<Résumé\>**  balises, ainsi qu’une  **\<param\>**  balise pour chaque paramètre est passé à la méthode et un  **\<retourne\>**  balise documenter ce que la méthode retourne.

   ![Modèle](media/doc_preview.png)

1. Tapez des commentaires et ajouter d’autres informations que vous estimez sont nécessaires.

   ![Commentaire terminé](media/doc_result.png)

## <a name="see-also"></a>Voir aussi
[Génération de code (C#)](../code-generation-csharp.md)  
[Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
