---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f74fafc325693df6a312647c9e9060a24cf256ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863553"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Définit le chemin d’accès ou les chemins d’accès des symboles de débogage sont recherchés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Chaîne contenant le chemin de recherche de symbole ou les chemins d’accès. Pour plus d’informations, consultez « Remarques ». Ne peut pas être null.|  
|`szSymbolCachePath`|[in] Chaîne contenant le chemin d’accès local où les symboles peuvent être mis en cache. Ne peut pas être null.|  
|`Flags`|[in] Pas utilisé ; toujours défini sur 0.|  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La chaîne `szSymbolSearchPath` est une liste d’un ou plusieurs chemins séparés par des points-virgules, pour rechercher des symboles. Ces chemins d’accès peuvent être un chemin d’accès local, un chemin d’accès UNC-style ou une URL. Ces chemins d’accès peuvent également être un mélange de types différents. Si le chemin d’accès est UNC (par exemple, \\\Symserver\Symbols), puis le moteur de débogage doit déterminer si le chemin d’accès à un serveur de symbole et doit être en mesure de charger les symboles à partir de ce serveur, la mise en cache dans le chemin d’accès spécifié par `szSymbolCachePath`.  
  
 Le chemin des symboles peut également contenir un ou plusieurs emplacements de cache. Les caches sont répertoriés par ordre de priorité, avec le cache de priorité le plus élevé en premier et séparées par des * symboles. Exemple :  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 Le [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) méthode effectue la charge réelle des symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

