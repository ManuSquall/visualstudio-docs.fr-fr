---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

propriétés spécifiées de lectures du jeu de propriétés actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Paramètres  
 `cpspec`  
 \[in\]  Nombre de propriétés spécifiées dans le tableau d' `rgpspec` .  Si le zéro, la méthode ne retourne aucune propriété mais retourne `S_OK` comme code de réussite.  
  
 `rgpspec`  
 \[in\]  Un tableau de propriétés à lire.  Les propriétés peuvent être spécifiées par un ID de propriété ou par un nom de chaîne facultative.  Il n'est pas nécessaire de spécifier des propriétés dans un ordre particulier dans le tableau.  Le tableau peut contenir des propriétés en double, provoquant ainsi des valeurs de propriété en double au retour pour les propriétés simples.  les propriétés Non\-simples doivent retourner l'accès refusé lors d'une tentative de les ouvrir une deuxième fois.  Le tableau peut contenir un mélange des identificateurs de propriété et des ID de chaîne.  Ce tableau doit avoir au moins le numéro d' `cpspec` de valeurs de propriété.  
  
 `rgvar`  
 \[in, out\]  Un tableau de structures d' `PROPVARIANT` \(dans l'espace de noms Microsoft.VisualStudio.OLE.Interop\) à remplir avec des valeurs pour chaque propriété.  Le tableau doit être au moins des éléments d' `cpspec` en taille.  L'appelant n'a pas besoin d'initialiser les valeurs dans le tableau.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si un ou plusieurs des propriétés sont introuvables.  Sinon retourne un code d'erreur.  
  
## Notes  
 Si une propriété est introuvable, l'entrée correspondante dans le tableau d' `rgvar` contient `VARIANT` avec le type d' `VT_EMPTY`.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)