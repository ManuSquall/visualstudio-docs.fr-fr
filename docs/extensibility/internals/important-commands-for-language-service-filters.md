---
title: Commandes importantes pour les filtres du service de langage | Microsoft Docs
description: En savoir plus sur les commandes importantes que vous devez prendre en charge lors de la création d’un filtre de service de langage complet dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd5f65248411a7ea6b892d5b4c800718456339f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899054"
---
# <a name="important-commands-for-language-service-filters"></a>Commandes importantes pour les filtres du service de langage
Si vous souhaitez créer un filtre de service de langage complet, envisagez de gérer les commandes suivantes. La liste complète des identificateurs de commande est définie dans l' <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération pour le code managé et le fichier d’en-tête Stdidcmd. h pour le code non managé [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Le fichier Stdidcmd. h se trouve dans le *chemin d’installation du kit de développement logiciel (SDK) Visual Studio*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Commandes à gérer

> [!NOTE]
> Il n’est pas obligatoire de filtrer toutes les commandes du tableau suivant.

|Commande|Description|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur clique avec le bouton droit. Cette commande indique qu’il est temps de fournir un menu contextuel. Si vous ne gérez pas cette commande, l’éditeur de texte fournit un menu contextuel par défaut sans aucune commande spécifique au langage. Pour inclure vos propres commandes dans ce menu, gérez la commande et affichez un menu contextuel vous-même.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Généralement envoyé lorsque l’utilisateur tape CTRL + J. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour afficher la zone de saisie semi-automatique des instructions.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape un caractère. Surveillez cette commande pour déterminer quand un caractère de déclenchement est tapé et pour fournir la saisie semi-automatique des instructions, des conseils de méthode et des marqueurs de texte, tels que la coloration syntaxique, la correspondance des accolades et les marqueurs d’erreur. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour la saisie semi-automatique des instructions et la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> pour les conseils de méthode. Pour prendre en charge les marqueurs de texte, surveillez cette commande pour déterminer si le caractère en cours de saisie requiert la mise à jour de vos marqueurs.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche entrée. Surveillez cette commande pour déterminer quand ignorer une fenêtre d’info-bulle de méthode en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Par défaut, l’affichage de texte gère cette commande.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche Retour arrière. Analyse pour déterminer quand ignorer une fenêtre d’info-bulle de méthode en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Par défaut, l’affichage de texte gère cette commande.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu ou d’une touche de raccourci. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour mettre à jour la fenêtre d’info-bulle avec les informations sur les paramètres.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur pointe sur une variable ou positionne le curseur sur une variable et sélectionne **Info Express** dans **IntelliSense** dans le menu **Edition** . Retournez le type de la variable dans une info-bulle en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Si le débogage est actif, l’info-bulle doit également indiquer la valeur de la variable.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Généralement envoyé lorsque l’utilisateur tape CTRL + barre d’espace. Cette commande indique au service de langage d’appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu, généralement **commenter la sélection** ou supprimer les **marques de commentaire** de la sélection **avancée** dans le menu **Edition** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indique que l’utilisateur souhaite commenter le texte sélectionné ; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indique que l’utilisateur souhaite supprimer les marques de commentaire du texte sélectionné. Ces commandes peuvent être implémentées uniquement par le service de langage.|

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
