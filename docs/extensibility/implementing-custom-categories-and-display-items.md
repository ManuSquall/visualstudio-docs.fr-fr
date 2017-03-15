---
title: "L’implémentation des catégories personnalisées et des éléments d’affichage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d117676515988f1bf7f73ed1e9786c7c2919135e
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-custom-categories-and-display-items"></a>L’implémentation des catégories personnalisées et afficher les éléments
Un VSPackage peut fournir le contrôle des polices et couleurs de son texte à le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) par le biais des catégories personnalisées et des éléments affichés.  
  
 Afficher les éléments et les catégories personnalisées sont sur le **polices et couleurs** page de propriétés. Pour ouvrir le **polices et couleurs** page de propriété, sur le **outils** menu, cliquez sur **Options**. Développez **environnement** , puis **polices et couleurs**.  
  
 Lorsque vous utilisez ce mécanisme, VSPackages doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interface et ses interfaces associées.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
 En principe, ce mécanisme peut être utilisé pour modifier tous les **afficher les éléments** et **catégories** qui les contiennent. Toutefois, il ne doit pas être utilisé pour modifier la **texte EditorCategory** ou son **afficher les éléments**. Pour plus d’informations, consultez [vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md).  
  
 Pour implémenter un gestionnaire **catégories** ou **afficher les éléments**, un VSPackage doit :  
  
-   Créez ou identifiez les catégories dans le Registre.  
  
     Implémentation de l’IDE de le **polices et couleurs** page de propriétés utilise ces informations pour interroger correctement pour le service de prise en charge d’une catégorie donnée.  
  
-   Créez ou identifiez les groupes (facultatifs) dans le Registre.  
  
     Il peut être utile de définir un groupe qui représente l’union de deux ou plusieurs catégories. Si un groupe est défini, l’IDE fusionne les sous-catégories automatiquement et distribue les éléments affichés dans le groupe.  
  
-   Implémenter la prise en charge de l’IDE.  
  
-   Gérer les modifications de police et la couleur.  
  
 Pour plus d’informations, consultez [l’accès à stockées paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Pour créer ou identifier des catégories  
  
-   Construire un type spécial d’entrée de Registre de catégorie sous [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<version de Visual Studio >*\FontAndColors\\`<Category>`]  
  
     *\<Catégorie >* est le nom non localisé de la catégorie.  
  
-   Remplir le Registre avec deux valeurs :  
  
    |Nom|Type|Données|Description|  
    |----------|----------|----------|-----------------|  
    |Catégorie|REG_SZ|GUID|Un GUID est créé pour identifier la catégorie.|  
    |Package|REG_SZ|GUID|Le GUID du service VSPackage qui prend en charge de la catégorie.|  
  
 Le service spécifié dans le Registre doit fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>pour la catégorie correspondante.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
## <a name="to-create-or-identify-groups"></a>Pour créer ou identifier des groupes  
  
-   Construire un type spécial d’entrée de Registre de catégorie sous [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<version de Visual Studio >*\FontAndColors\\*\<groupe >*]  
  
     *\<groupe >* est le nom non localisé du groupe.  
  
-   Remplir le Registre avec deux valeurs :  
  
    |Nom|Type|Données|Description|  
    |----------|----------|----------|-----------------|  
    |Catégorie|REG_SZ|GUID|Un GUID est créé pour identifier le groupe.|  
    |Package|REG_SZ|GUID|Le GUID du service qui prend en charge de la catégorie.|  
  
 Le service spécifié dans le Registre doit fournir une implémentation de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` pour le groupe correspondant.  
  
## <a name="to-implement-ide-support"></a>Pour implémenter la prise en charge IDE  
  
-   Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, qui retourne un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>interface ou un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface à l’IDE pour chaque **catégorie** ou groupe GUID fourni.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>  
  
-   Pour chaque **catégorie** pris en charge, un VSPackage qui implémente une instance distincte de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
-   Les méthodes implémentées via <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>doit fournir l’IDE avec :</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   Listes de **afficher les éléments** dans les **catégorie.**  
  
    -   Noms localisables pour **afficher les éléments**.  
  
    -   Afficher des informations pour chaque membre de **catégorie**.  
  
    > [!NOTE]
    >  Chaque **catégorie** doit contenir au moins un **afficher l’élément**.  
  
-   L’IDE utilise le `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface pour définir une union de plusieurs catégories.  
  
     Son implémentation fournit l’environnement de développement intégré :  
  
    -   Une liste de la **catégories** qui composent un groupe donné.  
  
    -   Accès aux instances du <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>prenant en charge chaque **catégorie** au sein du groupe.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   Noms de groupe localisable.  
  
-   Mise à jour de l’IDE :  
  
     L’IDE met en cache les informations sur les **police et couleur** paramètres. Par conséquent, après toute modification de l’environnement IDE **police et couleur** configuration, il est recommandé de s’assurer que le cache est mis à jour.  
  
 Mise à jour du cache s’effectue via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>de l’interface et peut être effectuées seulement ou globalement sélectionnées.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="to-handle-font-and-color-changes"></a>Pour gérer la police et la couleur des modifications  
 Pour correctement prendre en charge la colorisation de texte qui affiche un VSPackage, le service de colorisation prenant en charge le VSPackage doit répondre aux modifications initiées par l’utilisateur via la **polices et couleurs** page de propriétés. Un VSPackage pour ce faire :  
  
-   La gestion des événements générés par l’IDE en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
     L’IDE appelle la méthode appropriée après les modifications de l’utilisateur de la **polices et couleurs** page. Par exemple, il appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>méthode si une nouvelle police est sélectionnée.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>  
  
     ou  
  
-   Interrogation de l’IDE pour les modifications.  
  
     Cela est possible via le système implémenté <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Bien que principalement pour la prise en charge de la persistance, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>méthode peut être utilisée pour obtenir des informations de police et la couleur pour **afficher les éléments**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Pour plus d’informations, consultez [l’accès à stockées paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Pour garantir que les résultats obtenus par l’interrogation sont corrects, il peut être utile d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>interface pour déterminer si un vidage du cache et la mise à jour sont nécessaires avant d’appeler les méthodes d’extraction de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Mise en route de la police et les informations de couleur de colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L’accès à stockée paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Comment : accéder aux polices intégrées et jeu de couleurs](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md)
