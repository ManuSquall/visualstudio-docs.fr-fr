---
title: IDiaDataSource | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f4ca43f4cefc80508961b918e094a6954e5f3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736529"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lance l’accès à une source de symboles de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaDataSource`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Récupère le nom de fichier pour la dernière erreur de chargement.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|S’ouvre et prépare un fichier de base de données (.pdb) de programme comme une source de données de débogage.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|S’ouvre et vérifie que le fichier de base de données (.pdb) de programme correspond à des informations de signature fournies ; prépare le fichier .pdb en tant qu’une source de données de débogage.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|S’ouvre et prépare les données de débogage associées au fichier.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prépare les données de débogage stockées dans un fichier du programme (.pdb) de la base de données accédé via un flux de données en mémoire.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Ouvre une session pour l’interrogation des symboles.|  
  
## <a name="remarks"></a>Notes  
 Un appel à une des méthodes load de la `IDiaDataSource` interface ouvre la source de symboles. Un appel réussi au [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) méthode retourne un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interface qui prend en charge l’interrogation de la source de données. Si la méthode load renvoie une erreur liée au fichier le [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) méthode retourner la valeur contient le nom de fichier associé à l’erreur.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est obtenue en appelant le `CoCreateInstance` fonction avec l’identificateur de classe `CLSID_DiaSource` et l’ID de l’interface de `IID_IDiaDataSource`. L’exemple montre comment cette interface est obtenue.  
  
## <a name="example"></a>Exemple  
  
```cpp#  
  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)



