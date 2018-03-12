---
title: "L’accès à la mémoire tampon de texte à l’aide de l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 77002e095690da85e73f1a79d405cb5174b96851
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>L’accès à la mémoire tampon de texte à l’aide de l’API héritée
Le texte est chargé de gérer le flux de texte et la persistance du fichier. Bien que la mémoire tampon pour lire ou écrire d’autres formats, toutes les communications normales avec la mémoire tampon sont effectuée à l’aide d’Unicode. Dans les API héritées, la mémoire tampon de texte permettre utiliser - ou un système de coordonnées à deux dimensions pour identifier les emplacements de caractère dans la mémoire tampon.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Dimension un et deux repères  
 Une position de coordonnée unidimensionnelle est basée sur la position d’un caractère à partir du premier caractère dans la mémoire tampon, comme 147. Vous utilisez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interface pour accéder à un emplacement unidimensionnel dans la mémoire tampon. Un système de coordonnées à deux dimensions est basé sur des paires de ligne et d’index. Par exemple, un caractère dans la mémoire tampon à 43, 5 serait de ligne 43, cinq caractères à droite du premier caractère dans la ligne. Accéder à un emplacement à deux dimensions de la mémoire tampon en utilisant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface. À la fois le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> les interfaces sont implémentées par l’objet de mémoire tampon de texte (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) et sont accessibles à partir de l’autre à l’aide de `QueryInterface`. Le diagramme suivant illustre ces et autres interfaces de clé sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Objet de mémoire tampon de texte](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Objet de mémoire tampon de texte  
  
 Bien qu’un système de coordonnées fonctionne dans la mémoire tampon de texte, il est optimisé pour utiliser des coordonnées à deux dimensions. Un système de coordonnées unidimensionnel peut dégrader les performances. Par conséquent, utilisez le système de coordonnées à deux dimensions autant que possible.  
  
 La responsabilité de seconde de la mémoire tampon de texte est la persistance du fichier. Pour ce faire, l’objet de mémoire tampon de texte implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et agit comme le composant d’objet de données de document pour les éléments de projet et d’autres composants d’environnement impliquées dans la persistance. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modification des paramètres de la vue à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explique comment modifier les paramètres d’affichage à l’aide de l’API héritée.  
  
 [À l’aide du Gestionnaire de texte pour surveiller des paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explique comment utiliser le Gestionnaire de texte pour contrôler les paramètres globaux...  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)