---
title: "Générer des commentaires de documentation XML pour Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Générer des commentaires de documentation XML dans Visual Basic

**Quoi :** vous permet de générer immédiatement la base XML nécessaire pour documenter l’élément sélectionné. 

**Quand :** vous souhaitez créer des commentaires de documentation XML pour un traitement ultérieur par un outil de documentation comme Sandcastle.

**Pourquoi :** vous pouvez créer vous-même manuellement la totalité du bloc de commentaires, mais cela permet de gagner du temps et d’améliorer la précision en générant le modèle de base et les éléments supplémentaires. 

**Comment :**

1. Placez votre curseur sur l’élément que vous souhaitez documenter, par exemple, une méthode.

   ![Méthode à documenter](media/doc-highlight-vb.png)

1. Ensuite, tapez **'''** (3 guillemets simples) pour créer automatiquement le modèle de base et tous les éléments supplémentaires, le cas échéant.  Par exemple, lorsque vous commentez une méthode, vous générez les balises **\<summary\>** ainsi qu’une balise **\<param\>** pour chaque paramètre transmis à la méthode, puis une balise **\<returns\>** pour documenter ce que la méthode retourne.

   ![Modèle](media/doc-preview-vb.png)

1. Saisissez les commentaires et ajoutez d’autres informations que vous estimez nécessaires.

   ![Commentaire terminé](media/doc-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Documentation de votre code avec le langage XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Génération de code](../code-generation-in-visual-studio.md)