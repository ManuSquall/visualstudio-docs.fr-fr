---
title: Affichage des fichiers à l’aide de la commande ouvrir un fichier | Microsoft Docs
description: Découvrez comment l’environnement de développement intégré (IDE) de Visual Studio gère la commande ouvrir un fichier dans le menu fichier pour afficher les fichiers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96f92aa921c7bb78511ed685d846e288518258fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946824"
---
# <a name="display-files-by-using-the-open-file-command"></a>Afficher les fichiers à l’aide de la commande ouvrir un fichier
Les étapes suivantes décrivent comment l’IDE gère la commande **ouvrir un fichier** , qui est disponible dans le menu **fichier** de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Les étapes décrivent également comment les projets doivent répondre aux appels qui proviennent de cette commande.

 Quand un utilisateur clique sur la commande **ouvrir un fichier** dans le menu **fichier** et sélectionne un fichier dans la boîte de dialogue **ouvrir un fichier** , le processus suivant se produit :

1. À l’aide de la table de document en cours d’exécution, l’IDE détermine si le fichier est déjà ouvert dans un projet.

    - Si le fichier est ouvert, l’IDE réaffiche la fenêtre.

    - Si le fichier n’est pas ouvert, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> pour interroger chaque projet afin de déterminer quel projet peut ouvrir le fichier.

        > [!NOTE]
        > Dans l’implémentation de votre projet de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> , fournissez une valeur de priorité qui indique le niveau auquel votre projet ouvre le fichier. Les valeurs de priorité sont fournies dans l' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération.

2. Chaque projet répond avec un niveau de priorité qui indique l’importance qu’il place dans le projet pour ouvrir le fichier.

3. L’IDE utilise les critères suivants pour déterminer quel projet ouvre le fichier :

    - Le projet qui répond avec la priorité la plus élevée ( `DP_Intrinsic` ) ouvre le fichier. Si plusieurs projets répondent avec cette priorité, le premier projet à répondre ouvre le fichier.

    - Si aucun projet ne répond avec la priorité la plus élevée ( `DP_Intrinsic` ), mais que tous les projets répondent avec la même priorité, le projet actif ouvre le fichier. Si aucun projet n’est actif, le premier projet à répondre ouvre le fichier.

    - Si aucun projet ne réclame la propriété du fichier ( `DP_Unsupported` ), le projet fichiers divers ouvre le fichier.

         Si une instance du projet fichiers divers est créée, le projet répond toujours avec la valeur `DP_CanAddAsExternal` . Cette valeur indique que le projet peut ouvrir le fichier. Ce projet est utilisé pour héberger des fichiers ouverts qui ne se trouvent dans aucun autre projet. La liste des éléments de ce projet n’est pas persistante. ce projet est visible dans **Explorateur de solutions** uniquement lorsqu’il est utilisé pour ouvrir un fichier.

         Si le projet fichiers divers n’indique pas qu’il peut ouvrir le fichier, une instance du projet n’a pas été créée. Dans ce cas, l’IDE crée une instance du projet fichiers divers et indique au projet d’ouvrir le fichier.

4. Dès que l’IDE détermine quel projet ouvre le fichier, il appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode sur ce projet.

5. Le projet a ensuite la possibilité d’ouvrir le fichier à l’aide d’un éditeur spécifique à un projet ou d’un éditeur standard. Pour plus d’informations, consultez [Comment : ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md) et [Comment : ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md), respectivement.

## <a name="see-also"></a>Voir aussi
- [Afficher les fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Comment : ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)
- [Procédure : ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
