---
title: IDiaDataSource | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b6ddb2ba2cc568b8f07e6643dcaeb93c0dec8ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasource"></a>IDiaDataSource
Lance l’accès à une source de symboles de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaDataSource`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Récupère le nom de fichier pour la dernière erreur de chargement.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|S’ouvre et prépare un fichier programme (.pdb) comme source de données de débogage.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|S’ouvre et vérifie que le fichier de base de données (.pdb) de programme correspond aux informations de signature fournies ; prépare le fichier .pdb comme source de données de débogage.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|S’ouvre et prépare les données de débogage associées au fichier.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prépare les données de débogage stockées dans un fichier du programme (.pdb) de la base de données accédé via un flux de données en mémoire.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Ouvre une session pour l’interrogation des symboles.|  
  
## <a name="remarks"></a>Remarques  
 Un appel à une des méthodes load de la `IDiaDataSource` interface ouvre la source de symbole. Un appel réussi pour le [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) méthode retourne un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interface qui prend en charge l’interrogation de la source de données. Si la méthode load renvoie une erreur liée au fichier le [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) méthode retourne la valeur contient le nom de fichier associé à l’erreur.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est obtenue en appelant le `CoCreateInstance` fonction avec l’identificateur de classe `CLSID_DiaSource` et l’ID de l’interface de `IID_IDiaDataSource`. L’exemple montre comment cette interface est obtenue.  
  
## <a name="example"></a>Exemple  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)