---
title: "Comment : identifier les symboles dans une bibliothèque | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 60365f3722ae4e2c1f8b52dacc3df03840fb3304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>Comment : identifier les symboles dans une bibliothèque
Outils de consultation du symbole affichent hiérarchique des symboles. Les symboles représentent des espaces de noms, des objets, des classes, des membres de classe et d’autres éléments de langage.  
  
 Chaque symbole dans la hiérarchie peut être identifié par les informations de navigation passées par la bibliothèque de symboles pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets via les interfaces suivantes :  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 L’emplacement du symbole dans la hiérarchie permet de différencier un symbole. Il permet aux outils de consultation du symbole accéder à un symbole spécifique. Le chemin d’accès unique et complet au symbole détermine l’emplacement. Chaque élément dans le chemin d’accès est un nœud. Le chemin d’accès commence par le nœud de niveau supérieur et se termine par le symbole spécifique. Par exemple, si la méthode M1 est un membre de la classe C1 et C1 est dans l’espace de noms N1, le chemin d’accès complet de la méthode M1 est N1. C1. M1. Ce chemin d’accès contient trois nœuds : N1, C1 et M1.  
  
 Les informations de navigation permettent la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets à rechercher, sélectionnez et conserver sélectionné les symboles dans la hiérarchie. Il permet d’accéder à partir d’un outil de navigation vers un autre. Lors de l’utilisation **Explorateur d’objets** pour rechercher des symboles dans un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projet, vous pouvez cliquez avec le bouton droit sur une méthode et commencer le **Explorateur d’appels** outil pour afficher la méthode dans un graphique des appels.  
  
 Deux formes décrivent l’emplacement de symboles. La forme canonique est basée sur le chemin d’accès qualifié complet du symbole. Il représente un emplacement unique du symbole dans la hiérarchie. Elle est indépendante de l’outil de consultation du symbole. Pour obtenir les informations de forme canonique, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de l’objet gestionnaire appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> (méthode). Le formulaire de présentation décrit l’emplacement du symbole dans un outil de consultation du symbole spécifique. La position du symbole est relativement à la position d’autres symboles dans le hierarchicy. Un symbole donné peut avoir plusieurs chemins d’accès présentation, mais qu’un seul chemin d’accès canonique. Par exemple, si C1 classe héritée de la classe de C2 et les deux classes figurent dans l’espace de noms N1, la **Explorateur d’objets** affiche l’arborescence hiérarchique suivante :  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Le chemin d’accès canonique de la classe C2, dans cet exemple, est N1 + C2. Le chemin d’accès de la présentation de C2 inclut des nœuds de C1 et « Bases et Interfaces » : N1 + C1 + « Bases et Interfaces » + C2.  
  
 Pour obtenir les informations du formulaire de présentation, l’objet gestionnaire appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> (méthode).  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identification d’un symbole dans la hiérarchie  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Pour obtenir des canonique et informations de formulaires de présentation  
  
1.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Le Gestionnaire d’objets appelle cette méthode pour obtenir la liste de nœuds contenus dans le chemin d’accès canonique du symbole.  
  
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
  
2.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Le Gestionnaire d’objets appelle cette méthode pour obtenir la liste de nœuds contenus dans le chemin d’accès de la présentation du symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Comment : inscrire une bibliothèque avec le Gestionnaire d’objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Guide pratique pour exposer des listes de symboles fournies par la bibliothèque au Gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)