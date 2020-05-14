---
title: Commandes importantes pour les filtres de service linguistique (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707610"
---
# <a name="important-commands-for-language-service-filters"></a>Commandes importantes pour les filtres du service de langage
Si vous souhaitez créer un filtre de service linguistique entièrement en vedette, envisagez de manipuler les commandes suivantes. La liste complète des identifiants <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> de commande est définie dans le recensement du code géré et [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] du fichier d’en-tête Stdidcmd.h pour le code non géré. Vous pouvez trouver le fichier Stdidcmd.h dans *visual Studio SDK chemin d’installation*'VisualStudioIntegration’Common’Inc.

## <a name="commands-to-handle"></a>Commandes à manipuler

> [!NOTE]
> Il n’est pas obligatoire de filtrer pour chaque commande dans le tableau suivant.

|Commande|Description|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur clics à droite. Cette commande indique qu’il est temps de fournir un menu raccourci. Si vous ne gérez pas cette commande, l’éditeur de texte fournit un menu de raccourci par défaut sans aucune commande spécifique à la langue. Pour inclure vos propres commandes sur ce menu, gérez la commande et affichez vous-même un menu raccourci.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Généralement envoyé lorsque l’utilisateur tape CTRL-J. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sur le pour afficher la boîte d’achèvement de déclaration.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape un personnage. Surveillez cette commande pour déterminer quand un caractère déclencheur est tapé et pour fournir l’achèvement de l’instruction, des conseils de méthode et des marqueurs de texte, tels que la coloration syntaxe, l’appariement des accolades et les marqueurs d’erreur. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sur l’achèvement de l’instruction et la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode sur les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> conseils de méthode. Pour prendre en charge les marqueurs texte, surveillez cette commande pour déterminer si le personnage tapé nécessite que vous mettez à jour vos marqueurs.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la clé Enter. Surveillez cette commande pour déterminer quand rejeter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> une fenêtre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>de pointe de méthode en appelant la méthode sur le . Par défaut, la vue de texte gère cette commande.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche Backspace. Surveiller pour déterminer quand rejeter une fenêtre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>pointe de méthode en appelant la méthode sur le . Par défaut, la vue de texte gère cette commande.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu ou d’une clé de raccourci. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sur la mise à jour de la fenêtre de pointe avec les informations de paramètres.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur plane sur une variable ou positionne le curseur sur une variable et sélectionne **des informations rapides** d’IntelliSense dans le menu **Edit.** **IntelliSense** Retourner le type de la variable <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> dans un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>pourboire en appelant la méthode sur le . Si le débogage est actif, la pointe doit également montrer la valeur de la variable.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Généralement envoyé lorsque l’utilisateur tape CTRL-SPACEBAR. Cette commande indique au service <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> linguistique <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>d’appeler la méthode sur le .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu, généralement **Comment Selection** ou **Uncomment Selection** de **Advanced** dans le menu **Edit.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indique que l’utilisateur veut commenter le texte sélectionné; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indique que l’utilisateur veut désengagementer le texte sélectionné. Ces commandes ne peuvent être mises en œuvre que par le service linguistique.|

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
