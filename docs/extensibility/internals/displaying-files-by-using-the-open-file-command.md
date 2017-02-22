---
title: "Afficher les fichiers &#224; l&#39;aide de la commande Ouvrir un fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de projets, prise en charge de la commande Ouvrir un fichier"
  - "Ouvrir un fichier (commande)"
  - "persistance, prise en charge de la commande Ouvrir un fichier"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Afficher les fichiers &#224; l&#39;aide de la commande Ouvrir un fichier
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les étapes suivantes décrivent comment l'IDE gère la commande d' **Ouvrir un fichier** , qui est disponible dans le menu de **Fichier** dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Les étapes indiquent également comment les projets doivent satisfaire aux appels provenant de cette commande.  
  
 Lorsqu'un utilisateur clique sur la commande d' **Ouvrir un fichier** dans le menu de **Fichier** , et sélectionne un fichier de la boîte de dialogue d' **Ouvrir un fichier** , le processus suivant se produit.  
  
1.  À l'aide de le tableau en cours de exécution de document, l'IDE détermine si le fichier est déjà ouvert dans un projet.  
  
    -   Si le fichier est ouvert, l'IDE reblanchit la fenêtre.  
  
    -   Si le fichier n'est pas ouvert, l'IDE appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> pour interroger chaque projet de déterminer le projet peut ouvrir le fichier.  
  
        > [!NOTE]
        >  Dans votre mise en ? uvre de projet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, fournissez une valeur de priorité qui indique le niveau auquel votre projet ouvre le fichier.  Les valeurs de priorité sont fournies dans l'énumération d' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> .  
  
2.  Chaque projet répond à un niveau de priorité qui indique l'importance qu'il place pour être le projet pour ouvrir le fichier.  
  
3.  L'IDE utilise les critères suivants pour déterminer le projet ouvre le fichier :  
  
    -   Le projet qui répond à la priorité la plus élevée \(DP\_Intrinsic\) ouvre le fichier.  Si plusieurs projets répond à cette priorité, le premier projet pour répondre ouvre le fichier.  
  
    -   Si aucun projet ne répond à la priorité la plus élevée \(DP\_Intrinsic\), mais les projets répondent de même, la priorité plus basse, le projet actif ouvre le fichier.  Si aucun projet n'est actif, le premier projet pour répondre ouvre le fichier.  
  
    -   Si aucun projet ne fait la propriété du fichier \(DP\_Unsupported\), le projet Fichiers divers ouvre le fichier.  
  
         Si une instance du projet Fichiers divers est créée, le projet continue avec la valeur DP\_CanAddAsExternal.  cette valeur indique que le projet peut ouvrir le fichier.  Ce projet est utilisé de recevoir les fichiers ouverts qui ne sont pas dans un autre projet.  La liste d'éléments de ce projet n'est pas rendu persistant ; ce projet est visible dans **Explorateur de solutions** uniquement lorsqu'il est utilisé pour ouvrir un fichier.  
  
         Si le projet Fichiers divers n'indique pas qu'il peut ouvrir le fichier, une instance de projet n'a été créée.  Dans ce cas, l'IDE crée une instance du projet Fichiers divers et indique le projet pour ouvrir le fichier.  
  
4.  Dès que l'IDE détermine quel projet ouvre le fichier, il appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> sur ce projet.  
  
5.  Le projet possède alors l'option pour ouvrir le fichier à l'aide d'un éditeur spécifique au projet ou d'un éditeur standard.  Pour plus d'informations, consultez [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md) et [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md) respectivement.  
  
## Voir aussi  
 [Afficher les fichiers à l'aide de l'ouvrir avec la commande](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)   
 [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)