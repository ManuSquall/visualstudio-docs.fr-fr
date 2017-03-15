---
title: "IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient les informations d'attribut comme un blob des octets.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```c#  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### Paramètres  
 `ppBlob`  
 \[in, out\]  Un tableau qui est terminée avec les octets d'attribut.  
  
 `pdwLen`  
 \[in, out\]  Spécifie le nombre maximal d'octets pour revenir dans le tableau d' `ppBlob` et retourne le nombre d'octets réellement écrits dans le tableau.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Définissez le paramètre d' `ppBlob` à une valeur NULL pour retourner le nombre d'octets des attributs disponibles.  Ensuite allouez un tableau et passez ce tableau dans pour le paramètre d' `ppBlob` .  
  
 Les octets d'attribut représentent les données brutes de cet attribut.  
  
## Voir aussi  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)