---
title: "Chaînes de substitution utilisées dans. Pkgdef et. Les fichiers Pkgundef | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Chaînes de substitution utilisées dans. Pkgdef et. Fichiers Pkgundef
Vous pouvez utiliser les chaînes de substitution répertoriés ci-dessous dans le .pkgdef et fichiers .pkgundef vous définissez pour Visual Studio isolé application d’environnement.  
  
## <a name="substitution-strings"></a>Chaînes de substitution  
  
|Chaîne|Description|  
|------------|-----------------|  
|$=*RegistryEntry*$|La valeur de la *RegistryEntry* entrée. Si la chaîne d’entrée de Registre se termine par une barre oblique inverse (\\), la valeur par défaut de la sous-clé de Registre est utilisée. Par exemple, la substitution de chaîne $= HKEY_CURRENT_USER\Environment\TEMP$ est développé dans le dossier temporaire de l’utilisateur actuel.|  
|$AppName$|Le nom qualifié de l’application qui est passé pour les points d’entrée AppEnv.dll. Le nom qualifié se compose de l’identificateur de classe (CLSID) de l’objet application automation, qui est également enregistré comme la valeur du paramètre ThisVersionDTECLSID dans le fichier .pkgdef de projet, un trait de soulignement et le nom de l’application.|  
|$AppDataLocalFolder|Le sous-dossier sous % LocalAppData% pour cette application.|  
|$BaseInstallDir$|Le chemin d’accès complet de l’emplacement d’installation de Visual Studio.|  
|$CommonFiles$|La valeur de la variable d’environnement % %CommonProgramFiles.|  
|$MyDocuments$|Le chemin d’accès complet du dossier Mes Documents de l’utilisateur actuel.|  
|$PackageFolder$|Le chemin d’accès complet du répertoire qui contient les fichiers d’assembly de package d’application.|  
|$ProgramFiles$|La valeur de la variable d’environnement % ProgramFiles%.|  
|$RootFolder$|Le chemin d’accès complet du répertoire racine de l’application.|  
|$RootKey$|La clé de Registre racine pour l’application. Par défaut la racine est HKEY_CURRENT_USER\Software\\*CompanyName*\\*nom_projet*\\*VersionNumber* (lorsque l’application s’exécute, _Config est ajoutée à cette clé). Il est défini par la valeur RegistryRoot dans le *SolutionName*fichier .pkgdef.<br /><br /> La chaîne de $ $RootKey peut être utilisée pour récupérer une valeur de Registre sous la sous-clé de l’application. Par exemple, la chaîne « $= $RootKey$ $\AppIcon » renvoie la valeur de l’entrée AppIcon sous la sous-clé de racine d’application.<br /><br /> L’analyseur traite le fichier .pkgdef individuellement et peut accéder à une entrée de Registre sous la sous-clé de l’application uniquement si l’entrée a été précédemment définie.|  
|$ShellFolder$|Le chemin d’accès complet de l’emplacement d’installation de Visual Studio.|  
|$System$|Le dossier Windows\system32.|  
|$WINDIR$|Le dossier Windows.|  
  
 Si l’analyseur ne reconnaît pas la chaîne de substitution, ou il ne peut pas déterminer la valeur d’une entrée de Registre ou une variable d’environnement, puis il n’effectue pas de substitution sur cette partie de la chaîne.
