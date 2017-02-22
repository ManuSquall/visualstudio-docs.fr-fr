---
title: "IntelliSenseHostFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "IntelliSense, IntellisenseHostFlags (énumération)"
  - "IntellisenseHostFlags (énumération)"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie des indicateurs d'hôte IntelliSense.  
  
## Syntaxe  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### Paramètres  
  
|Membres|Description|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Mémoire tampon de contexte est en lecture seule.|  
|`IHF_NOSEPARATESUBJECT`|Aucun texte de l'objet. Mémoire tampon de contexte contient IntelliSense\-target \(implique `!IHF_READONLYCONTEXT`\).|  
|`IHF_SINGLELINESUBJECT`|Texte de l'objet n'est pas compatible en avec plusieurs lignes.|  
|`IHF_FORCECOMMITTOCONTEXT`|Comme pour `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Modification \(dans le contexte ou objet\) doit être effectuée en mode Refrappe.|  
  
## Configuration requise  
 SingleFileeditor.idl  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop>