---
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 761c94673a5f5cec55ce0174561946f1d5302cb4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953053"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit les attributs d’un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```csharp  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## <a name="members"></a>Membres  
 TEXT_DOC_ATTR_READONLY_2  
 Indique que le document est en lecture seule.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  En fait, cette valeur n’est pas définie dans l’assembly pour C#. Au lieu de cela, vous devez copier la définition de votre fichier source.  
  
 Passé en tant qu’argument à la [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
