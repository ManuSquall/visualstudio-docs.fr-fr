---
title: "MODULE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO"
helpviewer_keywords: 
  - "Structure MODULE_INFO"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit un module particulier \(DLL, EXE, ou assembly\).  
  
## Syntaxe  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```c#  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## Membres  
 dwValidFields  
 Une combinaison des indicateurs d'énumération de [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) qui spécifie quels champs sont remplis.  
  
 m\_bstrName  
 Nom du module.  
  
 m\_bstrUrl  
 L'URL du module.  
  
 m\_bstrVersion  
 la version de module.  
  
 m\_bstrDebugMessage  
 Un message facultatif à propos de le module, par exemple, « les symboles ne peut pas être chargé. »  
  
 m\_addrLoadAddress  
 l'adresse de chargement du module.  
  
 m\_addrPreferredLoadAddress  
 l'adresse par défaut de charge du module.  
  
 m\_dwSize  
 La taille du module.  
  
 m\_dwLoadOrder  
 L'ordre de chargement du module.  
  
 m\_TimeStamp  
 Le temps le fichier de symboles de sa dernière modification.  
  
 m\_bstrUrlSymbolLocation  
 l'emplacement du fichier de symboles \(par exemple, « .  \\ "\) spécifié dans le module.  Utilisé comme emplacement commençant à rechercher des symboles d'un module.  
  
 m\_dwModuleFlags  
 Une combinaison des indicateurs d'énumération de [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md) qui décrit le module.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) où elle est terminée.  
  
 cette structure correspond à chaque module répertorié dans la fenêtre de **Module** .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)