---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0fba00357fcb328000b904d3977bf03e5bc3885
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888171"
---
# <a name="module_info"></a>MODULE_INFO
Décrit un module particulier (DLL, EXE ou assembly).

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
 Combinaison d’indicateurs de l’énumération [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) qui spécifie les champs à remplir.

 `m_bstrName`\
 Nom du module.

 `m_bstrUrl`\
 URL du module.

 `m_bstrVersion`\
 Version du module.

 `m_bstrDebugMessage`\
 Message facultatif concernant le module, par exemple, « les symboles ne peuvent pas être chargés ».

 `m_addrLoadAddress`\
 Adresse de chargement du module.

 `m_addrPreferredLoadAddress`\
 Adresse de chargement par défaut du module.

 `m_dwSize`\
 Taille du module.

 `m_dwLoadOrder`\
 Ordre de chargement du module.

 `m_TimeStamp`\
 Heure de la dernière modification du fichier de symboles.

 `m_bstrUrlSymbolLocation`\
 Emplacement du fichier de symboles (par exemple, « . \\ ») spécifié dans le module. Utilisé comme emplacement de départ pour rechercher des symboles pour un module.

 `m_dwModuleFlags`\
 Combinaison d’indicateurs de l’énumération [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) qui décrit le module.

## <a name="remarks"></a>Remarques
 Cette structure est transmise à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) où elle est remplie.

 Cette structure correspond à chaque module listé dans la fenêtre **modules** .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
