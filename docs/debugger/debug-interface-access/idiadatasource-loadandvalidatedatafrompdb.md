---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::loadAndValidateDataFromPdb (méthode)"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre et vérifie que le fichier de base de données du programme \(.pdb\) correspond aux informations de signature fournies, et prépare le fichier .pdb comme source de données de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### Paramètres  
 `pdbPath`  
 \[in\]  Le chemin d'accès du fichier .pdb.  
  
 `pcsig70`  
 \[in\]  La signature de GUID à vérifier par rapport à la signature de fichier .pdb.  Seuls les fichiers .pdb dans [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] et ont ultérieurement des signatures GUID.  
  
 `sig`  
 \[in\]  La signature 32 bits à vérifier par rapport à la signature de fichier .pdb.  
  
 `age`  
 \[in\]  Valeur de personnes à vérifier.  L'âge ne correspond toujours à aucune valeur d'heure, il est utilisée pour déterminer si un fichier .pdb est pas synchronisé avec un fichier .exe correspondant.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre les valeurs de retour possibles de cette méthode.  
  
|Valeur|Description|  
|------------|-----------------|  
|E\_PDB\_NOT\_FOUND|pour ouvrir le fichier, ou le fichier a un format valide.|  
|E\_PDB\_FORMAT|Tenté d'accéder à un fichier par un format obsolète.|  
|E\_PDB\_INVALID\_SIG|La signature ne correspond pas.|  
|E\_PDB\_INVALID\_AGE|L'âge ne correspond pas.|  
|E\_INVALIDARG|paramètre non valide.|  
|E\_UNEXPECTED|La source de données a déjà été préparée.|  
  
## Notes  
 Un fichier .pdb contient la signature et les valeurs de personnes.  Ces valeurs sont répliquées dans le fichier .exe ou .DLL qui correspond au fichier .pdb.  Avant de préparer la source de données, cette méthode vérifie que la signature nommée et l'âge du fichier .pdb correspondent aux valeurs fournies.  
  
 Pour charger un fichier .pdb sans validation, utilisez la méthode d' [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Pour accéder au processus de chargement de données \(via un mécanisme de rappel\), utilisez la méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Pour charger un fichier .pdb directement de mémoire, utilisez la méthode d' [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) .  
  
## Exemple  
  
```cpp#  
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
  
## Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)