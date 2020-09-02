---
title: Barre déroulante | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204651"
---
# <a name="drop-down-bar"></a>Barre déroulante
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La barre déroulante est fournie en haut de la fenêtre de code et contient deux listes déroulantes.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de la barre déroulante  
 Dans [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , par exemple, la barre déroulante contient des listes pour les [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] fonctions membres Items et [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Items, comme illustré dans l’image suivante.  
  
 ![Déplacer les barres vers le&#45;](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Barre de liste déroulante  
  
 Lors de l’implémentation d’une barre déroulante, il existe quatre interfaces d’importance principale :  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implémentez cette interface pour insérer le contenu de la barre déroulante. Chaque combinaison de liste déroulante peut contenir du texte brut ou du texte fantaisie (gras, souligné ou italique), peut avoir des couleurs de police du texte de la fenêtre ou des couleurs grisées, et peut éventuellement fournir une petite bitmap en regard de l’élément de liste déroulante. À l’instar de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface, les images bitmap sont fournies dans les listes d’images. Chaque combinaison de liste déroulante peut avoir une liste d’images différente ; Toutefois, chaque liste d’images doit contenir des images de la même hauteur. En outre, à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> méthode, vous pouvez fournir une info-bulle pour chaque combinaison.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Appelez cette interface pour créer ou détruire la barre déroulante pour une fenêtre de code. Cette interface peut également être utilisée pour déterminer si une barre déroulante est déjà attachée à une fenêtre de code en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> méthode. Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> à partir de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Appelez cette interface pour communiquer directement avec la barre déroulante. Vous pouvez utiliser cette interface pour forcer une actualisation du contenu de la barre déroulante ou pour modifier la sélection dans l’une des zones de liste.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si vous avez inscrit `ShowDropdownBarOption` dans la clé de registre de votre service de langage, le gestionnaire de la fenêtre de code doit surveiller cet événement pour qu’il se synchronise avec les préférences de l’utilisateur en ce qui concerne l’affichage de la barre déroulante. Si vous n’inscrivez pas cette option dans votre clé de service de langage, l’option d’affichage ou de masquage de la barre déroulante est désactivée dans le menu **options** .  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Attachement d’une barre déroulante à une fenêtre de code  
 Pour attacher une barre déroulante à la fenêtre de code lors de sa création, un service de langage doit s’attacher à la barre déroulante lorsque la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode est appelée. Si un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> méthode indique qu’une barre déroulante n’existe pas encore, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Pour accéder à l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interface, appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> à partir du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> pointeur qui vous a été retourné lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implémentation a été attachée.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des fenêtres de code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Prise en charge de la barre de navigation dans un service de langage hérité](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
