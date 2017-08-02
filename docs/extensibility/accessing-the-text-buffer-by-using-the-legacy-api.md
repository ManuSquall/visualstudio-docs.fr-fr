---
title: "L&#39;acc&#232;s &#224; la m&#233;moire tampon de texte &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - mémoires tampons de texte"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# L&#39;acc&#232;s &#224; la m&#233;moire tampon de texte &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le texte est chargé de gérer les flux de texte et la persistance de fichier.  Bien que la mémoire tampon puisse lire ou écrire dans d'autres formats, toutes les communications ordinaire avec la mémoire tampon est exécutée à l'aide de Unicode.  Dans les API héritées, la mémoire tampon de texte peut utiliser un ou un à deux dimensions système de coordonnées pour identifier des emplacements de caractères dans la mémoire tampon.  
  
## systèmes de coordonnées un et de Deux\-Dimension  
 Une position des coordonnées unidimensionnel est basé sur une position de l'impression du premier caractère de la mémoire tampon, telle que 147.  Vous utilisez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> pour accéder à un emplacement unidimensionnel dans la mémoire tampon.  Un système de coordonnées à deux dimensions est basé sur les paires de ligne et d'index.  Par exemple, un caractère de la mémoire tampon à 43, 5 serait sur la ligne 43, cinq caractères à droite du premier caractère de cette ligne.  Vous accédez à un emplacement à deux dimensions dans la mémoire tampon à l'aide de l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> .  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> et les interfaces d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> sont implémentés par l'objet de mémoire tampon de texte \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\) et sont accessibles entre eux à l'aide de `QueryInterface`.  Le diagramme suivant illustre ces derniers et d'autres interfaces de clé sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Objet de mémoire tampon de texte](~/extensibility/media/vstextbuffer.gif "vsTextBuffer")  
objet de mémoire tampon de texte  
  
 Bien que l'un ou l'autre de système de coordonnées s'exécute dans la mémoire tampon de texte, il est optimisé pour utiliser des coordonnées à deux dimensions.  Un système de coordonnées unidimensionnel peut créer une baisse des performances.  Par conséquent, utilisez le système de coordonnées à deux dimensions autant que possible.  
  
 La responsabilité de la mémoire tampon de texte deuxième est persistance de fichier.  Pour ce faire, l'objet de mémoire tampon de texte implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et agit comme un composant d'objet de données du document pour les éléments de projet et d'autres composants d'environnement impliqués dans la persistance.  Pour plus d'informations, consultez [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md).  
  
## Dans cette section  
 [Modification des paramètres d'affichage à l'aide de l'API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explique comment modifier les ajustements d'affichage à l'aide de l'API héritée.  
  
 [Utilisation du Gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explique comment utiliser le gestionnaire de texte pour contrôler des paramètres globaux.  
  
## Voir aussi  
 [Dans l'éditeur de base](../extensibility/inside-the-core-editor.md)