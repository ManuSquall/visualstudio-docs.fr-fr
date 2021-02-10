---
title: 'Comment : identifier des symboles dans une bibliothèque | Microsoft Docs'
description: Découvrez comment identifier les symboles d’une bibliothèque en implémentant des méthodes qui transmettent des informations de navigation de la bibliothèque de symboles au gestionnaire d’objets Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b4e4c551c516b78ababb2400f7cfbd699ab06627
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932590"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Comment : identifier des symboles dans une bibliothèque
Les outils de navigation de symboles affichent des vues hiérarchiques de symboles. Les symboles représentent des espaces de noms, des objets, des classes, des membres de classe et d’autres éléments de langage.

 Chaque symbole de la hiérarchie peut être identifié par les informations de navigation passées par la bibliothèque de symboles au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets via les interfaces suivantes :

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 L’emplacement du symbole dans la hiérarchie distingue un symbole. Il permet aux outils de navigation de symboles de naviguer vers un symbole spécifique. Le chemin d’accès complet unique au symbole détermine l’emplacement. Chaque élément du chemin d’accès est un nœud. Le chemin d’accès commence par le nœud de niveau supérieur et se termine par le symbole spécifique. Par exemple, si la méthode M1 est un membre de la classe C1 et que C1 est dans l’espace de noms N1, le chemin d’accès complet de la méthode M1 est N1. C1. M1. Ce chemin contient trois nœuds : N1, C1 et M1.

 Les informations de navigation permettent au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets de rechercher, de sélectionner et de conserver les symboles dans la hiérarchie. Il permet de naviguer d’un outil de navigation à un autre. Quand vous utilisez l' **Explorateur d’objets** pour parcourir les symboles d’un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projet, vous pouvez cliquer avec le bouton droit sur une méthode et démarrer l’outil **Explorateur d’appels** pour afficher la méthode dans un graphique des appels.

 Deux formulaires décrivent l’emplacement des symboles. La forme canonique est basée sur le chemin d’accès complet du symbole. Il représente une position unique du symbole dans la hiérarchie. Il est indépendant de l’outil de navigation de symboles. Pour obtenir les informations de formulaire canoniques, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> méthode. Le formulaire de présentation décrit l’emplacement du symbole dans un outil de navigation de symboles spécifique. La position du symbole est relative à la position des autres symboles dans la hiérarchie. Un symbole donné peut avoir plusieurs chemins de présentation, mais un seul chemin d’accès canonique. Par exemple, si la classe C1 est héritée de la classe C2 et que les deux classes se trouvent dans l’espace de noms N1, l' **Explorateur d’objets** affiche l’arborescence hiérarchique suivante :

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Le chemin d’accès canonique de la classe C2, dans cet exemple, est N1 + C2. Le chemin de présentation de C2 comprend les nœuds C1 et « bases et interfaces » : N1 + C1 + « bases et interfaces » + C2.

 Pour obtenir les informations de formulaire de présentation, le gestionnaire d’objets appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> méthode.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Pour obtenir les informations de formulaires canoniques et de présentation

1. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     Le gestionnaire d’objets appelle cette méthode pour obtenir la liste des nœuds contenus dans le chemin d’accès canonique du symbole.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.

     Le gestionnaire d’objets appelle cette méthode pour obtenir la liste des nœuds contenus dans le chemin d’accès de présentation du symbole.

## <a name="see-also"></a>Voir aussi
- [Prise en charge des outils de navigation de symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procédure : inscrire une bibliothèque à l’aide du gestionnaire d’objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Comment : exposer des listes de symboles fournies par la bibliothèque au gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
