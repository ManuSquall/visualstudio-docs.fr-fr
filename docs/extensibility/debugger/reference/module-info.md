---
title: MODULE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714314"
---
# <a name="module_info"></a>MODULE_INFO
Décrit un module particulier (DLL, EXE ou assemblage).

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
 `dwValidFields`\
 Une combinaison de drapeaux de [l’MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) énumération qui précise quels champs sont remplis.

 `m_bstrName`\
 Nom du module.

 `m_bstrUrl`\
 L’URL du module.

 `m_bstrVersion`\
 La version module.

 `m_bstrDebugMessage`\
 Un message facultatif sur le module, par exemple, "Les symboles ne peuvent pas être chargés."

 `m_addrLoadAddress`\
 L’adresse de charge du module.

 `m_addrPreferredLoadAddress`\
 L’adresse de charge préférée du module.

 `m_dwSize`\
 La taille du module.

 `m_dwLoadOrder`\
 La commande de chargement du module.

 `m_TimeStamp`\
 L’heure à la dernière modification du fichier symbole.

 `m_bstrUrlSymbolLocation`\
 L’emplacement du fichier symbole (par\\exemple, ". ") spécifié dans le module. Utilisé comme point de départ pour trouver des symboles pour un module.

 `m_dwModuleFlags`\
 Une combinaison de drapeaux de [l’MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) énumération qui décrit le module.

## <a name="remarks"></a>Notes
 Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) où elle est remplie.

 Cette structure correspond à chaque module répertorié dans la fenêtre **Modules.**

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
