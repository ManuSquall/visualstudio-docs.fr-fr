---
title: MODULE_INFO | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_INFO
helpviewer_keywords: MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd49230165282dd656252c4edaabfbaa31d43340
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfo"></a>MODULE_INFO
Décrit un module particulier (assembly, EXE ou DLL).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Membres  
 dwValidFields  
 Une combinaison d’indicateurs à partir de la [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) énumération qui spécifie les champs sont remplis.  
  
 m_bstrName  
 Nom du module.  
  
 m_bstrUrl  
 L’URL du module.  
  
 m_bstrVersion  
 La version du module.  
  
 m_bstrDebugMessage  
 Un message facultatif sur le module, par exemple, « symboles ne peut pas être chargés. »  
  
 m_addrLoadAddress  
 L’adresse de chargement de module.  
  
 m_addrPreferredLoadAddress  
 L’adresse de chargement par défaut du module.  
  
 m_dwSize  
 La taille du module.  
  
 m_dwLoadOrder  
 L’ordre de chargement de module.  
  
 m_TimeStamp  
 L’heure de que dernière modification du fichier de symboles.  
  
 m_bstrUrlSymbolLocation  
 L’emplacement du fichier de symboles (par exemple, «.\\») spécifié dans le module. Utilisé comme un emplacement de départ pour rechercher des symboles pour un module.  
  
 m_dwModuleFlags  
 Une combinaison d’indicateurs à partir de la [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) énumération qui décrit le module.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) méthode où il est renseigné.  
  
 Cette structure correspond à tous les modules figurant dans le **Modules** fenêtre.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)