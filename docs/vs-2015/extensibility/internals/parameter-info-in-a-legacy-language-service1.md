---
title: Informations sur les paramètres dans un Service1 de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b1707313c40e7ea720fff3b9f70546af00ea486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839321"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informations sur les paramètres dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’info-bulle informations sur les paramètres IntelliSense fournit aux utilisateurs des conseils sur l’emplacement où ils se trouvent dans une construction de langage.  
  
 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [extension de l’éditeur et des services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="how-parameter-info-tooltips-work"></a>Fonctionnement des info-bulles des informations sur les paramètres  
 Quand vous tapez une instruction dans l’éditeur, le VSPackage affiche une petite fenêtre d’info-bulle contenant la définition de l’instruction en cours de saisie. Par exemple, si vous tapez une instruction Microsoft Foundation Classes (MFC) (telle que `pMainFrame ->UpdateWindow` ) et que vous appuyez sur la touche parenthèse ouvrante pour commencer à répertorier les paramètres, une info-bulle s’affiche pour afficher la définition de la `UpdateWindow` méthode.  
  
 Les info-bulles d’informations sur les paramètres sont généralement utilisées conjointement avec la saisie semi-automatique des instructions. Elles sont particulièrement utiles pour les langues qui ont des paramètres ou d’autres informations mises en forme après le nom de la méthode ou le mot clé.  
  
 Les info-bulles d’informations sur les paramètres sont initiées par le service de langage par le biais de l’interception de commande. Pour intercepter les caractères utilisateur, votre objet de service de langage doit implémenter l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface et passer la vue de texte d’un pointeur vers votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation, en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode dans l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Le filtre de commande intercepte les commandes que vous tapez dans la fenêtre de code. Surveillez les informations de commande pour savoir quand afficher des informations de paramètres à l’utilisateur. Vous pouvez utiliser le même filtre de commande pour la saisie semi-automatique des instructions, les marqueurs d’erreur, etc.  
  
 Quand vous tapez un mot clé pour lequel le service de langage peut fournir des indications, le service de langage crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objet et appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode dans l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface pour notifier l’IDE afin d’afficher un indicateur. Créez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objet à l’aide `VSLocalCreateInstance` de et en spécifiant la coclasse `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` est une fonction définie dans le fichier d’en-tête vsdoc. h qui appelle `QueryService` pour le registre local et appelle `CreateInstance` sur cet objet pour le `CLSID_VsMethodTipWindow` .  
  
## <a name="providing-a-method-tip"></a>Fourniture d’un Conseil de méthode  
 Pour fournir une info-bulle de méthode, appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode dans l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interface, en lui passant votre implémentation de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface.  
  
 Quand votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe est appelée, ses méthodes sont appelées dans l’ordre suivant :  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Retourne la position et la longueur des données pertinentes dans la mémoire tampon de texte actuelle. Cela indique à l’IDE de ne pas masquer ces données avec la fenêtre d’info-bulle.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Retourne le numéro de la méthode (index de base zéro) que vous souhaitez afficher initialement. Par exemple, si vous retournez zéro, la première méthode surchargée est initialement présentée.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Retourne le nombre de méthodes surchargées applicables dans le contexte actuel. Si vous retournez une valeur supérieure à 1 pour cette méthode, l’affichage de texte affiche des flèches vers le haut et vers le bas pour vous. Si vous cliquez sur la flèche vers le bas, l’IDE appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> méthode. Si vous cliquez sur la flèche vers le haut, l’IDE appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> méthode.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Le texte de l’info-bulle info sur les paramètres est construit lors de plusieurs appels aux <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> méthodes et.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Retourne le nombre de paramètres à afficher dans la méthode.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Si vous retournez un numéro de méthode correspondant à la surcharge que vous souhaitez afficher, cette méthode est appelée, suivie d’un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> méthode.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informe votre service de langage pour mettre à jour l’éditeur quand une info-bulle de méthode est affichée. Dans la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> méthode, appelez la commande suivante :  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Vous recevez un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode quand vous fermez la fenêtre d’info-bulle de la méthode.
