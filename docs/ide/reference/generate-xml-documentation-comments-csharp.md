---
title: "Générer des commentaires de documentation XML - génération de code (C#) | Microsoft Docs"
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
ms.workload: dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>Générer des commentaires de documentation XML en C# #
**Quoi :** vous permet de générer immédiatement la base XML nécessaire pour documenter l’élément sélectionné. 

**Quand :** vous souhaitez créer des commentaires de documentation XML pour un traitement ultérieur par un outil de documentation comme Sandcastle.

**Pourquoi :** vous pouvez créer vous-même manuellement la totalité du bloc de commentaires, mais cela permet de gagner du temps et d’améliorer la précision en générant le modèle de base et les éléments supplémentaires. 

**Comment :**

1. Placez votre curseur sur l’élément que vous souhaitez documenter, par exemple, une méthode.

   ![Méthode à documenter](media/doc-highlight-cs.png)

1. Ensuite, tapez **///** (3 barres obliques) pour créer automatiquement le modèle de base et tous les éléments supplémentaires, le cas échéant.  Par exemple, lorsque vous commentez une méthode, vous générez les balises **\<summary\>** ainsi qu’une balise **\<param\>** pour chaque paramètre transmis à la méthode, puis une balise **\<returns\>** pour documenter ce que la méthode retourne.

   ![Modèle](media/doc-preview-cs.png)

1. Saisissez les commentaires et ajoutez d’autres informations que vous estimez nécessaires.

   ![Commentaire terminé](media/doc-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
