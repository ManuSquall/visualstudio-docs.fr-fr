---
title: Disponibilité des commandes | Microsoft Docs
description: Découvrez comment le contexte de commande, qui change en fonction du projet actuel, de l’éditeur actuel et d’autres facteurs, détermine les commandes qui sont disponibles dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ad456c6c946964f3038a712274003bae5732fa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932734"
---
# <a name="command-availability"></a>Disponibilité des commandes

Le contexte de Visual Studio détermine les commandes qui sont disponibles. Le contexte peut changer en fonction du projet actuel, de l’éditeur actuel, des VSPackages chargés et d’autres aspects de l’environnement de développement intégré (IDE).

## <a name="command-contexts"></a>Contextes de commande

Les contextes de commande suivants sont les plus courants :

- IDE : les commandes fournies par l’IDE sont toujours disponibles.

- VSPackage : les VSPackages peuvent définir le moment où les commandes doivent être affichées ou masquées.

- Projet : les commandes de projet s’affichent uniquement pour le projet actuellement sélectionné.

- Éditeur : un seul éditeur peut être actif à la fois. Les commandes de l’éditeur actif sont disponibles. Un éditeur travaille en étroite collaboration avec un service de langage. Le service de langage doit traiter ses commandes dans le contexte de l’éditeur associé.

- Type de fichier : un éditeur peut charger plusieurs types de fichiers. Les commandes disponibles peuvent changer en fonction du type de fichier.

- Fenêtre active : la dernière fenêtre de document active définit le contexte de l’interface utilisateur (IU) pour les combinaisons de touches. Toutefois, une fenêtre outil qui a une table de liaison de clés qui ressemble au navigateur Web interne peut également définir le contexte de l’interface utilisateur. Pour les fenêtres de document à plusieurs onglets telles que l’éditeur HTML, chaque onglet possède un GUID de contexte de commande différent. Une fois qu’une fenêtre outil est inscrite, elle est toujours disponible dans le menu **affichage** .

- Contexte de l’interface utilisateur : les contextes d’interface utilisateur sont identifiés par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> lorsque la solution est en cours de génération, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> lorsque le débogueur est actif. Plusieurs contextes d’interface utilisateur peuvent être actifs en même temps.

## <a name="define-custom-context-guids"></a>Définir des GUID de contexte personnalisés

Si aucun GUID de contexte de commande approprié n’est déjà défini, vous pouvez en définir un dans votre VSPackage, puis le programmer pour qu’il soit actif ou inactif en fonction des besoins afin de contrôler la visibilité de vos commandes :

1. Enregistrez les GUID de contexte en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode.

2. Obtenir l’état d’un GUID de contexte en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode.

3. Activez et désactivez les GUID de contexte en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> méthode.

> [!CAUTION]
> Assurez-vous que votre VSPackage n’affecte pas les GUID de contexte existants, car d’autres VSPackages peuvent en dépendre.

## <a name="see-also"></a>Voir aussi

- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
