---
title: L’obtention de la police et les informations de couleur de colorisation de texte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d4b5ebbaea2b146f1b853360b88bad2363ce77f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516650"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>L’obtention de la police et les informations de couleur de colorisation de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [obtention de la police et les informations de couleur de colorisation de texte](https://docs.microsoft.com/visualstudio/extensibility/getting-font-and-color-information-for-text-colorization).  
  
Le processus qui effectue le rendu ou affiche le texte en couleurs se dans les éléments d’interface (UI) utilisateur varie selon le type de préférences de projet, sa technologie et les développeurs. Le **polices et couleurs** page de propriétés stocke les paramètres.  
  
 La plupart des implémentations qui affichent du texte en couleurs se doivent le `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` et associés des interfaces pour les paramètres d’affichage de présentation, la récupération et le stocker du texte.  
  
> [!NOTE]
>  Lors de la personnalisation de l’éditeur principal (qui prend en charge la **texte EditorCategory**), il est fortement recommandé d’utiliser la technologie de coloration dans le service de langage. Pour plus d’informations, consultez [vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtention des informations de couleur et de police par défaut  
 Tous les le **polices et couleurs** paramètres de n’importe quelle fenêtre d’affichage du texte doivent être spécifiés dans le **éléments affichés** d’un **catégorie**. Pour plus d’informations, consultez [polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Pour mettre en couleur, un VSPackage doit obtenir actuel **polices et couleurs** paramètres. Un VSPackage pour ce faire de plusieurs manières, selon ses besoins :  
  
-   Utiliser le mécanisme de persistance de police et de couleur pour récupérer l’état stockée ou en cours. Pour plus d’informations, consultez [l’accès à stockées paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface d’un service qui fournit les données de police et de couleur pour obtenir une instance de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, si le VSPackage n’est pas également le fournisseur de police et de couleur.  
  
-   Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
 Pour garantir que les résultats obtenus par l’interrogation sont à jour, il peut être utile d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour est nécessaire avant d’appeler les méthodes de récupération de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
 Après avoir obtenu les informations de police et couleur, analyser le texte à afficher pour identifier les éléments nécessitant la colorisation et ensuite afficher le texte dans la fenêtre à l’aide appropriées polices et couleurs.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilisation de polices et texte](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Utilisation des couleurs](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (interface graphique)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

