---
title: Mise en route de la police et les informations de couleur de colorisation de texte | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3b31ad2ec080070dec3c68b304f400d204d47a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Mise en route de la police et les informations de couleur de colorisation de texte
Le processus qui effectue le rendu ou affiche du texte impriment dans les éléments d’interface utilisateur utilisateur varie selon le type de projet, sa technologie et developer de préférences. Le **polices et couleurs** page de propriétés stocke les paramètres.  
  
 La plupart des implémentations qui affichent du texte impriment peut-être le `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` et associé les interfaces pour les paramètres d’affichage de présentation et la récupération de stocker du texte.  
  
> [!NOTE]
>  Lors de la personnalisation de l’éditeur principal (qui prend en charge la **texte EditorCategory**), il est fortement recommandé d’utiliser la technologie de coloration de la syntaxe dans le service de langage. Pour plus d’informations, consultez [vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Mise en route de la police par défaut et les informations de couleur  
 Tous les le **polices et couleurs** paramètres de n’importe quelle fenêtre d’affichage du texte doivent être spécifiés dans le **éléments affichés** d’un **catégorie**. Pour plus d’informations, consultez [polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Pour mettre en couleur, un VSPackage doit obtenir actuel **polices et couleurs** paramètres. Un VSPackage ce faire de plusieurs manières, selon ses besoins :  
  
-   Utilisez le mécanisme de persistance de police et de couleur pour récupérer l’état stocké ou en cours. Pour plus d’informations, consultez [l’accès à stockées paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface d’un service qui fournit les données de police et de couleur pour obtenir une instance de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, si le package Visual Studio n’est pas également le fournisseur de couleurs et de polices.  
  
-   Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
 Pour garantir que les résultats obtenus par l’interrogation sont à jour, il peut être utile d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour est nécessaire avant d’appeler les méthodes de récupération de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
 Après avoir obtenu les informations de police et la couleur, analysez le texte à afficher pour identifier les éléments nécessitant la colorisation et ensuite afficher le texte dans la fenêtre en utilisant les polices appropriées et les couleurs.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilisation de polices et texte](/dotnet/framework/winforms/advanced/using-fonts-and-text)   
 [Utilisation des couleurs](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (interface graphique)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)