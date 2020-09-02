---
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35644f06ae929e4168d5dc44d6fc488de020a637
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547453"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prépare les données de débogage stockées dans un fichier de base de données du programme (. pdb) accessible via un flux de données en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pIStream  
 dans <xref:IStream> Objet représentant le flux de données à utiliser.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.  
  
|Valeur|Description|  
|-----------|-----------------|  
|E_PDB_FORMAT|Tentative d’accès à un fichier avec un format obsolète.|  
|E_INVALIDARG|Paramètre non valide.|  
|E_UNEXPECTED|La source de données a déjà été préparée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet d’obtenir les données de débogage d’un fichier exécutable à partir de la mémoire via un <xref:IStream> objet.  
  
 Pour charger un fichier. pdb sans validation, utilisez la méthode [IDiaDataSource :: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Pour valider le fichier. pdb par rapport à des critères spécifiques, utilisez la méthode [IDiaDataSource :: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Pour accéder au processus de chargement des données (via un mécanisme de rappel), utilisez la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource :: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
