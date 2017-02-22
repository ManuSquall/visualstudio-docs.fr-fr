---
title: "Comment&#160;: d&#233;boguer en mode mixte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "déboguer (Visual Studio), mode mixte"
  - "déboguer des DLL"
  - "débogage en mode mixte"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: d&#233;boguer en mode mixte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les procédures suivantes décrivent comment déboguer le code managé et le code natif, également connu sous le nom de débogage en mode mixte.  Pour ce faire, il existe deux scénarios, selon si la DLL ou l'application est écrite en code natif :  
  
-   L'application appelante qui appelle votre DLL est écrite en code natif.  Dans ce cas, votre DLL est managée et les débogueurs managés et natifs doivent être activés pour déboguer ces deux types de code.  Vous pouvez le vérifier dans la boîte de dialogue Pages de propriétés de **\<Projet\>**.  Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante.  
  
-   L'application appelante qui appelle votre DLL est écrite en code managé et votre DLL est écrite en code natif.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour activer le débogage en mode mixte  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez le projet.  
  
2.  Dans le menu **Affichage**, cliquez sur **Pages de propriétés**.  
  
3.  Dans la boîte de dialogue Pages de propriétés de **\<Projet\>**, développez le nœud **Propriétés de configuration** et sélectionnez **Débogage**.  
  
4.  Définissez **Mixte** ou **Automatique** pour **Type de débogueur**.  
  
## Voir aussi  
 [Comment : déboguer à partir d'un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)