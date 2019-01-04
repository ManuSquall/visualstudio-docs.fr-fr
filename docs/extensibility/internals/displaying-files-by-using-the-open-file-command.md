---
title: Afficher les fichiers à l’aide de la commande Ouvrir un fichier | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59ff5d938c21c6344d1979fbfca94e8acb791db6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964661"
---
# <a name="display-files-by-using-the-open-file-command"></a>Afficher les fichiers à l’aide de la commande Ouvrir un fichier
Les étapes suivantes décrivent comment l’IDE gère le **ouvrir un fichier** commande, qui est disponible sur le **fichier** menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Les étapes décrivent également la façon dont les projets doivent répondre aux appels issus de cette commande.  
  
 Lorsqu’un utilisateur clique sur le **ouvrir un fichier** commande sur le **fichier** menu et sélectionne un fichier à partir de la **ouvrir un fichier** boîte de dialogue, la processus suivante se produit :  
  
1.  À l’aide de la table de document en cours d’exécution, l’IDE détermine si le fichier est déjà ouvert dans un projet.  
  
    -   Si le fichier est ouvert, l’IDE resurfaces la fenêtre.  
  
    -   Si le fichier n’est pas ouvert, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> pour chaque projet afin de déterminer quel projet peut ouvrir le fichier de requête.  
  
        > [!NOTE]
        >  Dans votre implémentation de projet de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, fournir une valeur de priorité qui indique le niveau auquel votre projet s’ouvre le fichier. Les valeurs de priorité sont fournies dans le <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération.  
  
2.  Chaque projet répond avec un niveau de priorité qui indique l’importance qu’il place sur en cours du projet à ouvrir le fichier.  
  
3.  L’IDE utilise les critères suivants pour déterminer quel projet s’ouvre le fichier :  
  
    -   Le projet qui répond avec la priorité la plus élevée (`DP_Intrinsic`) ouvre le fichier. Si plusieurs projets répond avec cette priorité, le premier projet répondre ouvre le fichier.  
  
    -   Si aucun projet ne répond avec la priorité la plus élevée (`DP_Intrinsic`), mais tous les projets répond avec la priorité de même, avec moins, le projet actif ouvre le fichier. Si aucun projet n’est active, le premier projet répondre ouvre le fichier.  
  
    -   Si aucun projet ne réclame la propriété du fichier (`DP_Unsupported`), le projet fichiers divers ouvre le fichier.  
  
         Si une instance du projet fichiers divers est créée, le projet répond toujours avec la valeur `DP_CanAddAsExternal`. Cette valeur indique que le projet peut ouvrir le fichier. Ce projet est utilisé pour héberger les fichiers ouverts ne sont pas dans n’importe quel autre projet. La liste des éléments de ce projet n’est pas rendu persistant ; ce projet est visible dans **l’Explorateur de solutions** uniquement lorsqu’il est utilisé pour ouvrir un fichier.  
  
         Si le projet fichiers divers n’indique pas qu’il peut ouvrir le fichier, une instance du projet n’a pas été créée. Dans ce cas, l’IDE crée une instance du projet fichiers divers et indique le projet pour ouvrir le fichier.  
  
4.  Dès que l’IDE détermine quel projet s’ouvre le fichier, elle appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode sur ce projet.  
  
5.  Le projet a ensuite la possibilité d’ouvrir le fichier à l’aide d’un éditeur spécifique au projet ou un éditeur standard. Pour plus d'informations, voir [Procédure : Ouvrir des éditeurs spécifiques du projet](../../extensibility/how-to-open-project-specific-editors.md) et [Comment : Ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md), respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher les fichiers à l’aide de la commande Ouvrir avec](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Guide pratique pour Ouvrez éditeurs spécifiques du projet](../../extensibility/how-to-open-project-specific-editors.md)   
 [Guide pratique pour Éditeurs standards Open](../../extensibility/how-to-open-standard-editors.md)