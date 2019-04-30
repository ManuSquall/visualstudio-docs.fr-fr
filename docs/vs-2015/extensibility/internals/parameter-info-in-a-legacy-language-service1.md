---
title: Informations sur les paramètres dans un langage hérité1 | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b1707313c40e7ea720fff3b9f70546af00ea486
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408657"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informations sur les paramètres dans un Service de langage hérité
L’info-bulle d’informations sur les paramètres IntelliSense fournit aux utilisateurs des indications sur l’endroit où elles se trouvent dans une construction de langage.

 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="how-parameter-info-tooltips-work"></a>Fonctionnement des info-bulles des informations de paramètre
 Lorsque vous tapez une instruction dans l’éditeur, le package Visual Studio affiche une fenêtre de petite info-bulle contenant la définition de l’instruction tapée. Par exemple, si vous tapez une instruction de Microsoft Foundation Classes (MFC) (tel que `pMainFrame ->UpdateWindow`) et appuyez sur la parenthèse ouvrante touche pour commencer à répertorier les paramètres, une info-bulle de méthode s’affiche pour confirmer la définition de la `UpdateWindow` (méthode).

 Info-bulles des informations de paramètre sont généralement utilisés conjointement avec la saisie semi-automatique des instructions. Ils sont particulièrement utiles pour les langages qui ont des paramètres ou autres informations de mise en forme après le mot clé ou le nom de la méthode.

 Les info-bulles d’informations sur les paramètres sont initiées par le service de langage via l’interception des commandes. Pour intercepter des caractères de l’utilisateur, votre objet de service de langage doit implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface et passer à l’affichage de texte un pointeur vers votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implémentation, en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Le filtre de commande intercepte des commandes que vous tapez dans la fenêtre de code. Surveiller les informations de commande pour savoir quand afficher des informations sur les paramètres à l’utilisateur. Vous pouvez utiliser le même filtre de commande pour la saisie semi-automatique des instructions, les marqueurs d’erreur et ainsi de suite.

 Lorsque vous tapez un mot clé pour lequel le service de langage peut fournir des indications, le service de langage crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objet et appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface pour notifier l’IDE pour afficher un indicateur. Créer le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> à l’aide de l’objet `VSLocalCreateInstance` et en spécifiant la coclasse `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` est une fonction définie dans le vsdoc.h de fichier d’en-tête qui appelle `QueryService` pour le Registre local et les appels `CreateInstance` sur cet objet pour le `CLSID_VsMethodTipWindow`.

## <a name="providing-a-method-tip"></a>En fournissant une info-bulle de méthode
 Pour fournir une info-bulle de méthode, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interface, en lui passant votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface.

 Lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> de classe est appelée, ses méthodes sont appelées dans l’ordre suivant :

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Retourne la position et la longueur des données pertinentes dans le tampon de texte actuel. Cela indique à l’IDE pour ne masquent pas les données à l’aide de la fenêtre d’info-bulle.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Retourne le numéro de méthode (index de base zéro) que vous souhaitez afficher initialement. Par exemple, si vous retournez zéro, la première méthode surchargée est affichée initialement.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Retourne le nombre de méthodes surchargées qui sont applicables dans le contexte actuel. Si vous retournez une valeur supérieure à 1 pour cette méthode, puis l’affichage de texte affiche des flèches haut et bas pour vous. Si vous cliquez sur la flèche vers le bas, l’IDE appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> (méthode). Si vous cliquez sur la flèche vers le haut, l’IDE appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> (méthode).

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Le texte de l’info-bulle d’informations sur les paramètres a été construit pendant plusieurs appels à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> méthodes.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Retourne le nombre de paramètres à afficher dans la méthode.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Si vous retournez un numéro de la méthode correspondant à la surcharge que vous souhaitez afficher, cette méthode est appelée, suivie d’un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> (méthode).

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Indique à votre service de langage pour mettre à jour de l’éditeur quand une info-bulle de méthode s’affiche. Dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> (méthode), exécutez la commande suivante :

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Vous recevez un appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode lorsque vous fermez la fenêtre d’info-bulle de méthode.