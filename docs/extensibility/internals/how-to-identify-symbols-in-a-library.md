---
title: "Comment : identifier les symboles dans une biblioth&#232;que | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Appeler l'outil de navigateur, identification des symboles dans la bibliothèque"
  - "Appeler l'outil de navigateur"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment : identifier les symboles dans une biblioth&#232;que
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

les outils de Symbole\-navigation affichent des vues hiérarchiques des symboles.  Les symboles représentent les espaces de noms, des objets, des classes, des membres de la classe, et d'autres éléments de langage.  
  
 Chaque symbole dans la hiérarchie peut être identifié par les informations de navigation passées par la bibliothèque de symboles au gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] via des interfaces suivantes :  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 L'emplacement du symbole dans la hiérarchie respecte un symbole.  Elle permet aux outils de symbole\-navigation pour accéder à un symbole spécifique.  L'unique, chemin qualifié complet du symbole détermine l'emplacement.  Chaque élément du chemin d'accès est un nœud.  Le démarrage du tracé avec le nœud de niveau supérieur et se termine avec le symbole spécifique.  Par exemple, si la méthode M1 est membre de la classe de C1 et C1 se trouve dans l'espace de noms N1, le chemin d'accès complet de la méthode M1 est N1. C1. M1.  Ce chemin d'accès contient trois nœuds : N1, C1, et M1.  
  
 Les informations de navigation permettent au gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour les localiser, sélectionner et conserver a sélectionné les symboles dans la hiérarchie.  Il permet de naviguer d'un outil la navigation vers un autre.  Lors de l'utilisation **Explorateur d'objets** pour parcourir des symboles dans un projet de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] , vous pouvez cliquer avec le bouton droit sur une méthode et démarrer l'outil d' **Explorateur d'appels** pour consulter la méthode dans un graphique des appels.  
  
 Deux formulaires décrivent l'emplacement de symboles.  La forme canonique est basé sur le chemin qualifié complet du symbole.  Il représente une seule position du symbole dans la hiérarchie.  Il est indépendant de l'outil de symbole\-navigation.  Pour obtenir des informations de format canonique, le gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> .  Le formulaire de vue d'ensemble décrit l'emplacement du symbole dans un outil spécifique de symbole\-navigation.  La position du symbole est relative à la position d'autres symboles dans le hierarchicy.  Un symbole donné peut avoir plusieurs chemins d'accès de présentation, mais un seul chemin d'accès canonique.  Par exemple, si la classe de C1 est héritée de la classe de C2 et les deux classes dans l'espace de noms N1, **Explorateur d'objets** affiche l'arborescence hiérarchique suivante :  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 le chemin d'accès canonique de la classe de C2, dans cet exemple, est N1 \+ C2.  Le chemin d'accès de présentation de C2 inclut nœuds de C1 et de « bases et d'interfaces » : N1 \+ C1 \+ « bases et interfaces » \+ C2.  
  
 Pour obtenir les informations du formulaire de présentation, le gestionnaire d'objets appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .  
  
## identifier un symbole dans la hiérarchie  
  
#### Pour obtenir des informations canoniques et de la présentation de formulaires  
  
1.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Le gestionnaire d'objets appelle cette méthode pour obtenir la liste de nœuds contenus dans le chemin d'accès canonique du symbole.  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Le gestionnaire d'objets appelle cette méthode pour obtenir la liste de nœuds contenus dans le chemin d'accès de présentation du symbole.  
  
## Voir aussi  
 [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Comment : inscrire une bibliothèque avec le Gestionnaire d'objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Comment : exposer de listes de symboles fournis par la bibliothèque pour le Gestionnaire d'objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)