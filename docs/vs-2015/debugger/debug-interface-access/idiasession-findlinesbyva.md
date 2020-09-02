---
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca69acebc9710bc18cba39ea9998bf90d2bf5767
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151646"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les informations de numéro de ligne pour les lignes contenues dans une plage d’adresses virtuelles (VA) spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 dans Spécifie l’adresse en tant que VA.  
  
 `length`  
 dans Spécifie le nombre d’octets de la plage d’adresses à couvrir avec cette requête.  
  
 `ppResult`  
 à Retourne un objet [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste de tous les numéros de ligne qui couvrent la plage d’adresses spécifiée.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre une fonction qui obtient tous les numéros de ligne contenus dans une fonction à l’aide de l’adresse virtuelle et de la longueur de la fonction.  
  
```cpp#  
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    ULONGLONG            va;  
    ULONGLONG            length;  
  
    if (pFunc->get_virtualAddress ( &va ) == S_OK)  
    {  
        pFunc->get_length( &length );  
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
