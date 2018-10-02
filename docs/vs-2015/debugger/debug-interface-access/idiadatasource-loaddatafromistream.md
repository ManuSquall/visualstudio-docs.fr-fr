---
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bba8ba990167872b9657c16b8b8620ddac96896d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495977"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaDataSource::loadDataFromIStream](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiadatasource-loaddatafromistream).  
  
Prépare les données de débogage stockées dans un fichier du programme (.pdb) de la base de données accédé via un flux de données en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pIStream  
 [in] Un <xref:IStream> objet représentant le flux de données à utiliser.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.  
  
|Value|Description|  
|-----------|-----------------|  
|E_PDB_FORMAT|Essaie d’accéder à un fichier avec un format obsolète.|  
|E_INVALIDARG|Invalidparameter.|  
|E_UNEXPECTED|Source de données a déjà été préparée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet des données de débogage pour un fichier exécutable doit être obtenu à partir de la mémoire via un <xref:IStream> objet.  
  
 Pour charger un fichier .pdb sans validation, utilisez la [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) (méthode).  
  
 Pour valider le fichier .pdb par rapport à des critères spécifiques, utilisez le [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) (méthode).  
  
 Pour obtenir l’accès pour le processus de chargement de données (via un mécanisme de rappel), utilisez le [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)



