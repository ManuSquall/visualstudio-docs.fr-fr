---
title: Accès à la mémoire tampon de texte à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185011"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Accès à la mémoire tampon du texte à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le texte est responsable de la gestion des flux de texte et de la persistance des fichiers. Même si la mémoire tampon peut lire ou écrire dans d’autres formats, toute communication ordinaire avec la mémoire tampon est effectuée à l’aide d’Unicode. Dans les API héritées, la mémoire tampon de texte peut utiliser un système de coordonnées à une ou deux dimensions pour identifier les emplacements de caractère dans la mémoire tampon.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Systèmes de coordonnées à une ou deux dimensions  
 La position d’une coordonnée unidimensionnelle est basée sur la position d’un caractère à partir du premier caractère de la mémoire tampon, par exemple 147. Vous utilisez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interface pour accéder à un emplacement unidimensionnel dans la mémoire tampon. Un système de coordonnées à deux dimensions est basé sur des paires de lignes et d’index. Par exemple, un caractère de la mémoire tampon à 43, 5 se trouve à la ligne 43, cinq caractères à droite du premier caractère de cette ligne. Vous accédez à un emplacement à deux dimensions dans la mémoire tampon à l’aide de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interface. Les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaces et sont implémentées par l’objet de mémoire tampon de texte ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ) et sont accessibles les unes par rapport aux autres à l’aide de `QueryInterface` . Le diagramme suivant illustre ces interfaces clés et d’autres sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Objet de mémoire tampon de texte](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Objet de mémoire tampon de texte  
  
 Bien qu’un système de coordonnées fonctionne dans la mémoire tampon de texte, il est optimisé pour utiliser des coordonnées à deux dimensions. Un système de coordonnées unidimensionnel peut créer une surcharge de performance. Par conséquent, utilisez le système de coordonnées à deux dimensions dans la mesure du possible.  
  
 La seconde responsabilité de la mémoire tampon de texte est la persistance du fichier. Pour ce faire, l’objet de mémoire tampon de texte implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et agit comme composant de l’objet de données de document pour les éléments de projet et d’autres composants d’environnement impliqués dans la persistance. Pour plus d’informations, consultez [ouverture et enregistrement d’éléments de projet](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modification des paramètres d’affichage à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explique comment modifier les paramètres d’affichage à l’aide de l’API héritée.  
  
 [Utilisation du gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explique comment utiliser le gestionnaire de texte pour analyser les paramètres globaux.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’intérieur de l’éditeur de base](../extensibility/inside-the-core-editor.md)
