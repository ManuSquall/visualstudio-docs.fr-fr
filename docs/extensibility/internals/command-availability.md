---
title: Disponibilité de commande (en anglais) Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709699"
---
# <a name="command-availability"></a>Disponibilité de commande

Le contexte Visual Studio détermine quelles commandes sont disponibles. Le contexte peut changer en fonction du projet actuel, de l’éditeur actuel, des VSPackages chargés et d’autres aspects de l’environnement de développement intégré (IDE).

## <a name="command-contexts"></a>Contextes de commandement

Les contextes de commande suivants sont les plus courants :

- IDE : Les commandes fournies par l’IDE sont toujours disponibles.

- VSPackage : VSPackages peut définir lorsque les commandes doivent être affichées ou cachées.

- Projet : Les commandes du projet n’apparaissent que pour le projet actuellement sélectionné.

- Rédacteur en chef : Un seul éditeur peut être actif à la fois. Les commandes de l’éditeur actif sont disponibles. Un éditeur travaille en étroite collaboration avec un service linguistique. Le service linguistique doit traiter ses commandes dans le contexte de l’éditeur associé.

- Type de fichier : Un éditeur peut charger plus d’un type de fichier. Les commandes disponibles peuvent changer en fonction du type de fichier.

- Fenêtre active : La dernière fenêtre de document active définit le contexte de l’interface utilisateur (interface utilisateur) pour les liaisons clés. Cependant, une fenêtre d’outil qui dispose d’une table de liaison des touches qui ressemble au navigateur Web interne pourrait également définir le contexte de l’interface utilisateur. Pour les fenêtres de documents multi-tabbed telles que l’éditeur HTML, chaque onglet a un contexte de commande différent GUID. Une fois qu’une fenêtre d’outil est enregistrée, elle est toujours disponible sur le menu **View.**

- Contexte de l’interface utilisateur : Les contextes d’assurance-chômage sont identifiés par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> lorsque la solution est en cours de construction, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> lorsque le débbuggeur est actif. Plusieurs contextes d’interface utilisateur peuvent être actifs en même temps.

## <a name="define-custom-context-guids"></a>Décrivez les GUIDs de contexte personnalisé

Si un cadre de commande approprié GUID n’est pas déjà défini, vous pouvez en définir un dans votre VSPackage, puis le programmer pour être actif ou inactif au besoin pour contrôler la visibilité de vos commandes :

1. Enregistrez les GUIDs <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> contextuelles en appelant la méthode.

2. Obtenez l’état d’un contexte <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> GUID en appelant la méthode.

3. Activez et éteignez les <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> GUIDs contextuelles en appelant la méthode.

> [!CAUTION]
> Assurez-vous que votre VSPackage n’affecte aucun contexte existant GUIDs parce que d’autres VSPackages peuvent en dépendre.

## <a name="see-also"></a>Voir aussi

- [Objets contextuelles de sélection](../../extensibility/internals/selection-context-objects.md)
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
