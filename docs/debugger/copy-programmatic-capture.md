---
title: "Copier (capture par programmation) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Copier (capture par programmation)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Copie le contenu du fichier actif du journal de graphiques \(.vsglog\) dans un nouveau fichier.  
  
## Syntaxe  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### Paramètres  
 `szNewVSGLog`  
 Le nom du nouveau fichier journal de graphique.  
  
## Remarques  
 Pour copier les informations de graphiques dans un nouveau fichier, vous devez déjà avoir capturé des informations de certains graphique ; sinon, rien ne se produit.