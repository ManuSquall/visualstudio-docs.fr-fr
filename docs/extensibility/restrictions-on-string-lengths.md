---
title: "Restrictions relatives aux longueurs de cha&#238;ne | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, restrictions relatives aux longueurs de chaîne"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Restrictions relatives aux longueurs de cha&#238;ne
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'API de plug\-in de contrôle de Source limite la longueur des chaînes utilisées dans les diverses fonctions.  
  
## Valeurs de longueur de chaîne  
  
|Constante|Valeur|  
|---------------|------------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Longueur n'inclut pas la fin `null`. Autres constantes avec le suffixe « \_SIZE » au lieu de « \_LEN » n'incluent pas d'espace pour la fin du `null`.  
  
|Constante|Valeur|  
|---------------|------------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)