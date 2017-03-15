---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromPdb (méthode)"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre et prépare un fichier de base de données du programme \(.pdb\) comme source de données de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### Paramètres  
 pdbPath  
 \[in\]  Le chemin d'accès du fichier .pdb.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre les valeurs de retour possibles de cette méthode.  
  
|Valeur|Description|  
|------------|-----------------|  
|E\_PDB\_NOT\_FOUND|pour ouvrir le fichier, ou déterminé que le fichier a un format valide.|  
|E\_PDB\_FORMAT|Tenté d'accéder à un fichier par un format obsolète.|  
|E\_INVALIDARG|paramètre non valide.|  
|E\_UNEXPECTED|La source de données a déjà été préparée.|  
  
## Notes  
 Cette méthode charge les données de débogage directement à partir d'un fichier .pdb.  
  
 Pour valider le fichier .pdb à des critères spécifiques, utilisez la méthode d' [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Pour accéder au processus de chargement de données \(via un mécanisme de rappel\), utilisez la méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Pour charger un fichier .pdb directement de mémoire, utilisez la méthode d' [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) .  
  
## Exemple  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)