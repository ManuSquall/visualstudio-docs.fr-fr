---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ajoute un message personnalisé au graphique de diagnostic *HUD* \(affichage prend en tête élevée\).  
  
## Syntaxe  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### Paramètres  
 `szMessage`  
 Le message devant être ajouté au HUD.  
  
## Remarques  
 Le diagnostic graphique HUD est affiché dans l'angle supérieur gauche de l'application qui s'exécute sous les diagnostics graphiques.  Il affiche des informations d'exécution sur l'application et sur la capture d'informations graphiques, et les messages qui sont ajoutés en appelant cette fonction.  
  
 Pour ajouter un message au HUD, vous ne devez pas activement capturer des graphiques informations—autrement dit, un message peut être ajouté à l'aide de l'instance de la classe `VsgDbg`, mais la fonction membre [Init](../debugger/init.md) n'est pas appelée en premier.  Les messages sont uniquement affichés dans HUD, ils ne sont pas enregistrés dans le fichier journal de graphiques.