---
title: "Comment&#160;: utiliser la fen&#234;tre Registres | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.registers"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "registres, débogage"
  - "contenus de registres"
  - "indicateurs, fenêtre Registres"
  - "groupes de registres"
  - "débogage (Visual Studio), fenêtre Registres"
  - "Registres (fenêtre)"
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser la fen&#234;tre Registres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**, catégorie **Général**.  
  
 La fenêtre **Registres** affiche le contenu des registres.  Si la fenêtre **Registres** reste ouverte pendant que vous exécutez le programme pas à pas, vous pouvez voir changer les valeurs des registres au fil de l'exécution du code.  Les valeurs récemment modifiées s'affichent en rouge.  Il est possible de modifier les valeurs des registres.  Pour plus d'informations, consultez [Comment : modifier une valeur de Registre](../debugger/how-to-edit-a-register-value.md).  
  
 Pour réduire l'encombrement, la fenêtre **Registres** classe les registres en groupes, lesquels varient en fonction de la plateforme et du type de processeur.  Vous pouvez afficher ou masquer des groupes selon vos besoins.  Pour plus d'informations, consultez [Comment : afficher et masquer les groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Pour une introduction avancée aux concepts qui sous\-tendent les registres et la fenêtre Registres, consultez [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour afficher la fenêtre Registres  
  
-   Dans le menu **Déboguer**, sélectionnez **Fenêtres**, puis **Registres**.  
  
     Le débogueur doit être en cours d'exécution ou en mode arrêt.  
  
    > [!NOTE]
    >  Les informations de Registre ne sont pas disponibles aux applications de script ou SQL.  
  
## Voir aussi  
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)