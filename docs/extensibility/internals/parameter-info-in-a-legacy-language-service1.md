---
title: Informations sur les paramètres dans un Service1 de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informations sur les paramètres dans un Service de langage hérité
L’info-bulle d’informations sur les paramètres IntelliSense fournit aux utilisateurs des indications sur où ils se trouvent dans une construction de langage.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [étendre l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="how-parameter-info-tooltips-work"></a>Fonctionnement des info-bulles des informations de paramètre  
 Lorsque vous tapez une instruction dans l’éditeur, le VSPackage affiche une fenêtre d’info-bulle petit contenant la définition de l’instruction en cours d’entrée. Par exemple, si vous tapez une instruction Microsoft Foundation Classes (MFC) (tel que `pMainFrame ->UpdateWindow`) et appuyez sur la parenthèse ouvrante touche pour commencer à répertorier les paramètres, une info-bulle de la méthode affiche la définition de la `UpdateWindow` (méthode).  
  
 Info-bulles des informations de paramètre sont généralement utilisées en conjonction avec la saisie semi-automatique des instructions. Ils sont particulièrement utiles pour les langues qui ont des paramètres ou autres informations de mise en forme après le mot clé ou le nom de la méthode.  
  
 Les info-bulles d’informations sur les paramètres sont initiées par le service de langage via l’interception de commande. Pour intercepter des caractères de l’utilisateur, votre objet de service de langage doit implémenter la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface et passer à l’affichage de texte un pointeur vers votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation, en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Le filtre de commande intercepte les commandes que vous tapez dans la fenêtre de code. Surveillez les informations de commande pour le moment afficher des informations sur les paramètres à l’utilisateur. Vous pouvez utiliser le même filtre de commande pour la saisie semi-automatique des instructions, les marqueurs de l’erreur et ainsi de suite.  
  
 Lorsque vous tapez un mot clé pour laquelle le service de langage peut fournir des indications, le service de langage crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objet et appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface pour notifier l’IDE affiche un indicateur. Créer le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> à l’aide de l’objet `VSLocalCreateInstance` et en spécifiant la coclasse `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` est une fonction définie dans le vsdoc.h de fichier d’en-tête qui appelle `QueryService` pour le Registre local et les appels `CreateInstance` sur cet objet pour le `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>En fournissant une info-bulle (méthode)  
 Pour fournir une info-bulle de la méthode, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interface, en lui passant l’implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface.  
  
 Lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> de classe est appelée, ses méthodes sont appelées dans l’ordre suivant :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Retourne la position et la longueur des données pertinentes dans la mémoire tampon de texte en cours. Cela indique à l’IDE de ne pas altérer les données à l’aide de la fenêtre d’info-bulle.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Retourne le nombre (méthode) (index de base zéro) que vous souhaitez afficher initialement. Par exemple, si vous retournez zéro, la première méthode surchargée est affichée initialement.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Retourne le nombre de méthodes surchargées qui sont applicables dans le contexte actuel. Si vous retournez une valeur supérieure à 1 pour cette méthode, puis l’affichage de texte affiche des flèches haut et bas pour vous. Si vous cliquez sur la flèche vers le bas, l’IDE appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> (méthode). Si vous cliquez sur la flèche vers le haut, l’IDE appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> (méthode).  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Le texte de l’info-bulle d’informations sur les paramètres est construit pendant plusieurs appels à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> méthodes.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Retourne le nombre de paramètres à afficher dans la méthode.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Si vous retournez un nombre de méthode correspondant avec la surcharge que vous souhaitez afficher, cette méthode est appelée, suivie d’un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> (méthode).  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informe le service de langage pour mettre à jour de l’éditeur lorsqu’une info-bulle de la méthode est affichée. Dans la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> méthode, appelez les éléments suivants :  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Vous recevez un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode lorsque vous fermez la fenêtre d’info-bulle de méthode.