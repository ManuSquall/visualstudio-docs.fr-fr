---
title: "Barre d&#233;roulante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hérité de Visual Studio SDK, éditeurs - liste déroulante de la barre"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Barre d&#233;roulante
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

la barre déroulante est fournie en haut de la fenêtre de code et contient deux listes déroulantes.  
  
## interfaces déroulantes de barre  
 Dans [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)], par exemple, la barre déroulante contient des listes pour les fonctions membres d'éléments de [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] et d'éléments de [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] , comme indiqué dans l'image suivante.  
  
 ![Barres déroulantes](~/extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
barre déroulante  
  
 En implémentant une barre déroulante, il existe quatre interfaces d'importance primaire :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     implémentez cette interface pour insérer le contenu de la barre déroulante.  Chaque combinaison déroulante peut contenir du texte brut ou le texte de fantaisie \(gras, soulignement, ou en italique\), peut avoir la couleur de la police de texte de la fenêtre ou grisée la couleur de la police, et peut éventuellement fournir une petite bitmap en regard de l'élément déroulant.  semblable à l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> , images bitmap sont fournis dans les listes d'images.  chaque combinaison déroulante peut avoir une liste d'images différente ; toutefois, chaque liste d'images doit contenir des images de la même hauteur.  En outre, à l'aide de la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> , vous pouvez fournir une info\-bulle pour chaque combinaison.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Appelez cette interface à créer ou destroy la barre déroulante pour une fenêtre de code.  Cette interface peut également être utilisée pour déterminer si une barre déroulante est déjà attachée à une fenêtre de code en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> .  appel <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     appelez cette interface pour communiquer directement avec la barre déroulante.  Vous pouvez utiliser cette interface pour forcer l'actualisation du contenu déroulant de barre ou pour modifier la sélection dans l'une des zones de liste.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si vous avez enregistré `ShowDropdownBarOption` dans votre clé de Registre de service de langage, votre gestionnaire de fenêtre de code doit surveiller cet événement pour synchroniser avec les préférences de l'utilisateur sur si la barre déroulante doit s'afficher.  Si vous n'enregistrez pas cette option dans votre clé de service de langage, l'option pour afficher ou masquer la barre déroulante est désactivée dans le menu d' **Options** .  
  
## Attacher une barre déroulante à une fenêtre de code  
 Pour attacher une barre déroulante dans la fenêtre de code lorsqu'elle est créée, un service de langage doit se joindre à la barre déroulante lorsque la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> est appelée.  Si un appel à la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> indique qu'une barre déroulante n'existe pas déjà, puis appelez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>.  Pour accéder à l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> , l'appel <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> du pointeur d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> retournées à vous lorsque votre implémentation d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> a été jointe.  
  
## Voir aussi  
 [Personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Prise en charge de la barre de Navigation dans un Service de langage hérité](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)