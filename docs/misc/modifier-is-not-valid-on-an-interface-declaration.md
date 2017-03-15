---
title: "&#39;&lt;modificateur&gt;&#39; n’est pas valide dans une d&#233;claration Interface | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30397"
  - "vbc30397"
helpviewer_keywords: 
  - "BC30397"
ms.assetid: 9143dc87-c396-4ff9-9987-0b460ee32b38
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;modificateur&gt;&#39; n’est pas valide dans une d&#233;claration Interface
Vous avez utilisé un modificateur non valide dans une déclaration `Interface`. Les seuls modificateurs valides pour les instructions `Sub`, `Function` ou `Property` déclarées dans une déclaration `Interface` sont les mots clés `Overloads` et `Default`. Les autres modificateurs, tels que `Public`, `Private`, `Friend`, `Protected`, `Shared`, `Static`, `Overrides`, `MustOverride` et `Overridable`, ne sont pas valides.  
  
 **ID d’erreur :** BC30397  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur.  
  
## Voir aussi  
 [NOT IN BUILD : Définition d’interface](http://msdn.microsoft.com/fr-fr/7840a52c-9c38-42c4-adbc-e2c02e9dc204)