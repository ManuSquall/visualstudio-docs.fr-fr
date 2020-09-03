---
title: IDebugClassField ::D oesInterfaceExist | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f71346c1b69729ae54ef0d33be4149e7000316c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191125"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si une interface spécifique est définie dans la classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszInterfaceName`  
 dans Chaîne contenant le nom de l’interface à rechercher.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK, retourne S_FALSE si l’interface n’existe pas ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode obtient une énumération de toutes les interfaces et recherche une interface correspondante dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
