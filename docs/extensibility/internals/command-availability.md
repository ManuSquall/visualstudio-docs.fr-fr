---
title: "Disponibilit&#233; de la commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes, contexte"
  - "éléments de menu, les contextes de visibilité"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Disponibilit&#233; de la commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le contexte de Visual Studio détermine quelles commandes sont disponibles. Le contexte peut changer selon le projet en cours, l’éditeur actuel, les VSPackages sont chargés et d’autres aspects de l’environnement de développement intégré \(IDE\).  
  
## Contextes de commande  
 Les contextes de commande suivants sont les plus courantes.  
  
-   **IDE** commandes fournies par l’IDE sont toujours disponibles.  
  
-   **VSPackage** VSPackages peut définir de commandes sont peuvent être affichées ou masquées.  
  
-   **Projet** commandes projet apparaissent uniquement pour le projet sélectionné actuellement.  
  
-   **Éditeur** qu’un seul éditeur peut être actif à la fois. Commandes de l’éditeur active sont disponibles. Un éditeur travaille en étroite collaboration avec un service de langage. Le service de langage doit traiter ses commandes dans le contexte de l’éditeur associé.  
  
-   **Type de fichier** un éditeur peut charger plus d’un type de fichier. Les commandes disponibles peuvent varier selon le type de fichier.  
  
-   **De la fenêtre active** la dernière fenêtre de document actif définit le contexte d’interface graphique utilisateur pour les combinaisons de touches. Toutefois, une fenêtre outil qui a une table de liaison de clé qui ressemble le navigateur Web interne peut également définir le contexte de l’interface utilisateur. Pour les fenêtres de document à plusieurs onglets tels que l’éditeur HTML chaque onglet possède un contexte de commande différents GUID. Après avoir enregistré une fenêtre outil, il est toujours disponible sur le **affichage** menu.  
  
-   **Le contexte de l’interface utilisateur** contextes d’interface utilisateur sont identifiés par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> lorsque la solution est en cours de génération, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> lorsque le débogueur est actif. Plusieurs contextes d’interface utilisateur peuvent être actives à la fois.  
  
## Définition des GUID de contexte personnalisé  
 Si un contexte de la commande appropriée que GUID n’est pas déjà défini, vous pouvez définir dans votre package VS et ensuite qu’il soit actif ou inactif afin de contrôler la visibilité des commandes de la programmer.  
  
1.  Enregistrez les GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> \(méthode\).  
  
2.  Obtenir l’état d’un GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> \(méthode\).  
  
3.  Activer et désactiver les GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> \(méthode\).  
  
    > [!CAUTION]
    >  Assurez\-vous que votre VSPackage n’affecte pas les GUID de contexte existant, car les autres packages VS peuvent dépendre les.  
  
## Voir aussi  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)