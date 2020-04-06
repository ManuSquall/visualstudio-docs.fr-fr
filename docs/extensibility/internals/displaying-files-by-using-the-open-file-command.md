---
title: Affichage des fichiers à l’aide de la commande de fichiers ouverts ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708595"
---
# <a name="display-files-by-using-the-open-file-command"></a>Afficher les fichiers en utilisant la commande Open File
Les étapes suivantes décrivent comment l’IDE gère la commande Open [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **File,** qui est disponible sur le menu **Fichier** en . Les étapes décrivent également comment les projets devraient répondre aux appels qui proviennent de cette commande.

 Lorsqu’un utilisateur clique sur la commande **Open File** sur le menu **Du fichier** et sélectionne un fichier à partir de la boîte de dialogue **Open File,** le processus suivant se produit :

1. À l’aide de la table de document en cours d’exécution, l’IDE détermine si le fichier est déjà ouvert dans un projet.

    - Si le fichier est ouvert, l’IDE refait surface sur la fenêtre.

    - Si le fichier n’est pas <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ouvert, l’IDE appelle à interroger chaque projet afin de déterminer quel projet peut ouvrir le fichier.

        > [!NOTE]
        > Dans votre mise <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>en œuvre de projet, fournir une valeur prioritaire qui indique le niveau auquel votre projet ouvre le fichier. Des valeurs prioritaires <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> sont fournies dans le recensement.

2. Chaque projet répond avec un niveau de priorité qui indique l’importance qu’il accorde au projet d’ouverture du dossier.

3. L’IDE utilise les critères suivants pour déterminer quel projet ouvre le fichier :

    - Le projet qui répond avec`DP_Intrinsic`la plus haute priorité ( ) ouvre le fichier. Si plus d’un projet répond avec cette priorité, le premier projet à répondre ouvre le dossier.

    - Si aucun projet ne répond`DP_Intrinsic`avec la plus haute priorité (), mais que tous les projets répondent avec la même priorité, moins, le projet actif ouvre le dossier. Si aucun projet n’est actif, le premier projet à répondre ouvre le fichier.

    - Si aucun projet ne revendique`DP_Unsupported`la propriété du fichier (), le projet Divers Files ouvre le dossier.

         Si une instance du projet Metcellaneous Files est créée, `DP_CanAddAsExternal`le projet répond toujours avec la valeur . Cette valeur indique que le projet peut ouvrir le fichier. Ce projet est utilisé pour héberger des fichiers ouverts qui ne sont pas dans un autre projet. La liste des éléments de ce projet n’est pas persistante; ce projet n’est visible dans **Solution Explorer** que lorsqu’il est utilisé pour ouvrir un fichier.

         Si le projet Divers Files n’indique pas qu’il peut ouvrir le dossier, une instance du projet n’a pas été créée. Dans ce cas, l’IDE crée un exemple du projet Divers Files et dit au projet d’ouvrir le fichier.

4. Dès que l’IDE détermine quel projet ouvre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> le fichier, il appelle la méthode sur ce projet.

5. Le projet a alors la possibilité d’ouvrir le fichier en utilisant un éditeur spécifique au projet ou un éditeur standard. Pour plus d’informations, voir [Comment ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md) et comment : Ouvrir les [éditeurs standard,](../../extensibility/how-to-open-standard-editors.md)respectivement.

## <a name="see-also"></a>Voir aussi
- [Afficher les fichiers en utilisant l’Open With command](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Ouvrez et enregistrez les éléments du projet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Comment : Ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)
- [Comment : Ouvrir les éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
