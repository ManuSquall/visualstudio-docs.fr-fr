---
title: "Afficher les fichiers à l’aide de la commande Ouvrir un fichier | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75d714399f851aa479f398064e576790c793fffa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Afficher les fichiers à l’aide de la commande Ouvrir un fichier
Les étapes suivantes décrivent comment l’IDE gère le **ouvrir le fichier** commande, qui est disponible sur le **fichier** menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Les étapes décrivent également comment les projets doivent répondre aux appels provenant de cette commande.  
  
 Lorsqu’un utilisateur clique sur le **ouvrir le fichier** commande le **fichier** menu et sélectionne un fichier à partir de la **ouvrir un fichier** boîte de dialogue, la processus suivante se produit.  
  
1.  À l’aide de la table de document en cours d’exécution, l’IDE détermine si le fichier est déjà ouvert dans un projet.  
  
    -   Si le fichier est ouvert, l’IDE resurfaces la fenêtre.  
  
    -   Si le fichier n’est pas ouvert, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> pour chaque projet pour déterminer le projet qui peut ouvrir le fichier de requête.  
  
        > [!NOTE]
        >  Dans votre implémentation de projet de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, fournissez une valeur de priorité qui indique le niveau auquel votre projet s’ouvre le fichier. Les valeurs de priorité sont fournies dans le <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération.  
  
2.  Chaque projet répond avec un niveau de priorité qui indique l’importance qu’il place sur en cours pour ouvrir le fichier projet.  
  
3.  L’IDE utilise les critères suivants pour déterminer le projet qui ouvre le fichier :  
  
    -   Le projet qui répond à la priorité la plus élevée (DP_Intrinsic) s’ouvre le fichier. Si plusieurs projets répond avec cette priorité, le premier projet répondre ouvre le fichier.  
  
    -   Si aucun répond de projet avec la priorité la plus élevée (DP_Intrinsic), mais tous les projets y répondre avec la priorité de celui-ci, inférieure, le projet actif ouvre le fichier. Si aucun projet n’est actif, le premier projet répondre ouvre le fichier.  
  
    -   Si aucun projet ne revendications possession du fichier (DP_Unsupported), le projet fichiers divers ouvre le fichier.  
  
         Si une instance du projet fichiers divers est créée, le projet répond toujours avec la valeur DP_CanAddAsExternal. Cette valeur indique que le projet peut ouvrir le fichier. Ce projet est utilisé pour héberger les fichiers ouverts ne sont pas dans un autre projet. La liste des éléments dans ce projet n’est pas persistante ; ce projet n’est visible dans **l’Explorateur de solutions** uniquement lorsqu’il est utilisé pour ouvrir un fichier.  
  
         Si le projet fichiers divers n’indique pas qu’il peut ouvrir le fichier, une instance du projet n’a pas été créée. Dans ce cas, l’IDE crée une instance du projet fichiers divers et indique le projet à ouvrir le fichier.  
  
4.  Dès que l’IDE détermine quel projet ouvre le fichier, elle appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode sur ce projet.  
  
5.  Ensuite, le projet a la possibilité d’ouvrir le fichier à l’aide d’un éditeur spécifique au projet ou un éditeur standard. Pour plus d’informations, consultez [Comment : ouvrir les éditeurs spécifique au projet](../../extensibility/how-to-open-project-specific-editors.md) et [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md), respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher les fichiers à l’aide de l’ouvrir avec la commande](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)   
 [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)