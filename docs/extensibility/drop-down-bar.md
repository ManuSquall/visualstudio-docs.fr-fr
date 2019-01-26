---
title: Barre déroulante | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3506ff05bf7551a66ea616ca4c49dbf6ea80f4a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949283"
---
# <a name="drop-down-bar"></a>Barre déroulante
La barre déroulante est fournie en haut de la fenêtre de code et contient deux listes déroulantes.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de barre déroulante  
 Dans [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], par exemple, la barre déroulante contient des listes pour [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] éléments et [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] fonctions de membres d’éléments, comme illustré dans l’image suivante.  
  
 ![DROP&#45;bas barres](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barre déroulante  
  
 Lors de l’implémentation d’une barre déroulante, il existe quatre interfaces de première importance :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implémentez cette interface pour insérer le contenu de la barre déroulante. Chaque combinaison de liste déroulante peut contenir du texte brut ou texte fantaisie (gras, souligné ou italique), peut avoir coloration de la fenêtre texte police ou des couleurs de police grisé et peut éventuellement fournir un petit bitmap en regard de l’élément de liste déroulante. Similaire à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface, les images bitmap sont fournies dans les listes d’images. Chaque combinaison de liste déroulante peut avoir une liste d’images différents ; Toutefois, chaque liste d’images doit contenir des images de la même hauteur. En outre, à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> (méthode), vous pouvez fournir une info-bulle pour chaque combinaison.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Appelez cette interface pour créer ou détruire la barre déroulante pour une fenêtre de code. Cette interface peut également être utilisée pour déterminer si une barre déroulante est déjà attachée à une fenêtre de code en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> (méthode). Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Appelez cette interface pour communiquer directement avec la barre déroulante. Vous pouvez utiliser cette interface pour forcer une actualisation de la liste déroulante barre contenu ou pour modifier la sélection de l’une des zones de liste.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si vous avez enregistré le `ShowDropdownBarOption` votre clé de Registre de service de langage, puis votre gestionnaire de fenêtres du code doit surveiller cet événement pour effectuer une synchronisation avec les préférences utilisateur concernant si la barre déroulante doit être affichée. Si vous n’inscrivez pas cette option dans votre clé de service de langage, l’option pour afficher ou masquer la barre déroulante est désactivée sur le **Options** menu.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Attacher une barre déroulante à une fenêtre de code  
 Pour attacher une barre déroulante à la fenêtre de code lorsqu’il est créé, un service de langage doit être attaché à la liste déroulante barre lorsque le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode est appelée. Si un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> (méthode) indique qu’une barre déroulante ne pas déjà existe, puis appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Pour accéder à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> l’interface, appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> pointeur retourné pour vous lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implémentation a été attachée.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnaliser les fenêtres de code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Prise en charge de la barre de Navigation dans un service de langage hérité](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)