---
title: Chaînes de substitution utilisés dans. Pkgdef et. Les fichiers Pkgundef | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1496931b02c5673c1f08253ebed7da0cae0b904c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817540"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Chaînes de substitution utilisés dans. Pkgdef et. Fichiers Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser les chaînes de substitution répertoriés ci-dessous dans le .pkgdef et .pkgundef les fichiers que vous définissez pour Visual Studio application shell isolée de.  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
  
|Chaîne|Description|  
|------------|-----------------|  
|$=*RegistryEntry*$|La valeur de la *RegistryEntry* entrée. Si la chaîne d’entrée de Registre se termine par une barre oblique inverse (\\), la valeur par défaut de la sous-clé de Registre est utilisée. Par exemple, la substitution de chaîne $= HKEY_CURRENT_USER\Environment\TEMP$ est développé dans le dossier temporaire de l’utilisateur actuel.|  
|$AppName$|Le nom qualifié de l’application qui est passé pour les points d’entrée AppEnv.dll. Le nom qualifié comprend le nom de l’application, un trait de soulignement et l’identificateur de classe (CLSID) de l’objet application automation, qui est également enregistré en tant que la valeur du paramètre ThisVersionDTECLSID dans le fichier .pkgdef de projet.|  
|$AppDataLocalFolder|Le sous-dossier sous %LocalAppData% pour cette application.|  
|$BaseInstallDir$|Le chemin d’accès complet de l’emplacement où Visual Studio a été installé.|  
|$CommonFiles$|La valeur de la variable d’environnement % %CommonProgramFiles%.|  
|$MyDocuments$|Le chemin d’accès complet du dossier Mes Documents de l’utilisateur actuel.|  
|$PackageFolder$|Le chemin d’accès complet du répertoire qui contient les fichiers d’assembly de package pour l’application.|  
|$ProgramFiles$|La valeur de la variable d’environnement % ProgramFiles %.|  
|$RootFolder$|Le chemin d’accès complet du répertoire racine de l’application.|  
|$RootKey$|La clé de Registre racine pour l’application. Par défaut la racine est HKEY_CURRENT_USER\Software\\*CompanyName*\\*nom_projet*\\*VersionNumber* (lorsque l’application est en cours d’exécution, _Config est ajoutée à cette clé). Il est défini par la valeur RegistryRoot dans le *SolutionName*fichier .pkgdef.<br /><br /> La chaîne de $ $RootKey peut être utilisée pour récupérer une valeur de Registre sous la sous-clé de l’application. Par exemple, la chaîne « $= $RootKey$ $\AppIcon » retourne la valeur de l’entrée AppIcon sous la sous-clé de racine d’application.<br /><br /> L’analyseur traite le fichier .pkgdef séquentiellement et peut accéder à une entrée de Registre sous la sous-clé de l’application uniquement si l’entrée a été précédemment définie.|  
|$ShellFolder$|Le chemin d’accès complet de l’emplacement où Visual Studio a été installé.|  
|$System$|Le dossier Windows\system32.|  
|$WINDIR$|Le dossier Windows.|  
  
 Si l’analyseur ne reconnaît pas la chaîne de substitution, ou il ne peut pas déterminer la valeur d’une entrée de Registre ou une variable d’environnement, il n’effectue pas substitution sur cette partie de la chaîne.

