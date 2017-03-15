---
title: "L’acc&#232;s &#224; stock&#233;e param&#232;tres de police et couleur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "polices, l’accès aux paramètres stockés"
  - "police et couleur de contrôle (Visual Studio SDK), persistance"
  - "couleurs, l’accès aux paramètres stockés"
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# L’acc&#232;s &#224; stock&#233;e param&#232;tres de police et couleur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) stocke les paramètres modifiés pour les polices et couleurs dans le Registre. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface pour accéder à ces paramètres.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Pour initier la persistance de l’état des polices et couleurs  
 Les informations de police et la couleur sont stockées par catégorie dans l’emplacement suivant : [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\< version de Visual Studio>*\FontAndColors\\*\< CategoryGUID>*], où *\< CategoryGUID>* est le GUID de catégorie.  
  
 Par conséquent, pour initier la persistance, un VSPackage doit :  
  
-   Obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface en appelant `QueryService` sur le fournisseur de services globaux.  
  
     `QueryService` doit être appelée à l’aide d’un argument ID service `SID_SVsFontAndColorStorage` et l’argument ID interface `IID_IVsFontAndColorStorage`.  
  
-   Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> méthode pour ouvrir une catégorie à rendre persistantes à l’aide du GUID de la catégorie et un indicateur de mode en tant qu’arguments.  
  
     Le mode spécifié par la `fFlags` argument, est construit à partir des valeurs dans le <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> (énumération). Contrôles de ce mode :  
  
    -   Les paramètres qui sont accessibles via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
    -   Tous les paramètres ou uniquement ceux que les utilisateurs à modifier et qui sont récupérables par les <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
    -   La manière de propager les modifications apportées aux paramètres utilisateur.  
  
    -   Le format des valeurs de couleur sont utilisés.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Pour utiliser la persistance de l’état des polices et couleurs  
 Couleurs et polices persistantes implique :  
  
-   Synchroniser les paramètres IDE avec paramètres stockés dans le Registre.  
  
-   Propagation des informations de modification du Registre.  
  
-   Définition et récupération des paramètres stockés dans le Registre.  
  
 Synchronisation du paramètre de stockage avec les paramètres de l’IDE est largement transparent. L’IDE sous-jacent écrit automatiquement les paramètres mis à jour de **Afficher les éléments** pour les entrées de Registre de catégories.  
  
 Si plusieurs packages VS partagent une catégorie particulière, un VSPackage nécessite que les événements sont générés lorsque les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface sont utilisés pour modifier les paramètres de Registre stockée.  
  
 Par défaut, la génération d’événements n’est pas activée. Pour activer la génération des événements, une catégorie doit être ouvert à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Cela force l’IDE à appeler approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> méthode qui implémente un VSPackage.  
  
> [!NOTE]
>  Modifications via le **police et couleur** page de propriétés générer des événements indépendants de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour des paramètres de police et la couleur de mise en cache est nécessaire avant d’appeler les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> (classe).  
  
### <a name="storing-and-retrieving-information"></a>Le stockage et la récupération des informations  
 Pour obtenir ou configurer les informations dont un utilisateur peut modifier pour un élément d’affichage nommé dans une catégorie d’ouvrir, appelez VSPackages le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> méthodes.  
  
 Pour une catégorie particulière est obtenue à l’aide des attributs d’informations sur la police du <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> méthodes.  
  
> [!NOTE]
>  Le `fFlags` argument passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> méthode lors de l’ouverture de cette catégorie définit le comportement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> méthodes. Par défaut, ces itemsthat d’aboutdisplay méthodes retournent uniquement des informations ont été modifiés. Toutefois, si une catégorie est ouverte à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> indicateur, les deux mises à jour et éléments inchangés affichés sont accessibles par <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Par défaut, uniquement modifié **éléments affichés** informations sont conservées dans le Registre. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface ne peut pas être utilisée pour récupérer tous les paramètres de polices et couleurs.  
  
> [!NOTE]
>  Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> méthodes retournent REGDB_E_KEYMISSING, (0x80040152L) lorsque vous les utilisez pour récupérer des informations sur inchangé **Afficher les éléments**.  
  
 Les paramètres de tous les **Afficher les éléments** dans un rôle particulier **catégorie** peut être obtenu à l’aide des méthodes de la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interface.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [L’implémentation des catégories personnalisées et afficher les éléments](../extensibility/implementing-custom-categories-and-display-items.md)