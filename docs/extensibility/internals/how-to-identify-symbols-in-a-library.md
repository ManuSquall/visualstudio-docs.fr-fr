---
title: 'Comment : Identifier les symboles dans une bibliothèque Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708005"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Comment : Identifier les symboles dans une bibliothèque
Les outils de navigation des symboles affichent des vues hiérarchiques des symboles. Les symboles représentent des espaces de noms, des objets, des classes, des membres de la classe et d’autres éléments linguistiques.

 Chaque symbole de la hiérarchie peut être identifié par les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informations de navigation transmises par la bibliothèque de symboles au gestionnaire d’objets à travers les interfaces suivantes :

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 L’emplacement du symbole dans la hiérarchie distingue un symbole. Il permet aux outils de navigation de symbole de naviguer vers un symbole spécifique. Le chemin unique et entièrement qualifié vers le symbole détermine l’emplacement. Chaque élément du chemin est un nœud. Le chemin commence avec le nœud de haut niveau et se termine par le symbole spécifique. Par exemple, si la méthode M1 est membre de la classe C1 et que la C1 est dans l’espace de nom N1, le chemin complet de la méthode M1 est N1. C1. M1. Ce chemin contient trois nœuds : N1, C1 et M1.

 Les informations de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] navigation permettent au gestionnaire d’objets de localiser, de sélectionner et de conserver les symboles sélectionnés dans la hiérarchie. Il permet de naviguer d’un outil de navigation à l’autre. Tout en utilisant Le navigateur [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] **d’objets** pour parcourir les symboles d’un projet, vous pouvez cliquer à droite sur une méthode et démarrer **l’outil De navigateur d’appels** pour afficher la méthode dans un graphique d’appel.

 Deux formes décrivent l’emplacement du symbole. La forme canonique est basée sur le chemin entièrement qualifié du symbole. Il représente une position unique du symbole dans la hiérarchie. Il est indépendant de l’outil de navigation des symboles. Pour obtenir les informations de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formulaire <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> canonique, le gestionnaire d’objets appelle la méthode. Le formulaire de présentation décrit l’emplacement du symbole dans un outil spécifique de navigation des symboles. La position du symbole est relative à la position d’autres symboles dans la hiérarchie. Un symbole donné peut avoir plusieurs voies de présentation, mais un seul chemin canonique. Par exemple, si la classe C1 est héritée de la classe C2 et que les deux classes sont dans l’espace nom N1, le **navigateur d’objet** affiche l’arbre hiérarchique suivant :

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Le parcours canonique de la classe C2, dans cet exemple, est N1 C2. Le parcours de présentation de C2 comprend les nœuds C1 et " Bases and Interfaces " : N1 ' C1 ' ' Bases et Interfaces' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

 Pour obtenir les informations du formulaire <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> de présentation, le gestionnaire d’objets appelle la méthode.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Pour obtenir des formulaires canoniques et de présentation

1. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     Le gestionnaire d’objets appelle cette méthode pour obtenir la liste des nœuds contenus dans la trajectoire canonique du symbole.

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

     Le gestionnaire d’objets appelle cette méthode pour obtenir la liste des nœuds contenus dans le chemin de présentation du symbole.

## <a name="see-also"></a>Voir aussi
- [Soutenir les outils de navigation des symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Comment : Enregistrer une bibliothèque auprès du gestionnaire de l’objet](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Comment : Exposer les listes de symboles fournis par la bibliothèque au gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
