---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05db065b047629e1eaac49e5f6aeeb05eed4307e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863822"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Conserve le contexte de la pile entre les appels de la méthode [IDiaFrameData :: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

## <a name="syntax"></a>Syntaxe

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDiaStackWalkFrame` .

|Méthode|Description|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Récupère la valeur d’un registre.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Définit la valeur d’un registre.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Lit la mémoire à partir de l’image.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Recherche l’adresse de retour de la fonction la plus proche dans le frame de pile spécifié.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Recherche dans le frame de pile spécifié une adresse de retour à l’adresse spécifiée ou à proximité de celle-ci.|

## <a name="remarks"></a>Remarques
 Cette interface est utilisée pendant l’exécution du programme pour lire et écrire des registres, ainsi que pour accéder à la mémoire et rechercher les adresses de retour.

## <a name="notes-for-callers"></a>Notes pour les appelants
 L’application cliente implémente cette interface et passe une instance de l’interface à la méthode [IDiaFrameData :: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . La même instance de cette interface est réutilisée et à nouveau pour maintenir l’état des registres lors de chaque appel de la `execute` méthode. La `execute` méthode utilise également cette interface pour déterminer l’adresse de retour.

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)