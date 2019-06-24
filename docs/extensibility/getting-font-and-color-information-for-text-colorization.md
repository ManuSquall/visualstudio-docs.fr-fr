---
title: L’obtention de la police et les informations de couleur de colorisation de texte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b35e52effe9a261eeb159ca9460e4351ae5f658
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342498"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Obtenir des informations de police et de couleur pour la colorisation de texte
Le processus qui effectue le rendu ou affiche le texte en couleurs se dans les éléments d’interface (UI) utilisateur varie selon le type de préférences de projet, sa technologie et les développeurs. Le **polices et couleurs** page de propriétés stocke les paramètres.

 La plupart des implémentations qui affichent du texte en couleurs se doivent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> et associés des interfaces pour les paramètres d’affichage de présentation, la récupération et le stocker du texte.

> [!NOTE]
> Lors de la personnalisation de l’éditeur principal (qui prend en charge la **texte EditorCategory**), il est recommandé d’utiliser la technologie de coloration dans le service de langage. Pour plus d’informations, consultez [vue d’ensemble de police et couleur](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Obtenir des informations de police et la couleur par défaut
 Tous les le **polices et couleurs** paramètres de n’importe quelle fenêtre d’affichage du texte doivent être spécifiés dans le **éléments affichés** d’un **catégorie**. Pour plus d’informations, consultez [polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Pour mettre en couleur, un VSPackage doit obtenir actuel **polices et couleurs** paramètres. Un VSPackage peut obtenir les paramètres actuels de plusieurs manières, selon ses besoins :

- Utiliser le mécanisme de persistance de police et de couleur pour récupérer l’état stockée ou en cours. Pour plus d’informations, consultez [accès stockés des paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).

- Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface d’un service qui fournit des données de police et de couleur pour obtenir une instance de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, si le VSPackage n’est pas également le fournisseur de police et de couleur.

- Implémentez l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Pour garantir que les résultats obtenus par l’interrogation sont à jour, il peut être utile d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour est nécessaire avant d’appeler les méthodes de récupération de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

Après avoir obtenu les informations de police et couleur, analyser le texte à afficher pour identifier les éléments qui nécessitent la colorisation. Afficher le texte dans la fenêtre à l’aide appropriées polices et couleurs.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Utilisez des polices et texte](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Utiliser des couleurs](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (interface graphique)](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)