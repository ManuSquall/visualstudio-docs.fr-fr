---
title: Informations sur les paramètres dans un service de langue héritée1 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706798"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informations sur les paramètres dans un service de langage hérité
L’outil IntelliSense Parameter Info fournit aux utilisateurs des conseils sur l’endroit où ils se trouvent dans une construction linguistique.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Extending the Editor and Language Services](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="how-parameter-info-tooltips-work"></a>Fonctionnement des outils d’information sur les paramètres
 Lorsque vous tapez une déclaration dans l’éditeur, le VSPackage affiche une petite fenêtre de pointe contenant la définition de la déclaration étant tapée. Par exemple, si vous tapez une déclaration Microsoft `pMainFrame ->UpdateWindow`Foundation Classes (MFC) (comme ) et appuyez sur la clé `UpdateWindow` de parenthèse d’ouverture pour commencer à énumérer les paramètres, une astuce de méthode apparaît affichant la définition de la méthode.

 Les outils d’information sur les paramètres sont généralement utilisés en conjonction avec l’achèvement de l’instruction. Ils sont plus utiles pour les langues qui ont des paramètres ou d’autres informations formatées après le nom de la méthode ou mot clé.

 Les outils d’information paramétrifé sont initiés par le service linguistique par l’interception de commande. Pour intercepter les caractères de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l’utilisateur, votre objet de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> service linguistique doit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> implémenter l’interface et passer la vue de texte d’un pointeur à votre implémentation, en appelant la méthode dans l’interface. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Le filtre de commande intercepte les commandes que vous tapez dans la fenêtre de code. Surveillez les informations de commande pour savoir quand afficher les informations de paramètres à l’utilisateur. Vous pouvez utiliser le même filtre de commande pour l’achèvement de l’instruction, les marqueurs d’erreur, et ainsi de suite.

 Lorsque vous tapez un mot clé pour lequel le service <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> linguistique peut <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> fournir des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> conseils, alors le service linguistique crée un objet et appelle la méthode dans l’interface pour aviser l’IDE pour afficher un indice. Créez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> l’objet en utilisant `VSLocalCreateInstance` `CLSID_VsMethodTipWindow`et en spécifiant la coclasse . `VsLocalCreateInstance`est une fonction définie dans le fichier `QueryService` d’en-tête `CreateInstance` vsdoc.h `CLSID_VsMethodTipWindow`qui appelle le registre local et appelle sur cet objet pour le .

## <a name="providing-a-method-tip"></a>Fournir un conseil de méthode
 Pour fournir un conseil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> de méthode, appelez la méthode dans l’interface, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> en la transmettant votre implémentation de l’interface. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>

 Lorsque <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> votre classe est invoquée, ses méthodes sont appelées dans l’ordre suivant :

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Retourne la position et la longueur des données pertinentes dans le tampon texte actuel. Cela permet à l’IDE de ne pas masquer ces données avec la fenêtre de pointe d’outils.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Retourne le numéro de méthode (index zéro) que vous souhaitez afficher au départ. Par exemple, si vous retournez zéro, la première méthode surchargée est initialement présentée.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Retourne le nombre de méthodes surchargées qui s’appliquent dans le contexte actuel. Si vous retournez une valeur supérieure à 1 pour cette méthode, alors la vue de texte s’affiche de haut en bas des flèches pour vous. Si vous cliquez sur la flèche <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> vers le bas, l’IDE appelle la méthode. Si vous cliquez sur la flèche <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> vers le haut, l’IDE appelle la méthode.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Le texte de l’outil d’info paramètre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> est construit lors de plusieurs appels et méthodes.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Retourne le nombre de paramètres à afficher dans la méthode.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Si vous retournez un numéro de méthode correspondant à la surcharge que vous <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> souhaitez afficher, cette méthode est appelée, suivie d’un appel à la méthode.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informe votre service linguistique de mettre à jour l’éditeur lorsqu’un pourboire de méthode est affiché. Dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> la méthode, appelez ce qui suit :

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Vous recevez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> appel à la méthode lorsque vous fermez la fenêtre de pointe de méthode.
