---
title: Implémentation des catégories personnalisées et affichage des éléments | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839538"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implémentation de catégories personnalisées et d’éléments d’affichage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage peut fournir le contrôle des polices et des couleurs de son texte à l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE) via des catégories personnalisées et des éléments d’affichage.  
  
 Les catégories personnalisées et les éléments affichés se trouvent dans la page de propriétés **polices et couleurs** . Pour ouvrir la page de propriétés **polices et couleurs** , dans le menu **Outils** , cliquez sur **options**. Développez **environnement** , puis cliquez sur **polices et couleurs**.  
  
 Lors de l’utilisation de ce mécanisme, les VSPackages doivent implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface et ses interfaces associées.  
  
 En principe, ce mécanisme peut être utilisé pour modifier tous les **éléments d’affichage** existants et les **catégories** qui les contiennent. Toutefois, il ne doit pas être utilisé pour modifier le **texte EditorCategory** ou ses **éléments d’affichage**. Pour plus d’informations, consultez [vue d’ensemble des polices et des couleurs](../extensibility/font-and-color-overview.md).  
  
 Pour implémenter des **catégories** personnalisées ou des **éléments d’affichage**, un VSPackage doit :  
  
- Créez ou identifiez des catégories dans le registre.  
  
   L’implémentation de l’IDE de la page de propriétés **polices et couleurs** utilise ces informations pour interroger correctement le service qui prend en charge une catégorie donnée.  
  
- Créez ou identifiez des groupes (facultatif) dans le registre.  
  
   Il peut être utile de définir un groupe, qui représente l’Union de deux catégories ou plus. Si un groupe est défini, l’IDE fusionne automatiquement les sous-catégories et distribue les éléments affichés au sein du groupe.  
  
- Implémenter la prise en charge de l’IDE.  
  
- Gérer les modifications de police et de couleur.  
  
  Pour plus d’informations, consultez [accès aux paramètres de police et de couleur stockés](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Pour créer ou identifier des catégories  
  
- Construire un type spécial d’entrée de Registre Category sous [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ]  
  
   *\<Category>* est le nom non localisé de la catégorie.  
  
- Remplissez le Registre avec deux valeurs :  
  
  |Nom|Type|Données|Description|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|GUID créé pour identifier la catégorie.|  
  |Package|REG_SZ|GUID|GUID du service VSPackage qui prend en charge la catégorie.|  
  
  Le service spécifié dans le registre doit fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> pour la catégorie correspondante.  
  
## <a name="to-create-or-identify-groups"></a>Pour créer ou identifier des groupes  
  
- Construire un type spécial d’entrée de Registre Category sous [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ]  
  
   *\<group>* est le nom non localisé du groupe.  
  
- Remplissez le Registre avec deux valeurs :  
  
  |Nom|Type|Données|Description|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|GUID créé pour identifier le groupe.|  
  |Package|REG_SZ|GUID|GUID du service qui prend en charge la catégorie.|  
  
  Le service spécifié dans le registre doit fournir une implémentation de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` pour le groupe correspondant.  
  
## <a name="to-implement-ide-support"></a>Pour implémenter la prise en charge IDE  
  
- Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> , qui retourne soit une interface, soit <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> une `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface à l’IDE pour chaque **catégorie** ou GUID de groupe fourni.  
  
- Pour chaque **catégorie** qu’il prend en charge, un VSPackage implémente une instance distincte de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface.  
  
- Les méthodes implémentées par le biais de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> doivent fournir l’IDE avec :  
  
  - Répertorie les **éléments affichés** dans la **catégorie.**  
  
  - Noms localisables pour les **éléments affichés**.  
  
  - Affiche des informations pour chaque membre de la **catégorie**.  
  
  > [!NOTE]
  > Chaque **catégorie** doit contenir au moins un **élément d’affichage**.  
  
- L’IDE utilise l' `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface pour définir une Union de plusieurs catégories.  
  
   Son implémentation fournit l’IDE avec :  
  
  - Liste des **catégories** qui composent un groupe donné.  
  
  - Accès aux instances de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> prenant en charge chaque **catégorie** au sein du groupe.  
  
  - Noms de groupes localisables.  
  
- Mise à jour de l’IDE :  
  
   L’IDE met en cache les informations sur les paramètres de **police et de couleur** . Par conséquent, après toute modification de la configuration de la **police et** de la couleur de l’IDE, il est recommandé de s’assurer que le cache est à jour.  
  
  La mise à jour du cache s’effectue par le biais de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface et peut être effectuée globalement ou uniquement sur des éléments sélectionnés.  
  
## <a name="to-handle-font-and-color-changes"></a>Pour gérer les modifications de police et de couleur  
 Pour prendre en charge correctement la coloration du texte affiché par le VSPackage, le service de colorisation qui le prend en charge doit répondre aux modifications effectuées par l’utilisateur via la page **de propriétés polices et couleurs** . Pour ce faire, un VSPackage effectue ce qui suit :  
  
- Gestion des événements générés par l’IDE en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interface.  
  
     L’IDE appelle la méthode appropriée après les modifications de l’utilisateur de la page **polices et couleurs** . Par exemple, il appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> méthode si une nouvelle police est sélectionnée.  
  
     - ou -  
  
- Interrogation de l’IDE pour les modifications.  
  
     Cela peut être effectué par le biais de l’interface implémentée par le système <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Bien qu’principalement pour la prise en charge de la persistance, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> méthode peut être utilisée pour obtenir des informations sur la police et la couleur pour les **éléments affichés**. Pour plus d’informations, consultez [accès aux paramètres de police et de couleur stockés](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Pour vous assurer que les résultats obtenus par l’interrogation sont corrects, il peut être utile d’utiliser l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si un vidage et une mise à jour du cache sont nécessaires avant d’appeler les méthodes de récupération de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Obtention d’informations sur la police et la couleur pour la coloration du texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Accès aux paramètres de police et de couleur stockés](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Comment : accéder aux polices et au modèle de couleurs intégrés](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Présentation de la couleur et de la police](../extensibility/font-and-color-overview.md)
