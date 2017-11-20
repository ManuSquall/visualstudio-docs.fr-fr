---
title: "Utilisé dans des chaînes de substitution. Pkgdef et. Les fichiers Pkgundef | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6144c0200c03776ead9e7dc7f46b5e9e707b6e82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Utilisé dans des chaînes de substitution. Pkgdef et. Fichiers Pkgundef
Vous pouvez utiliser les chaînes de substitution répertoriés ci-dessous dans le .pkgdef et application shell isolée de fichiers .pkgundef vous définissez pour vos Visual Studio.  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
  
|Chaîne|Description|  
|------------|-----------------|  
|$=*RegistryEntry*$|La valeur de la *RegistryEntry* entrée. Si la chaîne d’entrée de Registre se termine par une barre oblique inverse (\\), la valeur par défaut de la sous-clé de Registre est utilisée. Par exemple, la substitution de chaîne $= HKEY_CURRENT_USER\Environment\TEMP$ est développé dans le dossier temporaire de l’utilisateur actuel.|  
|$AppName$|Le nom qualifié de l’application qui est passée pour les points d’entrée AppEnv.dll. Le nom qualifié se compose de l’identificateur de classe (CLSID) de l’objet application automation, qui est également enregistré comme la valeur du paramètre ThisVersionDTECLSID dans le fichier .pkgdef de projet, un trait de soulignement et le nom de l’application.|  
|$AppDataLocalFolder|Le sous-dossier sous % LocalAppData% pour cette application.|  
|$BaseInstallDir$|Le chemin d’accès complet de l’emplacement où Visual Studio a été installé.|  
|$CommonFiles$|La valeur de la variable d’environnement % %CommonProgramFiles.|  
|$MyDocuments$|Le chemin d’accès complet du dossier Mes Documents de l’utilisateur actuel.|  
|$PackageFolder$|Le chemin d’accès complet du répertoire qui contient les fichiers d’assembly de package d’application.|  
|$ProgramFiles$|La valeur de la variable d’environnement % ProgramFiles%.|  
|$RootFolder$|Le chemin d’accès complet du répertoire racine de l’application.|  
|$RootKey$|La clé de Registre racine pour l’application. Par défaut la racine est HKEY_CURRENT_USER\Software\\*CompanyName*\\*nom_projet*\\*VersionNumber* (lorsque l’application est en cours d’exécution, _Config est ajoutée à cette clé). Il est défini par la valeur RegistryRoot dans le *SolutionName*fichier .pkgdef.<br /><br /> La chaîne de $ $RootKey peut être utilisée pour récupérer une valeur de Registre sous la sous-clé de l’application. Par exemple, la chaîne « $= $RootKey$ \AppIcon$ » retourne la valeur de l’entrée AppIcon sous la sous-clé de racine d’application.<br /><br /> L’analyseur traite le fichier .pkgdef de manière séquentielle et peut accéder à une entrée de Registre sous la sous-clé de l’application uniquement si l’entrée a été précédemment définie.|  
|$ShellFolder$|Le chemin d’accès complet de l’emplacement où Visual Studio a été installé.|  
|$System$|Le dossier Windows\system32.|  
|$WINDIR$|Le dossier Windows.|  
  
 Si l’analyseur ne reconnaît pas la chaîne de substitution, ou il ne peut pas déterminer la valeur d’une entrée de Registre ou une variable d’environnement, puis il n’effectue pas de substitution sur cette partie de la chaîne.