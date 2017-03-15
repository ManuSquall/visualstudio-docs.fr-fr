---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "IDiaDataSource::loadDataForExe (méthode)"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre et prépare les données de débogage associées au fichier de .exe\/.dll.  
  
## Syntaxe  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### Paramètres  
 exécutable  
 \[in\]  Chemin d'accès au fichier .exe ou au fichier .DLL.  
  
 searchPath  
 \[in\]  Chemin d'accès de substitution pour rechercher les informations de débogage.  
  
 pCallback  
 \[in\]  Une interface d' `IUnknown` d'un objet qui prend en charge une interface de rappel de débogage, telles qu' [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), et\/ou les interfaces d' [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant répertorie certains des codes d'erreur possibles de cette méthode.  
  
|Valeur|Description|  
|------------|-----------------|  
|E\_PDB\_NOT\_FOUND|pour ouvrir le fichier, ou le fichier a un format valide.|  
|E\_PDB\_FORMAT|Tenté d'accéder à un fichier par un format obsolète.|  
|E\_PDB\_INVALID\_SIG|La signature ne correspond pas.|  
|E\_PDB\_INVALID\_AGE|L'âge ne correspond pas.|  
|E\_INVALIDARG|paramètre non valide.|  
|E\_UNEXPECTED|La source de données a déjà été préparée.|  
  
## Notes  
 L'en\-tête de débogage des noms de fichiers de .exe\/.dll la colocalisation des données associée au débogage.  
  
 Cette méthode lit l'en\-tête puis les recherches de débogage pour et prépare les données de débogage.  La progression de la recherche peut, éventuellement, être stockée et contrôlée par les rappels.  Par exemple, [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) est appelé lorsque la méthode d' `IDiaDataSource::loadDataForExe` recherche et traite un répertoire debug.  
  
 Les interfaces d' [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) et d' [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) permettent l'application cliente de fournir d'autres méthodes pour lire des données à partir de le fichier exécutable lorsque le fichier n'est pas accessible directement via l'E\/S de fichier standard.  
  
 Pour charger un fichier .pdb sans validation, utilisez la méthode d' [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Pour valider le fichier .pdb à des critères spécifiques, utilisez la méthode d' [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Pour charger un fichier .pdb directement de mémoire, utilisez la méthode d' [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) .  
  
## Exemple  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)