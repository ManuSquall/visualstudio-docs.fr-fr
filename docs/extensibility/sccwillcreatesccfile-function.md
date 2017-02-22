---
title: "SccWillCreateSccFile (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "SccWillCreateSccFile (fonction)"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccWillCreateSccFile (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction détermine si le plug\-in de contrôle de code source prend en charge la création de la MSSCCPRJ. Fichier de contrôle de code source pour chacun des fichiers donnés.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 nFiles  
 \[in\] Le nombre de noms de fichiers inclus dans le `lpFileNames` de tableau, ainsi que la longueur de la `pbSccFiles` tableau.  
  
 lpFileNames  
 \[in\] Un tableau de noms de fichier qualifié complet à vérifier \(tableau doit être alloué par l'appelant\).  
  
 pbSccFiles  
 \[dans, out\] Tableau dans lequel stocker les résultats.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Opération réussie.|  
|SCC\_E\_INVALIDFILEPATH|Parmi les chemins d'accès dans le tableau n'est pas valide.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique.|  
  
## Notes  
 Cette fonction est appelée avec une liste de fichiers pour déterminer si le plug\-in de contrôle de code source prend en charge dans le MSSCCPRJ. Fichier SCC pour chacun des fichiers données \(pour plus d'informations sur le MSSCCPRJ. Fichier de contrôle de code source, consultez [MSSCCPRJ. Fichier de contrôle de code source](../extensibility/mssccprj-scc-file.md)\). Plug\-ins de contrôle de code source peut déclarer si elles ont la possibilité de créer MSSCCPRJ. Fichiers SCC en déclarant `SCC_CAP_SCCFILE` pendant l'initialisation. Le plug\-in retourne `TRUE` ou `FALSE` par fichier dans le `pbSccFiles` tableau pour indiquer quels fichiers donnés ayant MSSCCPRJ. Prise en charge du contrôle de code source. Si le plug\-in retourne un code de réussite de la fonction, les valeurs dans le tableau de résultats sont respectées. En cas d'échec, le tableau est ignoré.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ. Fichier de contrôle de code source](../extensibility/mssccprj-scc-file.md)