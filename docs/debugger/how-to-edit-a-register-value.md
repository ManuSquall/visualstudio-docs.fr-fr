---
title: "Comment&#160;: modifier une valeur de Registre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.register.edit"
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
  - "valeurs des registres"
  - "Registres (fenêtre), modifier les valeurs de registres"
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: modifier une valeur de Registre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**.  
  
### Pour modifier la valeur d'un Registre  
  
1.  Dans la fenêtre **Registres**, utilisez la touche TAB ou la souris pour placer le point d'insertion sur la valeur à modifier.  Quand vous commencez à taper, le curseur doit se trouver en face de la valeur à remplacer.  
  
2.  Tapez la nouvelle valeur.  
  
    > [!CAUTION]
    >  Modifier des valeurs de registres \(principalement des registres EIP et EBP\) peut affecter l'exécution du programme.  
  
    > [!CAUTION]
    >  Modifier des valeurs à virgule flottante risque d'entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires.  Dans un Registre en virgule flottante, même une modification apparemment anodine risque d'entraîner des changements de certains bits de poids faible.  
  
## Voir aussi  
 [Comment : utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)