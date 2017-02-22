---
title: "BP_LOCATION_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "Structure BP_LOCATION_TYPE"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type d'emplacement du point d'arrêt pour une requête de point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## Membres  
 BPLT\_NONE  
 ne spécifie aucun emplacement du point d'arrêt.  
  
 BPLT\_FILE\_LINE  
 Spécifie le type d'emplacement du point d'arrêt en ligne de fichier.  
  
 BPLT\_FUNC\_OFFSET  
 spécifie le type d'emplacement du point d'arrêt comme un offset de fonction.  
  
 BPLT\_CONTEXT  
 Spécifie le type d'emplacement du point d'arrêt en tant que contexte.  
  
 BPLT\_STRING  
 Spécifie le type d'emplacement du point d'arrêt en tant que chaîne.  
  
 BPLT\_ADDRESS  
 spécifie le type d'emplacement du point d'arrêt comme adresse.  
  
 BPLT\_RESOLUTION  
 spécifie le type d'emplacement du point d'arrêt comme résolution.  
  
 BPLT\_CODE\_FILE\_LINE  
 Spécifie le type d'emplacement du point d'arrêt en ligne de code source.  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 Spécifie le type d'emplacement du point d'arrêt comme un offset de fonction du code.  
  
 BPLT\_CODE\_CONTEXT  
 Spécifie le type d'emplacement du point d'arrêt en tant que contexte de code.  
  
 BPLT\_CODE\_STRING  
 Spécifie le type d'emplacement du point d'arrêt comme une chaîne de code.  
  
 BPLT\_CODE\_ADDRESS  
 spécifie le type d'emplacement du point d'arrêt comme adresse.  
  
 BPLT\_DATA\_STRING  
 spécifie le type d'emplacement du point d'arrêt comme une chaîne de données.  
  
 BPLT\_TYPE\_MASK  
 Spécifie un masque de bits, afin que le type de point d'arrêt puisse être récupéré hors de la valeur.  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 Spécifie un masque de bits, afin que le type d'emplacement du point d'arrêt puisse être récupéré hors de la valeur.  
  
## Notes  
 passé comme paramètre à la méthode d' [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) .  
  
 un type d'emplacement du point d'arrêt est composé d'un type de point d'arrêt et d'un type d'emplacement.  Cela signifie qu'un type d'emplacement du point d'arrêt n'est jamais un seul type de point d'arrêt \(par exemple,`BPT_CODE`\) ou d'emplacement \(par exemple,`BPLT_FILE_LINE`\).  Les constantes prédéfinies pour tous les types d'emplacement du point d'arrêt actuellement pris en charge sont incluses dans cette énumération \(`BPLT_CODE_FILE_LINE` via `BPLT_DATA_STRING`\).  
  
 `BPT_CODE` et `BPT_DATA` sont des membres de l'énumération [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)