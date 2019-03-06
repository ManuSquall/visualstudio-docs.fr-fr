---
title: L’accès à la mémoire tampon de texte à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dc331e06d1e82928f5c608d5b009258beb48dcc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722445"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Accéder à la mémoire tampon de texte à l’aide de l’API héritée
Le texte est chargé de gérer les flux de texte et la persistance du fichier. Bien que la mémoire tampon pour lire ou écrire les autres formats, toutes les communications normales avec la mémoire tampon sont effectuée à l’aide d’Unicode. Dans les API héritées, la mémoire tampon de texte peut utiliser soit un une ou un système de coordonnées à deux dimensions pour identifier les emplacements de caractère dans la mémoire tampon.

## <a name="one--and-two-dimension-coordinate-systems"></a>Et deux-unidimensionnel coordonner les systèmes
 Une position de la coordonnée unidimensionnelle repose sur la position d’un caractère à partir du premier caractère dans la mémoire tampon, tels que 147. Vous utilisez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interface pour accéder à un emplacement unidimensionnel dans la mémoire tampon. Un système de coordonnées à deux dimensions est basé sur des paires de ligne et d’index. Par exemple, un caractère dans la mémoire tampon à 43, 5 serait de ligne 43, cinq caractères à droite du premier caractère dans la ligne. Vous accédez à un emplacement à deux dimensions de la mémoire tampon en utilisant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface. À la fois le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaces sont implémentées par l’objet de mémoire tampon de texte (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) et est accessible à partir de l’autre à l’aide de `QueryInterface`. Le diagramme suivant illustre ces et autres interfaces de clé sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

 ![Objet de mémoire tampon de texte](../extensibility/media/vstextbuffer.gif "vsTextBuffer") objet de mémoire tampon de texte

 Bien que le de ces systèmes de coordonnées fonctionne dans la mémoire tampon de texte, il est optimisé pour utiliser des coordonnées à deux dimensions. Un système de coordonnées unidimensionnel peut dégrader les performances. Par conséquent, utilisez le système de coordonnées à deux dimensions autant que possible.

 Le deuxième responsabilité de la mémoire tampon de texte est une persistance de fichiers. Pour ce faire, l’objet de mémoire tampon de texte implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et agit comme le composant d’objet de données de document pour les éléments de projet et d’autres composants d’environnement impliquées dans la persistance. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md).

## <a name="in-this-section"></a>Dans cette section
- [Modifier les paramètres d’affichage à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md) explique comment modifier les paramètres de vue à l’aide de l’API héritée.

- [Utilisez le Gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md) explique comment utiliser le Gestionnaire de texte pour surveiller les paramètres globaux.

## <a name="see-also"></a>Voir aussi
- [À l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md)