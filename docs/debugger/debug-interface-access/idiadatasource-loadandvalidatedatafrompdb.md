---
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 272b43f7e33ce495aabd53f33022bdeaf4b951fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948900"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
S’ouvre et vérifie que le fichier de base de données (.pdb) de programme correspond à des informations de signature fournies et prépare le fichier .pdb en tant qu’une source de données de débogage.  
  
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
 [in] Le GUID de signature à vérifier la signature du fichier .pdb. Fichiers .pdb uniquement [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et versions ultérieures ont des signatures GUID.  
  
 `sig`  
 [in] La signature de 32 bits à vérifier par rapport à la signature de fichier .pdb.  
  
 `age`  
 [in] Valeur d’âge à vérifier. La durée de vie ne correspond pas nécessairement à n’importe quelle valeur de temps connu, il est utilisé pour déterminer si un fichier .pdb est désynchronisé avec un fichier .exe correspondant.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.  
  
|Value|Description|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier ou le fichier a un format non valide.|  
|E_PDB_FORMAT|Essaie d’accéder à un fichier avec un format obsolète.|  
|E_PDB_INVALID_SIG|Signature ne correspond pas.|  
|E_PDB_INVALID_AGE|Âge ne correspond pas.|  
|E_INVALIDARG|Paramètre non valide.|  
|E_UNEXPECTED|La source de données a déjà été préparée.|  
  
## <a name="remarks"></a>Notes  
 Un fichier .pdb contient des valeurs de signature et âge. Ces valeurs sont répliquées dans le fichier .exe ou .dll correspondant au fichier .pdb. Avant de préparer la source de données, cette méthode vérifie que le fichier .pdb nommé signature et l’âge correspondent aux valeurs fournies.  
  
 Pour charger un fichier .pdb sans validation, utilisez la [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) (méthode).  
  
 Pour obtenir l’accès pour le processus de chargement de données (via un mécanisme de rappel), utilisez le [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).  
  
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