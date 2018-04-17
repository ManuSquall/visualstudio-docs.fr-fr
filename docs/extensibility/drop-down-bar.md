---
title: Barre déroulante | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cf01e8a416407c570076812bf18aa6b21c21583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="drop-down-bar"></a>Barre déroulante
La barre déroulante est fournie en haut de la fenêtre de code et contient deux listes déroulantes.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de la barre déroulante  
 Dans [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], par exemple, la barre de la liste déroulante contient les listes de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] éléments et [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] les fonctions membres des éléments, comme indiqué dans l’image suivante.  
  
 ![DROP&#45;bas barres](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barre déroulante  
  
 Lorsque vous implémentez une barre de liste déroulante, il existe quatre interfaces de première importance :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implémentez cette interface pour insérer le contenu de la barre de menu déroulant. Chaque combinaison de liste déroulante peut contenir du texte brut ou texte fantaisiste (gras, souligné ou italique), peut avoir coloration de la police de texte fenêtre ou de couleurs de police grisé et peut éventuellement fournir une petite image bitmap en regard de l’élément de liste déroulante. Similaire à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface, les images bitmap sont fournies dans les listes d’images. Chaque combinaison de liste déroulante peut avoir une liste d’images différents ; Toutefois, chaque liste d’images doit contenir des images de la même hauteur. En outre, à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> (méthode), vous pouvez fournir une info-bulle pour chaque combinaison.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Appelez cette interface pour créer ou détruire la barre déroulante pour une fenêtre de code. Cette interface peut également être utilisée pour déterminer si une barre de liste déroulante est déjà attachée à une fenêtre de code en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> (méthode). Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Appelez cette interface pour communiquer directement avec la barre de menu déroulant. Vous pouvez utiliser cette interface pour forcer une actualisation de la liste déroulante de la barre contenu ou pour modifier la sélection de l’une des zones de liste.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si vous avez enregistré le `ShowDropdownBarOption` votre clé de Registre de service de langage, puis votre gestionnaire de fenêtrage code doit surveiller cet événement pour effectuer une synchronisation avec les préférences de l’utilisateur concernant indique si la barre de menu déroulant doit être affichée. Si vous n’inscrivez pas cette option dans votre clé de service de langage, alors que l’option pour afficher ou masquer la barre déroulante est désactivée sur le **Options** menu.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Attachement d’une barre de menu déroulant à une fenêtre de Code  
 Pour attacher une barre de liste déroulante dans la fenêtre de code lors de sa création, un service de langage doit être attaché à la liste déroulante barre lorsque la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode est appelée. Si un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> méthode indique qu’une barre de menu déroulant n’existe pas déjà, puis appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Pour accéder à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> l’interface, appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> à partir de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> pointeur retourné lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implémentation a été joint.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Prise en charge de la barre de navigation dans un service de langage hérité](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)