---
title: IDiaDataSource::loadAndValidateDataFromPdb | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bcd82116c7499d2a2289fc0c198a2be053226721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
S’ouvre et vérifie que le fichier de base de données (.pdb) de programme correspond à fourni les informations de signature et prépare le fichier .pdb comme source de données de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdbPath`  
 [in] Le chemin d’accès au fichier .pdb.  
  
 `pcsig70`  
 [in] Signature GUID à vérifier par rapport à la signature du fichier .pdb. Fichiers .pdb uniquement [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et versions ultérieures ont des signatures GUID.  
  
 `sig`  
 [in] La signature de 32 bits à vérifier par rapport à la signature du fichier .pdb.  
  
 `age`  
 [in] Valeur d’âge à vérifier. La durée de vie ne correspond pas nécessairement une valeur de temps connu, il est utilisé pour déterminer si un fichier .pdb est synchronisé avec un fichier .exe.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.  
  
|Value|Description|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier ou le fichier a un format non valide.|  
|E_PDB_FORMAT|Vous avez tenté d’accéder à un fichier avec un format obsolète.|  
|E_PDB_INVALID_SIG|Signature ne correspond pas.|  
|E_PDB_INVALID_AGE|Âge ne correspond pas.|  
|E_INVALIDARG|Paramètre non valide.|  
|E_UNEXPECTED|La source de données a déjà été préparée.|  
  
## <a name="remarks"></a>Notes  
 Un fichier .pdb contient des valeurs de signature et âge. Ces valeurs sont répliqués dans le fichier .exe ou .dll correspondant au fichier .pdb. Avant de préparer la source de données, cette méthode vérifie la signature et l’âge du fichier .pdb nommé correspondent aux valeurs fournies.  
  
 Pour charger un fichier .pdb sans validation, utilisez la [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) (méthode).  
  
 Pour obtenir l’accès pour le processus de chargement de données (via un mécanisme de rappel), utilisez la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
 Pour charger un fichier .pdb directement à partir de la mémoire, utilisez le [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (méthode).  
  
## <a name="example"></a>Exemple  
  
```C++  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)