---
title: "Comment : impl&#233;menter des marqueurs d&#39;erreur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - marqueurs d'erreur"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment : impl&#233;menter des marqueurs d&#39;erreur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il est très difficile les personnalisations d'éditeur de texte implémenter des marques d'erreurs \(ou des lignes ondulées rouges\).  Toutefois, les avantages qu'ils permettent aux utilisateurs de votre VSPackage peuvent fortement être supérieurs au coût pour contribuer.  Les marques d'erreurs marquent subtile le texte que votre l'analyseur de langage comme incorrect avec une ligne ondulée rouge ou ondulée.  Cet indicateur aide les programmeurs en affichant visuellement code incorrect.  
  
 Marqueurs de texte à utiliser pour implémenter des soulignements ondulés rouges.  En règle générale, les services linguistiques ajoutez les lignes ondulées rouges à la mémoire tampon de texte comme série d'arrière\-plan, à la durée d'inactivité ou dans un thread d'arrière\-plan.  
  
### pour implémenter la fonctionnalité rouge de ligne ondulée  
  
1.  Sélectionnez le texte dans lequel vous voulez l'endroit la ligne ondulée rouge.  
  
2.  créez une marque du type `MARKER_CODESENSE_ERROR`.  Pour plus d'informations, consultez [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Ensuite, passez un pointeur d'interface de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
 Ce processus vous permet également de créer le texte de conseils ou un menu contextuel spécial sur une marque données.  Pour plus d'informations, consultez [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
 Les objets suivants sont requis avant que les marqueurs d'erreurs puissent être affichées.  
  
-   un analyseur.  
  
-   Un fournisseur de la tâche \(autrement dit, une implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\) qui contient un enregistrement des modifications apportées aux informations de ligne pour identifier les lignes re\-à analyser.  
  
-   Un filtre d'affichage de texte qui capture les événements de modification du signe insertion de la vue à l'aide de la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\).  
  
 l'analyseur, le fournisseur de tâche, et le filtre fournissent l'infrastructure nécessaire pour rendre des marques d'erreurs possibles.  Les étapes suivantes fournissent le processus pour afficher des marqueurs d'erreurs.  
  
1.  Dans une vue qui est filtrée, le filtre obtient un pointeur vers le fournisseur de tâche associée aux données de cette vue.  
  
    > [!NOTE]
    >  Vous pouvez utiliser le même filtre de commande pour obtenir des conseils de méthode, saisie semi\-automatique des instructions, marqueurs d'erreurs, et ainsi de suite.  
  
2.  Lorsque le filtre reçoit un événement indiquant que vous avez déplacé vers une autre ligne, une tâche est créée pour rechercher des erreurs.  
  
3.  Le gestionnaire de tâche vérifie si la ligne est modifiée.  Si c'est le cas, elle analyse la ligne pour les erreurs.  
  
4.  Si des erreurs sont rencontrées, le fournisseur de tâche crée une instance de tâche.  Cette instance crée le marqueur de texte que l'environnement utilise comme marqueur d'erreurs dans l'affichage de texte.  
  
## Voir aussi  
 [À l'aide de marqueurs de texte avec l'API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)