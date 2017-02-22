---
title: "Informations sur les param&#232;tres dans un Service1 de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage, les conseils (méthode)"
  - "conseils de méthode"
  - "services de langage, paramètre info-bulle"
  - "Interface de IVsMethodData"
  - "Informations sur les paramètres (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Informations sur les param&#232;tres dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L’info\-bulle d’informations sur les paramètres IntelliSense fournit aux utilisateurs des conseils sur où elles se trouvent dans une construction de langage.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [Extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## Fonctionnement des info\-bulles Info de paramètre  
 Lorsque vous entrez une instruction dans l’éditeur, le VSPackage affiche une fenêtre de petite info\-bulle contenant la définition de l’instruction en cours d’entrée. Par exemple, si vous entrez une instruction de Microsoft Foundation Classes \(MFC\) \(tels que `pMainFrame ->UpdateWindow`\) et appuyez sur la clé de la parenthèse ouvrante pour commencer à répertorier les paramètres, une info\-bulle de la méthode affiche la définition de la `UpdateWindow` méthode.  
  
 Info\-bulles des informations de paramètre sont généralement utilisées en conjonction avec la saisie semi\-automatique des instructions. Elles sont plus utiles pour les langages qui ont des paramètres ou autres informations de mise en forme après le mot clé ou le nom de la méthode.  
  
 Les info\-bulles d’informations sur les paramètres sont initiées par le service de langage via l’interception de commande. Pour intercepter des caractères de l’utilisateur, votre objet de service de langage doit implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface et passer à l’affichage de texte un pointeur vers votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation, en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Le filtre de commande intercepte les commandes que vous tapez dans la fenêtre de code. Surveiller les informations de commande pour savoir quand afficher des informations sur les paramètres à l’utilisateur. Vous pouvez utiliser le même filtre de commande pour la saisie semi\-automatique des instructions, marqueurs d’erreur et ainsi de suite.  
  
 Lorsque vous tapez un mot clé pour laquelle le service de langage peut fournir des indications, le service de langage crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objet et appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface pour notifier l’IDE affiche un indicateur. Créer le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> à l’aide de l’objet `VSLocalCreateInstance` et en spécifiant la coclasse `CLSID_VsMethodTipWindow`.`VsLocalCreateInstance` est une fonction définie dans le vsdoc.h de fichier d’en\-tête qui appelle `QueryService` pour le Registre local et appelle `CreateInstance` sur cet objet pour le `CLSID_VsMethodTipWindow`.  
  
## En fournissant une info\-bulle \(méthode\)  
 Pour fournir une info\-bulle de la méthode, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interface, en lui transmettant votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface.  
  
 Lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> de classe est appelée, les méthodes sont appelées dans l’ordre suivant :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Retourne la position et la longueur des données pertinentes dans le tampon de texte actuel. Ce code indique à l’IDE ne pas altérer les données à l’aide de la fenêtre d’info\-bulle.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Retourne le nombre \(méthode\) \(index de base zéro\) que vous souhaitez afficher initialement. Par exemple, si vous retournez zéro, la première méthode surchargée est affichée initialement.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Retourne le nombre de méthodes surchargées qui sont applicables dans le contexte actuel. Si vous retournez une valeur supérieure à 1 pour cette méthode, puis l’affichage de texte affiche des flèches haut et bas pour vous. Si vous cliquez sur la flèche vers le bas, l’IDE appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> méthode. Si vous cliquez sur la flèche vers le haut, l’IDE appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> méthode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Le texte de l’info\-bulle d’informations sur les paramètres est construit pendant plusieurs appels à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> méthodes.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Retourne le nombre de paramètres à afficher dans la méthode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Si vous retournez un nombre de méthode correspondant à la surcharge que vous souhaitez afficher, cette méthode est appelée, suivie d’un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> \(méthode\).  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informe le service de langage pour mettre à jour de l’éditeur lorsqu’une info\-bulle de la méthode s’affiche. Dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> \(méthode\), exécutez la commande suivante :  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Vous recevez un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode lorsque vous fermez la fenêtre d’info\-bulle de méthode.