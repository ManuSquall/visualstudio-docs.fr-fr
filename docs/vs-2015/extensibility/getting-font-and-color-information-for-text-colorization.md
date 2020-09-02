---
title: Obtention d’informations sur la police et la couleur pour la coloration du texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696855"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtention des informations sur la couleur et la police pour la colorisation du texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le processus qui restitue ou affiche du texte en couleur dans les éléments d’interface utilisateur dépend du type de projet, de sa technologie et des préférences de développeur. La page de propriétés **polices et couleurs** stocke les paramètres.  
  
 La plupart des implémentations qui affichent du texte en couleur nécessitent les `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaces et associées pour la présentation, la récupération et le stockage des paramètres d’affichage de texte.  
  
> [!NOTE]
> Lors de la personnalisation de l’éditeur principal (qui prend en charge le **texte EditorCategory**), il est fortement recommandé d’utiliser la technologie de coloration dans le service de langage. Pour plus d’informations, consultez [vue d’ensemble des polices et des couleurs](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtention d’informations sur la police et la couleur par défaut  
 Tous les paramètres de **polices et de couleurs** de toute fenêtre affichant du texte doivent être spécifiés dans les **éléments d’affichage** d’une **catégorie**. Pour plus d’informations, consultez [polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Pour coloriser, un VSPackage doit obtenir les paramètres actuels **des polices et des couleurs** . Un VSPackage peut y parvenir de l’une des manières suivantes, en fonction de ses besoins :  
  
- Utilisez le mécanisme de persistance de police et de couleur pour récupérer l’État stocké ou actuel. Pour plus d’informations, consultez [accès aux paramètres de police et de couleur stockés](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Utilisez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface d’un service qui fournit des données de police et de couleur pour obtenir une instance de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , si le VSPackage n’est pas également le fournisseur de polices et de couleurs.  
  
- Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Pour vous assurer que les résultats obtenus par l’interrogation sont à jour, il peut être utile d’utiliser l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour est nécessaire avant d’appeler les méthodes de récupération de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
  Une fois que vous avez obtenu les informations de police et de couleur, analysez le texte à afficher pour identifier les éléments nécessitant une colorisation, puis affichez le texte dans la fenêtre à l’aide des polices et des couleurs appropriées.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilisation des polices et du texte](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Utilisation des couleurs](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (Graphics Device Interface)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
