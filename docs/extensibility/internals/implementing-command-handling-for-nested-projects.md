---
title: Implémentation de la gestion des commandes pour les projets imbriqués | Microsoft Docs
description: Découvrez comment implémenter la gestion des commandes pour les projets imbriqués dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4324e207d7b424295137f9523ed0bed538b3d806
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899984"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implémentation de la gestion des commandes pour les projets imbriqués
L’IDE peut passer des commandes qui sont transmises via les <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaces et aux projets imbriqués, ou les projets parents peuvent filtrer ou substituer les commandes.

> [!NOTE]
> Seules les commandes gérées normalement par le projet parent peuvent être filtrées. Les commandes telles que **générer** et **déployer** qui sont gérées par l’IDE ne peuvent pas être filtrées.

 Les étapes suivantes décrivent le processus d’implémentation de la gestion des commandes.

## <a name="procedures"></a>Procédures

#### <a name="to-implement-command-handling"></a>Pour implémenter la gestion des commandes

1. Lorsque l’utilisateur sélectionne un projet imbriqué ou un nœud dans un projet imbriqué :

   1. L’IDE appelle la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode.

      — ou —

   2. Si la commande provient d’une fenêtre de hiérarchie, telle qu’une commande de menu contextuel dans Explorateur de solutions, l’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> méthode sur le parent du projet.

2. Le projet parent peut examiner les paramètres à passer à `QueryStatus` , tels que `pguidCmdGroup` et `prgCmds` , pour déterminer si le projet parent doit filtrer les commandes. Si le projet parent est implémenté pour filtrer les commandes, il doit définir :

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Le projet parent doit alors retourner `S_OK` .

    Si le projet parent ne filtre pas la commande, il doit simplement retourner `S_OK` . Dans ce cas, l’IDE achemine automatiquement la commande vers le projet enfant.

    Le projet parent n’a pas besoin d’acheminer la commande vers le projet enfant. L’IDE effectue cette tâche..

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
