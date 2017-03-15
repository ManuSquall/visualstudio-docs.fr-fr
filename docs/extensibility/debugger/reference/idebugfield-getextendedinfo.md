---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugField::GetExtendedInfo (méthode)"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait les informations détaillées concernant un champ.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### Paramètres  
 `guidExtendedInfo`  
 \[in\]  sélectionne les informations à retourner.  Les valeurs valides sont :  
  
|Valeur|Description|  
|------------|-----------------|  
|`guidConstantValue`|La valeur comme une séquence d'octets.|  
|`guidConstantType`|Le type comme une signature de type.|  
  
 `prgBuffer`  
 \[out\]  Retourne les informations détaillées.  
  
 `pdwLen`  
 \[in, out\]  Retourne la taille des informations détaillées, en octets.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Actuellement, cette méthode retourne uniquement le type ou la valeur d'une constante.  L'appelant doit libérer la mémoire tampon retournée dans `prgBuffer` en appelant la fonction de `CoTaskMemFree` COM \(C\+\+\) ou l' <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(c\#\).  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)